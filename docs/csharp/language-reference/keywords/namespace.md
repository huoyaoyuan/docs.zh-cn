---
title: namespace 关键字 - C# 参考
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: df921ecc670bf12411dc8b0d828d6c19bb0a1aec
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422741"
---
# <a name="namespace-c-reference"></a>命名空间（C# 参考）

`namespace` 关键字用于声明包含一组相关对象的作用域。 可以使用命名空间来组织代码元素并创建全局唯一类型。

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>备注

在命名空间中，可以声明零个或多个以下类型：

- 另一个命名空间

- [class](class.md)

- [接口](interface.md)

- [struct](struct.md)

- [enum](enum.md)

- [delegate](delegate.md)

无论是否在 C# 源文件中显式声明命名空间，编译器都会添加一个默认命名空间。 此未命名的命名空间（有时被称为全局命名空间）存在于每个文件中。 全局命名空间中的任何标识符都可用于已命名的命名空间。

命名空间隐式具有公共访问权限，这是不可修改的。 有关可以分配给命名空间中元素的访问修饰符的讨论，请参阅[访问修饰符](access-modifiers.md)。

可以在两个或多个声明中定义一个命名空间。 例如，以下示例将两个类定义为 `MyCompany` 命名空间的一部分：

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>示例

以下示例显示如何在嵌套命名空间中调用静态方法。

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a>相关资源

有关使用命名空间的详细信息，请参阅以下主题：

- [命名空间](../../programming-guide/namespaces/index.md)

- [使用命名空间](../../programming-guide/namespaces/using-namespaces.md)

- [如何：使用全局命名空间别名](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>C# 语言规范

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>请参阅

- [C# 参考](../../language-reference/index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [C# 关键字](index.md)
- [using](using-directive.md)
- [using static](using-static.md)
