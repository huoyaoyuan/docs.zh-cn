---
title: 继承 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 8f49118ebff8dcdfee45ce30de9b35437141e2bb
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398474"
---
# <a name="inheritance-c-programming-guide"></a>继承（C# 编程指南）

继承（以及封装和多形性）是面向对象的编程的三个主要特征之一。 通过继承，可以创建重用、扩展和修改在其他类中定义的行为的新类。 其成员被继承的类称为“基类”  ，继承这些成员的类称为“派生类”  。 派生类只能有一个直接基类。 但是，继承是可传递的。 如果 ClassC 派生自 ClassB，并且 ClassB 派生自 ClassA，则 ClassC 会继承在 ClassB 和 ClassA 中声明的成员。  
  
> [!NOTE]
>  结构不支持继承，但它们可以实现接口。 有关详细信息，请参阅[接口](../../../csharp/programming-guide/interfaces/index.md)。  
  
 从概念上讲，派生类是基类的专门化。 例如，如果有一个基类 `Animal`，则可以有一个名为 `Mammal` 的派生类，以及另一个名为 `Reptile` 的派生类。 `Mammal` 是 `Animal`，`Reptile` 也是 `Animal`，但每个派生类表示基类的不同专门化。  
  
 定义要从其他类派生的类时，派生类会隐式获得基类的所有成员（除了其构造函数和终结器）。 派生类因而可以重用基类中的代码，而无需重新实现。 在派生类中，可以添加更多成员。 通过这种方法，派生类可扩展基类的功能。  
  
 下图显示一个类 `WorkItem`，它表示某个业务流程中的工作项。 像所有类一样，它派生自 <xref:System.Object?displayProperty=nameWithType> 且继承其所有方法。 `WorkItem` 添加了自己的五个成员。 其中包括一个构造函数，因为无法继承构造函数。 类 `ChangeRequest` 继承自 `WorkItem`，表示特定类型的工作项。 `ChangeRequest` 将另外两个成员添加到它从 `WorkItem` 和 <xref:System.Object> 继承的成员中。 它必须添加自己的构造函数，并且还添加了 `originalItemID`。 属性 `originalItemID` 使 `ChangeRequest` 实例可以与向其应用更改请求的原始 `WorkItem` 相关联。  
  
 ![展示类继承的图](./media/inheritance/class-inheritance-diagram.png)  
  
 下面的示例演示如何在 C# 中表示前面图中所示的类关系。 该示例还演示了 `WorkItem` 替代虚方法 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 的方式，以及 `ChangeRequest` 类继承该方法的 `WorkItem` 的实现方式。  
  
 [!code-csharp[csProgGuideInheritance#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#49)]  
  
## <a name="abstract-and-virtual-methods"></a>抽象方法和虚方法  
 基类将方法声明为[虚拟](../../../csharp/language-reference/keywords/virtual.md) 时，派生类可以使用其自己的实现[重写](../../../csharp/language-reference/keywords/override.md)该方法。 如果基类将成员声明为[抽象](../../../csharp/language-reference/keywords/abstract.md)，则必须在直接继承自该类的任何非抽象类中重写该方法。 如果派生类本身是抽象的，则它会继承抽象成员而不会实现它们。 抽象和虚拟成员是多形性（面向对象的编程的第二个主要特征）的基础。 有关详细信息，请参阅[多态性](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)。  
  
## <a name="abstract-base-classes"></a>抽象基类  
 如果要通过使用 [new](../../../csharp/language-reference/operators/new-operator.md) 运算符来防止直接实例化，则可以将类声明为[抽象](../../../csharp/language-reference/keywords/abstract.md)。 如果这样做，则仅当从该类派生新类时，才能使用该类。 抽象类可以包含一个或多个本身声明为抽象的方法签名。 这些签名指定参数和返回值，但没有任何实现（方法体）。 抽象类不必包含抽象成员；但是，如果类包含抽象成员，则类本身必须声明为抽象。 本身不抽象的派生类必须为来自抽象基类的任何抽象方法提供实现。 有关详细信息，请参阅[抽象类、密封类和类成员](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
## <a name="interfaces"></a>接口  
 接口  是引用类型，有些类似于仅包含抽象成员的抽象基类。 类实现接口时，它必须为接口的所有成员提供实现。 类可以实现多个接口，即使它只能派生自单个直接基类。  
  
 接口用于为类定义特定功能，这些功能不一定具有“是”关系。 例如，<xref:System.IEquatable%601?displayProperty=nameWithType> 接口可由任何类或结构实现，这些类或构造必须启用客户端代码来确定该类型的两个对象是否等效（但是由该类型定义等效性）。 <xref:System.IEquatable%601> 不表示基类和派生类之间存在的同一种“是”关系（例如，`Mammal` 是 `Animal`）。 有关详细信息，请参阅[接口](../../../csharp/programming-guide/interfaces/index.md)。  
  
## <a name="preventing-further-derivation"></a>防止进一步派生  
 类可以通过将自己或成员声明为[密封](../../../csharp/language-reference/keywords/sealed.md)，来防止其他类继承自它或继承自其任何成员。 有关详细信息，请参阅[抽象类、密封类和类成员](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
## <a name="derived-class-hiding-of-base-class-members"></a>基类成员的派生类隐藏  
 派生类可以通过使用相同名称和签名声明成员来隐藏基类成员。 [new](../../../csharp/language-reference/keywords/new-modifier.md) 修饰符可以用于显式指示成员不应作为基类成员的重写。 使用 [new](../../../csharp/language-reference/keywords/new-modifier.md) 不是必需的，但如果未使用 [new](../../../csharp/language-reference/keywords/new-modifier.md)，则会生成编译器警告。 有关详细信息，请参阅[使用 Override 和 New 关键字进行版本控制](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)和[了解何时使用 Override 和 New 关键字](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../../../csharp/programming-guide/index.md)
- [类和结构](../../../csharp/programming-guide/classes-and-structs/index.md)
- [class](../../../csharp/language-reference/keywords/class.md)
- [struct](../../../csharp/language-reference/keywords/struct.md)
