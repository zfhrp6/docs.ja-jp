---
title: "開発時にアプリケーションの機密情報を安全に格納する"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 開発時にアプリケーションの機密情報を安全に格納する"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f70f7c741da9653745e4f542125986c701b5d22d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="2dc81-104">開発時にアプリケーションの機密情報を安全に格納する</span><span class="sxs-lookup"><span data-stu-id="2dc81-104">Storing application secrets safely during development</span></span>

<span data-ttu-id="2dc81-105">保護されたリソースおよびその他のサービスに接続する場合、ASP.NET Core アプリケーションは、通常、接続文字列やパスワードなど、機密情報を含む資格情報を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dc81-105">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="2dc81-106">このような機密情報は、"*シークレット*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2dc81-106">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="2dc81-107">ソース コードに機密情報を含めないこと、さらに決してソース管理に機密情報を格納しないことがベスト プラクティスです。</span><span class="sxs-lookup"><span data-stu-id="2dc81-107">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="2dc81-108">ASP.NET Core 構成モデルを使用して、安全な場所からシークレットを読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dc81-108">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="2dc81-109">開発リソースおよびステージング リソースにアクセスするためのシークレットは、運用環境のリソースにアクセスするために使用するシークレットとは区別する必要があります。さまざまな人が、そのようなさまざまなシークレット セットへのアクセスを必要とするからです。</span><span class="sxs-lookup"><span data-stu-id="2dc81-109">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="2dc81-110">開発時に使用するシークレットを格納するには、環境変数にシークレットを格納するか、または ASP.NET Core Secret Manager ツールを使用してシークレットを格納する方法が一般的です。</span><span class="sxs-lookup"><span data-stu-id="2dc81-110">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="2dc81-111">運用環境でのストレージの安全性を高めるには、マイクロサービスで Azure Key Vault にシークレットを格納することができます。</span><span class="sxs-lookup"><span data-stu-id="2dc81-111">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="2dc81-112">環境変数にシークレットを格納する</span><span class="sxs-lookup"><span data-stu-id="2dc81-112">Storing secrets in environment variables</span></span>

<span data-ttu-id="2dc81-113">ソース コードの外部にシークレットを保持する方法の 1 つは、開発者用が開発用コンピューター上で文字列ベースのシークレットを[環境変数](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables)として設定するというものです。</span><span class="sxs-lookup"><span data-stu-id="2dc81-113">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="2dc81-114">環境変数を使用してシークレットを階層名 (構成セクションで入れ子にされる名前) で格納する場合、作成する変数名にはコロン (:) で区切られた、シークレット名の完全な階層を含めます。</span><span class="sxs-lookup"><span data-stu-id="2dc81-114">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="2dc81-115">たとえば、環境変数 Logging:LogLevel:Default を Debug に設定する場合、それは次の JSON ファイルから構成値を取得することと等価になります。</span><span class="sxs-lookup"><span data-stu-id="2dc81-115">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="2dc81-116">環境変数からこれらの値にアクセスするためには、アプリケーションは IConfigurationRoot オブジェクトを構築する際に ConfigurationBuilder 上で AddEnvironmentVariables を呼び出す必要があるだけです。</span><span class="sxs-lookup"><span data-stu-id="2dc81-116">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="2dc81-117">環境変数は一般にプレーン テキストとして格納されるため、環境変数が設定されたコンピューターまたはプロセスのセキュリティが侵害されると、環境変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dc81-117">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="2dc81-118">ASP.NET Core Secret Manager を使用してシークレットを格納する</span><span class="sxs-lookup"><span data-stu-id="2dc81-118">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="2dc81-119">ソース コードの外部にシークレットを保持する別の方法として、ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) ツールを使用するやり方があります。</span><span class="sxs-lookup"><span data-stu-id="2dc81-119">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="2dc81-120">Secret Manager ツールを使用するには、Microsoft.Extensions.SecretManager.Tools パッケージへのツール参照 (DotNetCliToolReference) をプロジェクト ファイル内に含めます。</span><span class="sxs-lookup"><span data-stu-id="2dc81-120">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="2dc81-121">その依存関係が存在し、それが復元されたら、dotnet user-secrets コマンドを使用して、コマンドラインからシークレットの値を設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2dc81-121">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="2dc81-122">これらのシークレットは、ユーザーのプロファイル ディレクトリにある JSON ファイルに格納され (OS によって詳細は異なる)、ソース コードから離れた場所に置かれます。</span><span class="sxs-lookup"><span data-stu-id="2dc81-122">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="2dc81-123">Secret Manager ツールによって設定されたシークレットは、シークレットを使用するプロジェクトの UserSecretsId プロパティによって編成されます。</span><span class="sxs-lookup"><span data-stu-id="2dc81-123">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="2dc81-124">そのため、プロジェクト ファイルに UserSecretsId プロパティを必ず設定する必要があります (次のスニペットに示すように)。</span><span class="sxs-lookup"><span data-stu-id="2dc81-124">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="2dc81-125">ID として使用される実際の文字列は、プロジェクト内で一意である限り重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="2dc81-125">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="2dc81-126">Secret Manager で格納されたシークレットをアプリケーションで使用するには、ConfigurationBuilder インスタンス上で AddUserSecrets&lt;T&gt; を呼び出して、アプリケーション用のシークレットをその構成に含めます。</span><span class="sxs-lookup"><span data-stu-id="2dc81-126">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="2dc81-127">ジェネリック パラメーター T は、UserSecretId が適用されたアセンブリからの型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dc81-127">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="2dc81-128">通常、AddUserSecrets&lt;Startup&gt; を使用することに問題はありません。</span><span class="sxs-lookup"><span data-stu-id="2dc81-128">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2dc81-129">[Previous] (authorization-net-microservices-web-applications.md) [Next] (azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="2dc81-129">[Previous] (authorization-net-microservices-web-applications.md) [Next] (azure-key-vault-protects-secrets.md)</span></span>
