---
title: 実稼働時に機密情報を保護するために Azure Key Vault を使用する
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 実稼働時に機密情報を保護するために Azure Key Vault を使用する'
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 5ad5686909c29eba5916cbcc4b7115a16108a004
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580404"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>実稼働時に機密情報を保護するために Azure Key Vault を使用する

環境変数として保存されているシークレットまたは Secret Manager ツールによって保存されたシークレットは、マシンのローカルに暗号化されていない状態で保存されています。 シークレットを保存する上でより安全な選択肢として [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) があります。Azure Key Vault には、キーとシークレットを保存するためのセキュリティで保護された中央の場所が用意されています。

Microsoft.Extensions.Configuration.AzureKeyVault パッケージを使用すると、ASP.NET Core アプリケーションから Azure Key Vault の構成情報を読み取ることができます。 Azure Key Vault のシークレットを初めて使用する場合は、次の手順を実行します。

まず、アプリケーションを Azure AD アプリケーションとして登録します (キー コンテナーへのアクセスは Azure AD で管理されます)。この操作は、Azure 管理ポータルで実行できます。

アプリケーションでパスワードまたはクライアント シークレットの代わりに証明書を使用して認証する場合は、[New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell コマンドレットを使用できます。 Azure Key Vault に登録する証明書には、公開キーのみが必要です (アプリケーションでは秘密キーが使用されます)。

次に、新しいサービス プリンシパルを作成して、登録されたアプリケーションにキー コンテナーへのアクセス権を付与します。 この処理を実行するには、次の PowerShell コマンドを使用します。

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

次に、IConfigurationRoot インスタンスを作成するときに IConfigurationBuilder.AddAzureKeyVault 拡張メソッドを呼び出して、アプリケーションの構成ソースとしてキー コンテナーを含めます。 AddAzureKeyVault を呼び出すには、前の手順で登録し、キー コンテナーへのアクセス権が付与されたアプリケーション ID が必要です。

  現在、.NET Standard と .NET Core は、クライアント ID とクライアント シークレットを使用して Azure Key Vault から構成情報を取得する処理をサポートしています。 .NET Framework アプリケーションでは、クライアント シークレットの代わりに証明書を取得する IConfigurationBuilder.AddAzureKeyVault のオーバーロードを使用できます。 この記事の執筆時点で、.NET Standard および .NET Core でこのオーバーロードを利用できるようにする作業が[進行中](https://github.com/aspnet/Configuration/issues/605)です。 証明書を受け付ける AddAzureKeyVault オーバーロードを利用できるようになるまでは、次の例に示すように、ASP.NET Core アプリケーションは、明示的に KeyVaultClient オブジェクトを作成することで、証明書ベースの認証を使用して Azure Key Vault にアクセスできます。

```csharp
// Configure Key Vault client
var kvClient = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(async
    (authority, resource, scope) =>
    {
        var cert = // Get certificate from local store/file/key vault etc. as needed
        // From the Microsoft.IdentityModel.Clients.ActiveDirectory pacakge
        var authContext = new AuthenticationContext(authority,
            TokenCache.DefaultShared);
        var result = await authContext.AcquireTokenAsync(resource,
            // From the Microsoft.Rest.ClientRuntime.Azure.Authentication pacakge
            new ClientAssertionCertificate("{Application ID}", cert));
        return result.AccessToken;
    }));

    // Get configuration values from Key Vault
    var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        // Other configuration providers go here.
        .AddAzureKeyVault("{KeyValueUri}", kvClient,
        new DefaultKeyVaultSecretManager());
```

この例では、構成プロバイダーの登録処理の末尾で AddAzureKeyVault が呼び出されます。 前のプロバイダーの構成値を上書きし、他のソースの構成値でキー コンテナーの構成値が上書きされないようにするために、最後の構成プロバイダーとして Azure Key Vault を登録することをお勧めします。

## <a name="additional-resources"></a>その他の技術情報

-   **Azure Key Vault を使用したアプリケーション シークレットの保護**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **開発中のアプリ シークレットの安全な保存**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **データ保護の構成**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **キー管理と有効期間**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets.** GitHub リポジトリ。
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[前へ] (developer-app-secrets-storage.md) [次へ] (../key-takeaways.md)
