---
title: "Azure Key Vault を使用して、実稼働時に機密データを保護するには"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Azure Key Vault を使用して、実稼働時に機密データを保護するには"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7f922997e8d0c63e206cd68f4efda14985c86b72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>Azure Key Vault を使用して、実稼働時に機密データを保護するには

環境変数として保存またはシークレット マネージャー ツールによって保存された機密情報がまだローカルに保存され、コンピューターに暗号化されていません。 機密情報を格納するためのより安全なオプションは[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)キーとシークレットを格納するためのセキュリティで保護された、中央の場所を提供します。

Microsoft.Extensions.Configuration.AzureKeyVault パッケージには、Azure Key Vault から構成情報を読み取る ASP.NET Core アプリケーションができます。 Azure Key Vault からシークレットを使用するを起動するには、次の手順に従います。

最初に、Azure AD アプリケーションとして、アプリケーションを登録します。 (キー コンテナーへのアクセスは、Azure AD によって管理されます)。これにより、Azure 管理ポータルででしょう。

代わりに、パスワードまたはクライアント シークレットではなく、証明書を使用して認証をアプリにする場合を使えば、[新規 AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell コマンドレット。 証明書を Azure Key Vault に登録するには、公開キーのみが必要があります。 (アプリケーションは、秘密キーを使用します)

新しいサービス プリンシパルを作成することで、キーの資格情報コンテナーに登録済みのアプリケーション アクセス権を付与第二に、します。 これを行う次の PowerShell コマンドを使用します。

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

IConfigurationRoot インスタンスを作成するときに、IConfigurationBuilder.AddAzureKeyVault 拡張メソッドを呼び出すことによって、アプリケーションの構成ソースとしては、key vault には第三が含まれます。 AddAzureKeyVault を呼び出すことを必要とするアプリケーション ID が登録され、前の手順で、key vault へのアクセス許可を注意してください。

  現時点では、.NET 標準と .NET Core をサポートして、Azure Key Vault から構成情報を取得するクライアント ID およびクライアント シークレットを使用します。 .NET framework アプリケーションでは、クライアント シークレットの代わりに、証明書を受け取る IConfigurationBuilder.AddAzureKeyVault のオーバー ロードを使用できます。 このドキュメントの作成時点では、[進行中の](https://github.com/aspnet/Configuration/issues/605).NET 標準と .NET Core でそのオーバー ロードを使用できるようにします。 AddAzureKeyVault オーバー ロードを受け付ける、証明書が使用可能なまで ASP.NET Core アプリケーションは、次の例に示すように、KeyVaultClient オブジェクトを明示的に作成して証明書ベースの認証の Azure Key Vault をアクセスできます。

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

この例では、AddAzureKeyVault への呼び出しは、構成プロバイダーの登録の末尾には提供されます。 以前のプロバイダーからの構成値を上書きする機会があるほか、ように他のソースから構成値をオーバーライドなし key vault から最後の構成プロバイダーとして Azure Key Vault を登録することをお勧めします。

## <a name="additional-resources"></a>その他の技術情報

-   **Azure Key Vault を使用して、アプリケーションの機密データを保護する**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **アプリ シークレットは、開発中の安全な保管**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **データ保護を構成する**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **キーの管理と有効期間**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#データ保護の既定設定*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets です。** GitHub のリポジトリ。
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[前](開発者向けのアプリのシークレット-storage.md) [次へ] (../キー takeaways.md)
