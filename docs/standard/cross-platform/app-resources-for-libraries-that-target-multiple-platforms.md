---
title: 面向多个平台的库的应用程序资源
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e846f45b55ac09d6ce6af4f3223c3bdba1dc83ba
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506009"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>面向多个平台的库的应用程序资源
可以使用.NET Framework[可移植类库](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)项目类型以确保可以从多个平台访问类库中的资源。 该项目类型可以在 Visual Studio 2012 中，面向.NET Framework 类库的可移植子集。 使用可移植类库可确保你的库可以从桌面应用、 Silverlight 应用程序、 Windows Phone 应用进行访问和[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]应用。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 可移植类库项目使非常有限的一个子集中的类型<xref:System.Resources>命名空间可用于您的应用程序，但它允许你使用<xref:System.Resources.ResourceManager>类检索资源。 但是，如果你使用 Visual Studio 创建应用，则应使用 Visual Studio 创建的强类型包装器而不是直接使用 <xref:System.Resources.ResourceManager> 类。

 若要在 Visual Studio 中创建的强类型化的包装器，设置主资源文件**访问修饰符**到 Visual Studio 资源设计器**公共**。 这将创建一个包含强类型 ResourceManager 包装器的 [resourceFileName].designer.cs 或 [resourceFileName].designer.vb 文件。 有关使用强类型的资源包装器的详细信息，请参阅中的"生成强类型资源类"一节[Resgen.exe （资源文件生成器）](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)主题。

## <a name="resource-manager-in-the-portable-class-library"></a>可移植类库中的资源管理器
 在可移植类库项目中，对资源的所有访问都由<xref:System.Resources.ResourceManager>类。 因为中的类型<xref:System.Resources>命名空间，如<xref:System.Resources.ResourceReader>和<xref:System.Resources.ResourceSet>，是从可移植类库项目不可访问，它们不能用于访问资源。

 可移植类库项目包括四个<xref:System.Resources.ResourceManager>下表中列出的成员。 这些构造函数和方法使你能够实例化 <xref:System.Resources.ResourceManager> 对象和检索字符串资源。

|`ResourceManager` 成员|描述|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|创建一个可访问在指定程序集中找到的已命名资源文件的 <xref:System.Resources.ResourceManager> 实例。|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|创建一个与指定类型对应的 <xref:System.Resources.ResourceManager> 实例。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|检索当前区域性的已命名资源。|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|检索属于指定区域性的已命名资源。|

 排除其他<xref:System.Resources.ResourceManager>成员从序列化对象、 非字符串数据和映像的可移植类库方法不能检索从资源文件。 若要从可移植类库中使用的资源，应以字符串形式存储的所有对象数据。 例如，你可以通过将数值转换为字符串来将其存储在资源文件中，并且你可以检索它们，然后使用数字数据类型的 `Parse` 或 `TryParse` 方法将其转换回数字。 你可通过调用 <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> 方法将图像或其他二进制数据转换为字符串表示形式，并通过调用 <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> 方法将其还原到字节数组。

## <a name="the-portable-class-library-and-windows-store-apps"></a>可移植类库和 Windows 应用商店应用
 可移植类库项目将资源存储在.resx 文件中，然后编译为.resources 文件并在编译时嵌入在主程序集或附属程序集。 另一方面，[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]应用需在 .resw 文件中存储资源，这些文件随后将被编译为单个包资源索引 (PRI) 文件。 但是，尽管不兼容的文件格式，可移植类库将工作[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]应用。

 若要从 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]应用使用你的类库，请在 Windows 应用商店应用项目中添加对类库的引用。 Visual Studio 以透明方式将资源提取到.resw 文件程序集，并使用它来生成 Windows 运行时可以从其提取资源的 PRI 文件。 在运行时，Windows 运行时执行的代码在可移植类库，但它从 PRI 文件中检索可移植类库的资源。

 如果你的可移植类库项目包含本地化的资源，使用中心辐射模型以将其部署只需根据需要对桌面应用程序中的库。 若要在 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]应用中使用主资源文件和所有本地化的资源文件，可添加对主程序集的引用。 在编译时，Visual Studio 会将你的主资源文件以及所有本地化资源文件中的资源提取到单独的 .resw 文件中。 然后将.resw 文件编译为单个 PRI 文件中的 Windows 运行时在运行时访问。

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>示例:非本地化可移植类库
 下面的简单、 非本地化可移植类库示例使用的资源来存储列的名称并确定要为表格数据保留的字符数。 此示例使用名为 LibResources.resx 的文件存储下表中列出的字符串资源。

|资源名称|资源值|
|-------------------|--------------------|
|Born|Birthdate|
|BornLength|12|
|Hired|雇佣日期|
|HiredLength|12|
|Id|Id|
|ID.Length|12|
|名称|名称|
|NameLength|25|
|标题|Employee Database|

 下面的代码定义`UILibrary`类，该类使用名为资源管理器包装`resources`由 Visual Studio 生成时**访问修饰符**文件更改为**公共**. UILibrary 类根据需要分析字符串数据。 . 请注意，该类位于 `MyCompany.Employees` 命名空间中。

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 以下代码阐释如何从控制台模式应用访问 `UILibrary` 类及其资源。 它需要对 UILibrary.dll 要添加到控制台应用程序项目的引用。

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 下列代码阐释了如何从 `UILibrary`应用访问 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 类及其资源。 它需要对 UILibrary.dll 要添加到 Windows 应用商店应用项目的引用。

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>示例:本地化的可移植类库
 下面的本地化可移植类库示例包括法语 （法国） 和英语 （美国） 区域性的资源。 英语 （美国） 区域性是应用程序的默认区域性;在表中显示其资源[上一节](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc)。 法语（法国）区域性的资源文件命名为 LibResources.fr-FR.resx，该文件包含下表中列出的字符串资源。 `UILibrary` 类的源代码与上一部分中所示的相同。

|资源名称|资源值|
|-------------------|--------------------|
|Born|Date de naissance|
|BornLength|20|
|Hired|日期 embauché|
|HiredLength|16|
|Id|Id|
|名称|Nom|
|标题|基 de données des employés|

 以下代码阐释如何从控制台模式应用访问 `UILibrary` 类及其资源。 它需要对 UILibrary.dll 要添加到控制台应用程序项目的引用。

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 下列代码阐释了如何从 `UILibrary`应用访问 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 类及其资源。 它需要对 UILibrary.dll 要添加到 Windows 应用商店应用项目的引用。 它使用静态 `ApplicationLanguages.PrimaryLanguageOverride` 属性将应用的首选语言设置为法语。

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Resources.ResourceManager>
- [桌面应用中的资源](../../../docs/framework/resources/index.md)
- [打包和部署资源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
