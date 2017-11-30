---
title: "開発時にアプリケーションの機密情報を安全に格納"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |開発時にアプリケーションの機密情報を安全に格納"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f1b8b257a3e677c7e665e1d394a8adf7e651bec2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="1c559-104">開発時にアプリケーションの機密情報を安全に格納</span><span class="sxs-lookup"><span data-stu-id="1c559-104">Storing application secrets safely during development</span></span>

<span data-ttu-id="1c559-105">保護されたリソースとその他のサービスに接続するに ASP.NET Core アプリケーションは、通常の接続文字列、パスワード、または他の機密情報を含む資格情報を使用する必要です。</span><span class="sxs-lookup"><span data-stu-id="1c559-105">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="1c559-106">この機密情報と呼ばれます*シークレット*です。</span><span class="sxs-lookup"><span data-stu-id="1c559-106">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="1c559-107">ベスト プラクティスをソース コード内の機密情報を含めない確かを除く、ソース管理に機密情報を保存することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1c559-107">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="1c559-108">代わりに、ASP.NET Core の構成モデルを使用して、安全な場所からシークレットを読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c559-108">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="1c559-109">開発へのアクセスとステージング環境のさまざまな個人は、これらの機密情報のセットへのアクセスを必要があるため、運用環境のリソースにアクセスするときに使用されるリソースのシークレットを分離する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c559-109">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="1c559-110">開発時に使用される機密情報を保存するには、一般的なアプローチは、環境変数または ASP.NET Core シークレット マネージャー ツールを使用して機密情報を保存するかといます。</span><span class="sxs-lookup"><span data-stu-id="1c559-110">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="1c559-111">実稼働環境でのより安全な記憶域、microservices は、Azure Key Vault に機密情報を保存することができます。</span><span class="sxs-lookup"><span data-stu-id="1c559-111">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="1c559-112">環境変数に機密情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="1c559-112">Storing secrets in environment variables</span></span>

<span data-ttu-id="1c559-113">ソース コードからシークレットを保持する方法の 1 つとして文字列ベースのシークレットを設定する開発者用[環境変数](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables)開発用コンピューターでします。</span><span class="sxs-lookup"><span data-stu-id="1c559-113">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="1c559-114">(これらの構成セクションで入れ子になった) 階層の名前を持つ機密情報の格納を完全名のシークレットの階層を含む環境変数の名前を作成し、環境変数を使用する場合は、コロン (:) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="1c559-114">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="1c559-115">たとえば、デバッグにログ記録: LogLevel:Default 環境変数の設定、次の JSON ファイルから、構成値と等価のようになります。</span><span class="sxs-lookup"><span data-stu-id="1c559-115">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="1c559-116">環境変数からこれらの値にアクセスするに、アプリケーションは IConfigurationRoot オブジェクトを構築するときに、その ConfigurationBuilder で AddEnvironmentVariables を呼び出すだけが必要です。</span><span class="sxs-lookup"><span data-stu-id="1c559-116">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="1c559-117">環境変数がプレーン テキストとして格納されることに注意してください。 コンピューターまたは環境変数とプロセスは、セキュリティが侵害された環境変数の値が表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="1c559-117">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="1c559-118">ASP.NET Core シークレット マネージャーを使用して機密情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="1c559-118">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="1c559-119">ASP.NET Core[シークレット Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager)ツールは、ソース コードからシークレットを保持するための別のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1c559-119">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="1c559-120">シークレット マネージャー ツールを使用するには、Microsoft.Extensions.SecretManager.Tools パッケージは、プロジェクト ファイル内にツール リファレンス (DotNetCliToolReference) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c559-120">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="1c559-121">その依存関係が存在し、復元されて、コマンドラインからのシークレットの値を設定する dotnet ユーザー シークレット コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c559-121">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="1c559-122">これらのシークレットは、ユーザーのプロファイル ディレクトリにあります (詳細は OS によって異なる場合)、ソース コードから離れた場所での JSON ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1c559-122">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="1c559-123">シークレット シークレット マネージャー ツールによって設定は、機密情報を使用しているプロジェクトの UserSecretsId プロパティで構成されます。</span><span class="sxs-lookup"><span data-stu-id="1c559-123">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="1c559-124">そのため、(次のスニペットに示すように) と、プロジェクト ファイルで UserSecretsId プロパティを設定することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c559-124">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="1c559-125">プロジェクト内で一意である限り、ID として使用される実際の文字列は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="1c559-125">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="1c559-126">AddUserSecrets を呼び出すことにより実現は、アプリケーションでシークレット マネージャーに格納されているシークレットを使用して&lt;T&gt;構成に含める、アプリケーションのシークレットの ConfigurationBuilder インスタンスにします。</span><span class="sxs-lookup"><span data-stu-id="1c559-126">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="1c559-127">ジェネリック パラメーター T は、UserSecretId に適用されたアセンブリから型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c559-127">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="1c559-128">通常 AddUserSecrets を使用して&lt;スタートアップ&gt;問題ありません。</span><span class="sxs-lookup"><span data-stu-id="1c559-128">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1c559-129">[前](承認-net-microservices-web-applications.md) [次へ] (azure のキーの資格情報コンテナーの保護-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="1c559-129">[Previous] (authorization-net-microservices-web-applications.md) [Next] (azure-key-vault-protects-secrets.md)</span></span>
