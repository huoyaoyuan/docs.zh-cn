---
title: Char 数据类型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 8313c2282a3b4b7b035f9f3b685a786c4471f53a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630152"
---
# <a name="char-data-type-visual-basic"></a>Char 数据类型 (Visual Basic)

保存16位 (2 字节) 无符号码位, 范围介于0到65535之间。 每个*码位*或字符代码都表示一个 Unicode 字符。

## <a name="remarks"></a>备注

当需要仅保存单个字符且无需`String`开销时, 请使用数据类型。`Char` 在某些情况下, 可以`Char()`使用 ( `Char`元素数组) 保存多个字符。

的`Char`默认值为码位为0的字符。

## <a name="unicode-characters"></a>Unicode 字符

Unicode 的第一个128码位 (0 – 127) 对应于标准美式键盘上的字母和符号。 这前128码位与 ASCII 字符集定义的代码点相同。 第二个128码位 (128 – 255) 表示特殊字符, 例如基于拉丁语的字母表号、重音、货币符号和分数。 Unicode 对各种符号 (包括全球文本字符、音调符号和数学符号和技术符号) 使用剩余的代码点 (256-65535)。

您可以对<xref:System.Char.IsDigit%2A> `Char`变量使用和<xref:System.Char.IsPunctuation%2A>等方法来确定其 Unicode 分类。

## <a name="type-conversions"></a>类型转换

Visual Basic 不会直接在和`Char`数值类型之间转换。 您可以使用<xref:Microsoft.VisualBasic.Strings.Asc%2A>或<xref:Microsoft.VisualBasic.Strings.AscW%2A> `Char` 函数`Integer`将值转换为表示其码位的。 您可以使用<xref:Microsoft.VisualBasic.Strings.Chr%2A>或<xref:Microsoft.VisualBasic.Strings.ChrW%2A> `Integer` 函数`Char`将值转换为具有该码位的。

如果类型检查开关 ( [Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)) 为 on, 则必须将文本类型字符追加到单字符字符串文本中, 以将其标识为`Char`数据类型。 下面的示例阐释了这一点。 对`charVar`变量的第一次赋值将生成编译器错误`Option Strict` [BC30512](../../misc/bc30512.md) , 因为处于打开。 第二个编译成功, `c`因为文本类型字符将文本标识`Char`为值。

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a>编程提示

- **负数。** `Char`是无符号类型, 不能表示负值。 在任何情况下, 不应使用`Char`来保存数值。

- **互操作注意事项。** 如果你使用不是为 .NET Framework 编写的组件 (如自动化或 COM 对象) 进行交互, 请记住, 在其他环境中字符类型具有不同的数据宽度 (8 位)。 如果将一个8位参数传递给此类组件, 请`Byte` `Char`在新的 Visual Basic 代码中将其声明为而不是。

- **扩大.** 数据类型扩大到`String`。 `Char` 这意味着你可以将`Char`转换`String`为<xref:System.OverflowException?displayProperty=nameWithType>, 而不会遇到。

- **键入字符。** 将文本类型字符`C`追加到单字符字符串文本会将其强制转换`Char`为数据类型。 `Char`没有标识符类型字符。

- **Framework 类型。** .NET Framework 中的对应类型是 <xref:System.Char?displayProperty=nameWithType> 结构。

## <a name="see-also"></a>请参阅

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [String 数据类型](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [如何：调用需要使用无符号类型的 Windows 函数](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
