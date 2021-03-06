---
title: 使用绑定配置服务和客户端
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 0f01fefc46cbc2cddaef9b025d59db8e2f734d9f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645130"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>使用绑定配置服务和客户端
绑定是指定连接到终结点所需的通信详细信息的对象。 更具体地说，绑定包含用于创建客户端或服务运行时的配置信息，创建方法是定义用于各个终结点或客户端通道的传输、连网格式（消息编码）和协议的具体内容。 若要创建的正常运行的 Windows Communication Foundation (WCF) 服务，在服务中的每个终结点需要的绑定。 本主题解释什么是绑定、如何定义绑定以及如何为终结点指定特定的绑定。  
  
## <a name="what-a-binding-defines"></a>绑定所定义的内容  
 绑定中的信息可能非常基本，也可能非常复杂。 最基本的绑定仅指定连接终结点所必需的传输协议（如 HTTP）。 一般来说，绑定包含的有关如何连接到终结点的信息属于下表中的某一类别。  
  
 协议  
 确定要使用的安全机制（可靠消息传递功能或事务上下文流设置）。  
  
 传输  
 确定要使用的基础传输协议（例如，TCP 或 HTTP）。  
  
 编码  
 确定消息编码（例如，文本/XML、二进制或消息传输优化机制），该编码确定消息如何在网络上表示为字节流。  
  
## <a name="system-provided-bindings"></a>系统提供的绑定  
 WCF 包含一组旨在满足大多数应用程序的要求和方案的系统提供绑定。 下面的类表示系统提供的绑定的一些示例：  
  
- <xref:System.ServiceModel.BasicHttpBinding>：符合 WS 的 HTTP 协议绑定，适用于连接到 Web 服务的基本配置文件 1.1 规范 (例如，ASP.NET Web 服务 [ASMX]-基于服务)。  
  
- <xref:System.ServiceModel.WSHttpBinding>：HTTP 协议绑定，适用于连接到终结点符合 Web 服务规范协议。  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>：使用.NET 二进制编码和组帧技术一起使用命名管道传输 Windows 连接到同一台计算机上其他 WCF 终结点。  
  
- <xref:System.ServiceModel.NetMsmqBinding>：使用.NET 二进制编码和组帧技术与消息队列 (也称为 MSMQ) 一起使用来创建与其他 WCF 终结点的排队的消息连接。  
  
 有关说明，使用系统提供的绑定的完整列表，请参阅[System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)。  
  
## <a name="custom-bindings"></a>自定义绑定  
 如果系统提供的绑定集合不具有某一服务应用程序所需的正确功能组合，则可以创建 <xref:System.ServiceModel.Channels.CustomBinding> 绑定。 有关元素的详细信息<xref:System.ServiceModel.Channels.CustomBinding>绑定，请参阅[ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)并[自定义绑定](../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## <a name="using-bindings"></a>使用绑定  
 使用绑定需要执行两个基本步骤：  
  
1. 选择或定义绑定。 最简单的方法就是选择一个系统提供的绑定并使用它的默认设置。 您还可以选择一个系统提供的绑定，然后根据您的要求重新设置它的属性值。 或者，你可以创建一个自定义绑定并根据需要设置每一个属性。  
  
2. 创建使用此绑定的终结点。  
  
## <a name="code-and-configuration"></a>代码和配置  
 你可以通过代码或配置来定义或配置绑定。 例如，这两种方法不受所用绑定的类型的影响，无论你是使用系统提供的绑定还是使用 <xref:System.ServiceModel.Channels.CustomBinding> 绑定。 通常，使用代码可使你在编译时对绑定的定义拥有完全的控制权。 但是，使用配置，允许系统管理员或 WCF 服务或客户端以更改绑定的参数的用户。 这种灵活性通常是可取的因为没有方法来预测的特定计算机需求和网络在其中部署 WCF 应用程序的条件。 从代码分隔绑定（和寻址）信息允许管理员无需重新编译或重新部署应用程序就可以更改绑定详细信息。 请注意，如果在代码中定义绑定，该绑定将覆盖配置文件中所指定的任何基于配置的定义。 有关这些方法的示例，请参见下面的主题：  
  
- [如何：承载 WCF 服务中托管的应用程序](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)提供了在代码中创建绑定的一个示例。  
  
- [教程：创建 Windows Communication Foundation 客户端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)提供了使用配置创建客户端的一个示例。  
  
## <a name="see-also"></a>请参阅

- [终结点创建概述](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [如何：在配置中指定服务绑定](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [如何：在代码中指定服务绑定](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
- [如何：在配置中指定客户端绑定](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
- [如何：在代码中指定客户端绑定](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
