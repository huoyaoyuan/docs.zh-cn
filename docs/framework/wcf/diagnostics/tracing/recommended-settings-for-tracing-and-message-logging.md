---
title: 跟踪和消息日志记录的推荐设置
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: fa6dc74a26f6a76591a15c549a892f31a65c521e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779725"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>跟踪和消息日志记录的推荐设置
本主题描述用于不同操作环境的跟踪和消息日志记录的推荐设置。  
  
## <a name="recommended-settings-for-a-production-environment"></a>生产环境中的推荐设置  
 对于生产环境，如果您使用的是 WCF 跟踪源，请将 `switchValue` 设置为“警告”。 如果您使用的是 WCF `System.ServiceModel` 跟踪源，请将 `switchValue` 属性设置为 `Warning`，并将 `propagateActivity` 属性设置为 `true`。 如果您使用的是用户定义的跟踪源，请将 `switchValue` 属性设置为 `Warning, ActivityTracing`。 可以使用手动完成这[配置编辑器工具 (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。 如果你没有预测性能情况，则可以在上述所有情况中，将 `switchValue` 属性设置为 `Information`，这将生成大量的跟踪数据。 下面的示例演示这些推荐的设置。  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>用于部署或调试的推荐设置  
 对于部署或调试环境，请为用户定义的或 `Information` 跟踪源选择 `Verbose` 或 `ActivityTracing`，以及 `System.ServiceModel`。 若要增强调试功能，也应将其他跟踪源 (`System.ServiceModel.MessageLogging`) 添加到配置中以启用消息日志记录。 请注意，`switchValue` 属性对此跟踪源没有任何影响。  
  
 下面的示例通过使用利用了 `XmlWriterTraceListener` 的共享侦听器来演示推荐的设置。  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"   
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a>使用 WMI 修改设置  
 可以使用 WMI 更改运行时的配置设置（通过按照上述配置示例，启用配置中的 `wmiProviderEnabled` 属性）。 例如，可以在运行时使用 CIM Studio 中的 WMI 将跟踪源级别从“警告”更改为“信息”。 应该注意，这种方式的即时调试的性能开销可能非常高。 有关使用 WMI 的详细信息，请参阅[使用 Windows Management Instrumentation 进行诊断](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)主题。  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>在 ASP.NET 跟踪中启用相关事件  
 除非启用了 ASP.NET 事件跟踪，否则 ASP.NET 事件不会设置关联 ID (ActivityID)。 若要正确查看相关的事件，必须启用 ASP.NET 事件跟踪命令控制台中使用以下命令，这可以通过转到**启动**，**运行**并键入**cmd**,  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 若要关闭 ASP.NET 事件跟踪，请使用以下命令：  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>请参阅

- [使用 Windows Management Instrumentation 进行诊断](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
