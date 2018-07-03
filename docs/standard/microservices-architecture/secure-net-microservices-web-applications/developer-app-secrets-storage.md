---
title: 開発時にアプリケーションの機密情報を安全に格納する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 開発時にアプリケーションの機密情報を安全に格納する
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 560120db35ae190bdef1f95d72ac1e5de697124e
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105947"
---
# <a name="storing-application-secrets-safely-during-development"></a>開発時にアプリケーションの機密情報を安全に格納する

保護されたリソースおよびその他のサービスに接続する場合、ASP.NET Core アプリケーションは、通常、接続文字列やパスワードなど、機密情報を含む資格情報を使用する必要があります。 このような機密情報は、"*シークレット*" と呼ばれます。 ソース コードに機密情報を含めないこと、さらに決してソース管理に機密情報を格納しないことがベスト プラクティスです。 ASP.NET Core 構成モデルを使用して、安全な場所からシークレットを読み取る必要があります。

開発リソースおよびステージング リソースにアクセスするためのシークレットは、運用環境のリソースにアクセスするために使用するシークレットとは区別する必要があります。さまざまな人が、そのようなさまざまなシークレット セットへのアクセスを必要とするからです。 開発時に使用するシークレットを格納するには、環境変数にシークレットを格納するか、または ASP.NET Core Secret Manager ツールを使用してシークレットを格納する方法が一般的です。 運用環境でのストレージの安全性を高めるには、マイクロサービスで Azure Key Vault にシークレットを格納することができます。

## <a name="storing-secrets-in-environment-variables"></a>環境変数にシークレットを格納する

ソース コードの外部にシークレットを保持する方法の 1 つは、開発者用が開発用コンピューター上で文字列ベースのシークレットを[環境変数](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables)として設定するというものです。 環境変数を使用してシークレットを階層名 (構成セクションで入れ子にされる名前) で格納する場合、作成する変数名にはコロン (:) で区切られた、シークレット名の完全な階層を含めます。

たとえば、環境変数 Logging:LogLevel:Default を Debug に設定する場合、それは次の JSON ファイルから構成値を取得することと等価になります。

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

環境変数からこれらの値にアクセスするためには、アプリケーションは IConfigurationRoot オブジェクトを構築する際に ConfigurationBuilder 上で AddEnvironmentVariables を呼び出す必要があるだけです。

環境変数は一般にプレーン テキストとして格納されるため、環境変数が設定されたコンピューターまたはプロセスのセキュリティが侵害されると、環境変数の値が表示されます。

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>ASP.NET Core Secret Manager を使用してシークレットを格納する

ソース コードの外部にシークレットを保持する別の方法として、ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) ツールを使用するやり方があります。 Secret Manager ツールを使用するには、Microsoft.Extensions.SecretManager.Tools パッケージへのツール参照 (DotNetCliToolReference) をプロジェクト ファイル内に含めます。 その依存関係が存在し、それが復元されたら、dotnet user-secrets コマンドを使用して、コマンドラインからシークレットの値を設定できるようになります。 これらのシークレットは、ユーザーのプロファイル ディレクトリにある JSON ファイルに格納され (OS によって詳細は異なる)、ソース コードから離れた場所に置かれます。

Secret Manager ツールによって設定されたシークレットは、シークレットを使用するプロジェクトの UserSecretsId プロパティによって編成されます。 そのため、プロジェクト ファイルに UserSecretsId プロパティを必ず設定する必要があります (次のスニペットに示すように)。 ID として使用される実際の文字列は、プロジェクト内で一意である限り重要ではありません。

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Secret Manager で格納されたシークレットをアプリケーションで使用するには、ConfigurationBuilder インスタンス上で AddUserSecrets&lt;T&gt; を呼び出して、アプリケーション用のシークレットをその構成に含めます。 ジェネリック パラメーター T は、UserSecretId が適用されたアセンブリからの型である必要があります。 通常、AddUserSecrets&lt;Startup&gt; を使用することに問題はありません。


>[!div class="step-by-step"]
[前へ](authorization-net-microservices-web-applications.md)
[次へ](azure-key-vault-protects-secrets.md)
