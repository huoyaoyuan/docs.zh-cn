---
title: 如何：声明对象变量, 并将对象分配给 Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 71949d50b01d7f252a988e86ca259261086d3b3b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630869"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>如何：声明对象变量, 并将对象分配给 Visual Basic

通过在[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)中指定`As Object`来声明[对象数据类型](../../../../visual-basic/language-reference/data-types/object-data-type.md)的变量。 通过在赋值语句或初始化子句中将对象放置在等号 (`=`) 之后, 可以将对象分配给此类变量。

## <a name="example"></a>示例

下面的示例声明一个`Object`变量, 并将当前的实例分配给它。

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

可以通过将变量初始化为其声明的一部分, 来合并声明和赋值。 下面的示例与前面的示例等效。

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a>编译代码

此示例需要：

- 对 <xref:System> 命名空间的引用。

- 要在其中放置语句的`Dim`类、结构或模块。

- 要在其中放置赋值语句的过程。

## <a name="see-also"></a>请参阅

- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [对象变量声明](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object 数据类型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
