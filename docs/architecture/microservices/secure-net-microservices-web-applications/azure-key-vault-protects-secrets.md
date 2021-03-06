---
title: 在生产时使用 Azure Key Vault 保护机密
description: .NET 微服务和 Web 应用程序中的安全性 - Azure Key Vault 是处理完全由管理员控制的应用程序机密的绝佳方式。 管理员甚至可以在不需要开发人员处理的情况下分配和撤销开发值。
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 63bf357c95b82a820b6dfb6a2d24a5d89f66de72
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675664"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>在生产时使用 Azure Key Vault 保护机密

存储为环境变量的机密或由机密管理器工具存储的机密仍在本地存储并在计算机上解密。 用于存储机密更加安全的选项是使用 [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)，它为存储密钥和机密提供安全的中央位置。

Microsoft.Extensions.Configuration.AzureKeyVault  包允许 ASP.NET Core 应用程序从 Azure Key Vault 中读取配置信息。 若要开始通过 Azure Key Vault 使用机密，请按照下列步骤操作：

1. 将应用程序注册为 Azure AD 应用程序。 （对密钥保管库的访问由 Azure AD 管理。）可以通过 Azure 管理门户完成此操作。\

   或者，如果希望应用程序使用证书而不是密码或客户端密码进行身份验证，可以使用 [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet。 向 Azure Key Vault 注册的证书仅需要公钥。 应用程序将使用私钥。

2. 通过创建新的服务主体授予已注册应用程序访问密钥保管库的权限。 可以使用以下 PowerShell 命令来执行此操作：

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. 创建 <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> 实例时通过调用 <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> 扩展方法将密钥保管库作为配置源包括在应用程序中。 请注意，调用 `AddAzureKeyVault` 将需要前面步骤中已注册并已获取密钥保管库访问权限的应用程序 ID。

   还可以使用 `AddAzureKeyVault` 重载，该重载通过包含对 [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) 包的引用来用证书代替客户端机密。

> [!IMPORTANT]
> 建议将 Azure Key Vault 注册为最后一个配置提供程序，这样它就可以覆盖之前提供程序的配置值。

## <a name="additional-resources"></a>其他资源

- **使用 Azure Key Vault 保护应用程序机密** \
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- **在开发期间安全存储应用机密** \
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- **配置数据保护** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- **ASP.NET Core 中的数据保护密钥管理和生存期信息** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- Microsoft.Extensions.Configuration.KeyPerFile  GitHub 存储库。 \
  <https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile>

>[!div class="step-by-step"]
>[上一页](developer-app-secrets-storage.md)
>[下一页](../key-takeaways.md)
