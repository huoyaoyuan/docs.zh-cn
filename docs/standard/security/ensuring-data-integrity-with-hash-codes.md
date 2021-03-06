---
title: 使用哈希代码确保数据完整性
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0383dc3024352b9fac879532ab2789a60488c96
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331635"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>使用哈希代码确保数据完整性
哈希值是用于唯一标识数据的固定长度的数字值。 哈希值以小得多的数字值表示大量数据，因此与数字签名配合使用。 对哈希值进行签名比对较大的值进行签名更为高效。 对于验证通过不安全通道发送的数据的完整性，哈希值也很有用。 当被发送出去确定数据是否已更改时，将接收数据的哈希值与数据的哈希值相比较。  
  
 本主题介绍如何通过使用 <xref:System.Security.Cryptography?displayProperty=nameWithType> 命名空间中的类生成和验证哈希代码。  
  
## <a name="generating-a-hash"></a>生成哈希  
 托管哈希类可以对字节数组或托管流对象进行哈希处理。 以下示例使用 SHA1 哈希算法为字符串创建哈希值。 该示例使用 <xref:System.Text.UnicodeEncoding> 类将字符串转换为通过使用 <xref:System.Security.Cryptography.SHA1Managed> 类进行哈希处理的字节数组。 然后向控制台显示哈希值。  

 由于 SHA1 出现冲突, Microsoft 建议 SHA256 或更好。
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 此代码将向控制台显示以下字符串：  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a>验证哈希  
 可将数据与哈希值进行比较，以确定其完整性。 通常，在某个特定时间对数据进行哈希运算，并以某种方式保护哈希值。 稍后，可以再次对数据进行哈希运算，并与受保护的值进行比较。 如果哈希值匹配，则数据未更改。 如果值不匹配，则数据已损坏。 要使此系统发挥作用，必须对受保护的哈希加密或对所有的不受信任方保密。  
  
 以下示例将字符串旧的哈希值与新的哈希值进行比较。 此示例循环访问哈希值的每个字节并进行比较。  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 如果两个哈希值匹配，则此代码将向控制台现实以下内容：  
  
```  
The hash codes match.  
```  
  
 如果不匹配，则此代码显示以下信息：  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>请参阅

- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
