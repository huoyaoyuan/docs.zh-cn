---
title: 安全性 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: 33af2200c5d672dc63dc7be79833a174bfe31c20
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504254"
---
# <a name="security-linq-to-dataset"></a>安全性 (LINQ to DataSet)
本主题介绍 LINQ to DataSet 中的安全问题。  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>将查询传递到不受信任的组件  
 LINQ to DataSet 查询可以在程序的一个点中表述，而在另一个中执行。 在表述查询的点，查询可引用的任何元素可见，如调用方法所属的类或表示局部变量/自变量的符号的私有成员。 在执行时，查询能有效访问那些查询在表述中引用的成员，即使其中调用代码没有可见性。 执行查询的代码没有任意添加的可见性，因为它不能选择要访问的内容。 它能严格访问查询所访问的内容，并且仅通过查询本身访问。  
  
 这意味着将查询的引用传递到其他代码段即表示信任接收该查询的组件，组件可访问查询引用的所有公共成员和私有成员。 一般情况下，LINQ to DataSet 查询应不能传递到不受信任的组件，除非查询已经过仔细构造，因此它不会公开应保留为私有的信息。  
  
## <a name="external-input"></a>外部输入  
 应用程序常常采用外部输入（来自用户或其他外部代理），并根据该输入执行操作。  对于 LINQ to DataSet，应用程序可能会构造以某种方式，根据外部输入或使用外部查询中输入的查询。 LINQ to DataSet 查询位置接受参数的文本都被接受。 应用程序开发人员应使用参数化查询，而不是将来自外部代理的文本直接注入查询。  
  
 任何直接或间接从用户或外部代理派生的输入都可能包含利用目标语言的语法来执行未授权操作的内容。 这称为 SQL 注入式攻击，是以目标语言为 Transact-SQL 的攻击模式命名的。 恶意用户利用这种直接注入到查询的用户输入删除数据库表、产生拒绝服务或者更改所执行操作的性质。 虽然可以在 LINQ to DataSet 查询撰写，但通过对象模型 API 执行。 LINQ to DataSet 查询不使用字符串操作或串联，因为它们是在 TRANSACT-SQL 中，不易受到传统意义上的 SQL 注入式攻击来撰写。  
  
## <a name="see-also"></a>请参阅

- [编程指南](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
