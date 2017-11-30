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
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="03221-104">Azure Key Vault を使用して、実稼働時に機密データを保護するには</span><span class="sxs-lookup"><span data-stu-id="03221-104">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="03221-105">環境変数として保存またはシークレット マネージャー ツールによって保存された機密情報がまだローカルに保存され、コンピューターに暗号化されていません。</span><span class="sxs-lookup"><span data-stu-id="03221-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="03221-106">機密情報を格納するためのより安全なオプションは[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)キーとシークレットを格納するためのセキュリティで保護された、中央の場所を提供します。</span><span class="sxs-lookup"><span data-stu-id="03221-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="03221-107">Microsoft.Extensions.Configuration.AzureKeyVault パッケージには、Azure Key Vault から構成情報を読み取る ASP.NET Core アプリケーションができます。</span><span class="sxs-lookup"><span data-stu-id="03221-107">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="03221-108">Azure Key Vault からシークレットを使用するを起動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="03221-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="03221-109">最初に、Azure AD アプリケーションとして、アプリケーションを登録します。</span><span class="sxs-lookup"><span data-stu-id="03221-109">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="03221-110">(キー コンテナーへのアクセスは、Azure AD によって管理されます)。これにより、Azure 管理ポータルででしょう。</span><span class="sxs-lookup"><span data-stu-id="03221-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="03221-111">代わりに、パスワードまたはクライアント シークレットではなく、証明書を使用して認証をアプリにする場合を使えば、[新規 AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell コマンドレット。</span><span class="sxs-lookup"><span data-stu-id="03221-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="03221-112">証明書を Azure Key Vault に登録するには、公開キーのみが必要があります。</span><span class="sxs-lookup"><span data-stu-id="03221-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="03221-113">(アプリケーションは、秘密キーを使用します)</span><span class="sxs-lookup"><span data-stu-id="03221-113">(Your application will use the private key.)</span></span>

<span data-ttu-id="03221-114">新しいサービス プリンシパルを作成することで、キーの資格情報コンテナーに登録済みのアプリケーション アクセス権を付与第二に、します。</span><span class="sxs-lookup"><span data-stu-id="03221-114">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="03221-115">これを行う次の PowerShell コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="03221-115">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="03221-116">IConfigurationRoot インスタンスを作成するときに、IConfigurationBuilder.AddAzureKeyVault 拡張メソッドを呼び出すことによって、アプリケーションの構成ソースとしては、key vault には第三が含まれます。</span><span class="sxs-lookup"><span data-stu-id="03221-116">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="03221-117">AddAzureKeyVault を呼び出すことを必要とするアプリケーション ID が登録され、前の手順で、key vault へのアクセス許可を注意してください。</span><span class="sxs-lookup"><span data-stu-id="03221-117">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="03221-118">現時点では、.NET 標準と .NET Core をサポートして、Azure Key Vault から構成情報を取得するクライアント ID およびクライアント シークレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="03221-118">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="03221-119">.NET framework アプリケーションでは、クライアント シークレットの代わりに、証明書を受け取る IConfigurationBuilder.AddAzureKeyVault のオーバー ロードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="03221-119">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="03221-120">このドキュメントの作成時点では、[進行中の](https://github.com/aspnet/Configuration/issues/605).NET 標準と .NET Core でそのオーバー ロードを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="03221-120">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="03221-121">AddAzureKeyVault オーバー ロードを受け付ける、証明書が使用可能なまで ASP.NET Core アプリケーションは、次の例に示すように、KeyVaultClient オブジェクトを明示的に作成して証明書ベースの認証の Azure Key Vault をアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="03221-121">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

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

<span data-ttu-id="03221-122">この例では、AddAzureKeyVault への呼び出しは、構成プロバイダーの登録の末尾には提供されます。</span><span class="sxs-lookup"><span data-stu-id="03221-122">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="03221-123">以前のプロバイダーからの構成値を上書きする機会があるほか、ように他のソースから構成値をオーバーライドなし key vault から最後の構成プロバイダーとして Azure Key Vault を登録することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="03221-123">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="03221-124">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="03221-124">Additional resources</span></span>

-   <span data-ttu-id="03221-125">**Azure Key Vault を使用して、アプリケーションの機密データを保護する**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="03221-125">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="03221-126">**アプリ シークレットは、開発中の安全な保管**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="03221-126">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="03221-127">**データ保護を構成する**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="03221-127">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="03221-128">**キーの管理と有効期間**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#データ保護の既定設定*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="03221-128">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="03221-129">**Microsoft.Extensions.Configuration.DockerSecrets です。**</span><span class="sxs-lookup"><span data-stu-id="03221-129">**Microsoft.Extensions.Configuration.DockerSecrets.**</span></span> <span data-ttu-id="03221-130">GitHub のリポジトリ。</span><span class="sxs-lookup"><span data-stu-id="03221-130">GitHub repo.</span></span>
    [<span data-ttu-id="03221-131">*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span><span class="sxs-lookup"><span data-stu-id="03221-131">*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span></span>](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
<span data-ttu-id="03221-132">[前](開発者向けのアプリのシークレット-storage.md) [次へ] (../キー takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="03221-132">[Previous] (developer-app-secrets-storage.md) [Next] (../key-takeaways.md)</span></span>
