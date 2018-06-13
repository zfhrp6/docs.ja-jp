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
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="ad958-103">実稼働時に機密情報を保護するために Azure Key Vault を使用する</span><span class="sxs-lookup"><span data-stu-id="ad958-103">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="ad958-104">環境変数として保存されているシークレットまたは Secret Manager ツールによって保存されたシークレットは、マシンのローカルに暗号化されていない状態で保存されています。</span><span class="sxs-lookup"><span data-stu-id="ad958-104">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="ad958-105">シークレットを保存する上でより安全な選択肢として [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) があります。Azure Key Vault には、キーとシークレットを保存するためのセキュリティで保護された中央の場所が用意されています。</span><span class="sxs-lookup"><span data-stu-id="ad958-105">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="ad958-106">Microsoft.Extensions.Configuration.AzureKeyVault パッケージを使用すると、ASP.NET Core アプリケーションから Azure Key Vault の構成情報を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="ad958-106">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="ad958-107">Azure Key Vault のシークレットを初めて使用する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ad958-107">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="ad958-108">まず、アプリケーションを Azure AD アプリケーションとして登録します</span><span class="sxs-lookup"><span data-stu-id="ad958-108">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="ad958-109">(キー コンテナーへのアクセスは Azure AD で管理されます)。この操作は、Azure 管理ポータルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad958-109">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="ad958-110">アプリケーションでパスワードまたはクライアント シークレットの代わりに証明書を使用して認証する場合は、[New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell コマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad958-110">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="ad958-111">Azure Key Vault に登録する証明書には、公開キーのみが必要です</span><span class="sxs-lookup"><span data-stu-id="ad958-111">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="ad958-112">(アプリケーションでは秘密キーが使用されます)。</span><span class="sxs-lookup"><span data-stu-id="ad958-112">(Your application will use the private key.)</span></span>

<span data-ttu-id="ad958-113">次に、新しいサービス プリンシパルを作成して、登録されたアプリケーションにキー コンテナーへのアクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="ad958-113">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="ad958-114">この処理を実行するには、次の PowerShell コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad958-114">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="ad958-115">次に、IConfigurationRoot インスタンスを作成するときに IConfigurationBuilder.AddAzureKeyVault 拡張メソッドを呼び出して、アプリケーションの構成ソースとしてキー コンテナーを含めます。</span><span class="sxs-lookup"><span data-stu-id="ad958-115">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="ad958-116">AddAzureKeyVault を呼び出すには、前の手順で登録し、キー コンテナーへのアクセス権が付与されたアプリケーション ID が必要です。</span><span class="sxs-lookup"><span data-stu-id="ad958-116">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="ad958-117">現在、.NET Standard と .NET Core は、クライアント ID とクライアント シークレットを使用して Azure Key Vault から構成情報を取得する処理をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="ad958-117">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="ad958-118">.NET Framework アプリケーションでは、クライアント シークレットの代わりに証明書を取得する IConfigurationBuilder.AddAzureKeyVault のオーバーロードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad958-118">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="ad958-119">この記事の執筆時点で、.NET Standard および .NET Core でこのオーバーロードを利用できるようにする作業が[進行中](https://github.com/aspnet/Configuration/issues/605)です。</span><span class="sxs-lookup"><span data-stu-id="ad958-119">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="ad958-120">証明書を受け付ける AddAzureKeyVault オーバーロードを利用できるようになるまでは、次の例に示すように、ASP.NET Core アプリケーションは、明示的に KeyVaultClient オブジェクトを作成することで、証明書ベースの認証を使用して Azure Key Vault にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ad958-120">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

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

<span data-ttu-id="ad958-121">この例では、構成プロバイダーの登録処理の末尾で AddAzureKeyVault が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ad958-121">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="ad958-122">前のプロバイダーの構成値を上書きし、他のソースの構成値でキー コンテナーの構成値が上書きされないようにするために、最後の構成プロバイダーとして Azure Key Vault を登録することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ad958-122">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ad958-123">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="ad958-123">Additional resources</span></span>

-   <span data-ttu-id="ad958-124">**Azure Key Vault を使用したアプリケーション シークレットの保護**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="ad958-124">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="ad958-125">**開発中のアプリ シークレットの安全な保存**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="ad958-125">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="ad958-126">**データ保護の構成**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="ad958-126">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="ad958-127">**キー管理と有効期間**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="ad958-127">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="ad958-128">**Microsoft.Extensions.Configuration.DockerSecrets.**</span><span class="sxs-lookup"><span data-stu-id="ad958-128">**Microsoft.Extensions.Configuration.DockerSecrets.**</span></span> <span data-ttu-id="ad958-129">GitHub リポジトリ。</span><span class="sxs-lookup"><span data-stu-id="ad958-129">GitHub repo.</span></span>
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
<span data-ttu-id="ad958-130">[前へ] (developer-app-secrets-storage.md) [次へ] (../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="ad958-130">[Previous] (developer-app-secrets-storage.md) [Next] (../key-takeaways.md)</span></span>
