---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: c4069ef760877935c4ce194144d131d0dc58b4d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504367"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
LINQ 到数据集可以更轻松和更快地对数据执行查询缓存在<xref:System.Data.DataSet>对象。 具体而言，LINQ to DataSet 可以简化查询，使开发人员能够编写查询的编程语言本身，而不是通过使用单独的查询语言。 这是非常适合 Visual Studio 开发人员，他们现在可以充分利用编译时语法检查、 静态类型化，并在其查询中的 Visual Studio 提供 IntelliSense 支持。  
  
 此外可以使用 LINQ to DataSet 对已从一个或多个数据源合并的数据执行查询。 这可以使许多需要灵活表示和处理数据的方案（例如查询本地聚合的数据和 Web 应用程序中的中间层缓存）能够实现。 具体地说，一般报告、分析和业务智能应用程序将需要这种操作方法。  
  
 主要通过中的扩展方法公开 LINQ to DataSet 的功能<xref:System.Data.DataRowExtensions>和<xref:System.Data.DataTableExtensions>类。 LINQ 到数据集生成和使用现有的 ADO.NET 体系结构，并不是为了替换应用程序代码中的 ADO.NET。 现有的 ADO.NET 代码将继续在 LINQ to DataSet 应用程序中正常工作。 下图说明了 LINQ to ADO.NET 和数据存储的数据集的关系。  
  
 ![显示 LINQ to DataSet 基于 ADO.NET 提供程序关系图。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>本节内容  
 [入门](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [编程指南](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>参考  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>请参阅

- [语言集成查询 (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [语言集成查询 (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ 和 ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
