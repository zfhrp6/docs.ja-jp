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
# <a name="storing-application-secrets-safely-during-development"></a>開発時にアプリケーションの機密情報を安全に格納

保護されたリソースとその他のサービスに接続するに ASP.NET Core アプリケーションは、通常の接続文字列、パスワード、または他の機密情報を含む資格情報を使用する必要です。 この機密情報と呼ばれます*シークレット*です。 ベスト プラクティスをソース コード内の機密情報を含めない確かを除く、ソース管理に機密情報を保存することをお勧めします。 代わりに、ASP.NET Core の構成モデルを使用して、安全な場所からシークレットを読み取る必要があります。

開発へのアクセスとステージング環境のさまざまな個人は、これらの機密情報のセットへのアクセスを必要があるため、運用環境のリソースにアクセスするときに使用されるリソースのシークレットを分離する必要があります。 開発時に使用される機密情報を保存するには、一般的なアプローチは、環境変数または ASP.NET Core シークレット マネージャー ツールを使用して機密情報を保存するかといます。 実稼働環境でのより安全な記憶域、microservices は、Azure Key Vault に機密情報を保存することができます。

## <a name="storing-secrets-in-environment-variables"></a>環境変数に機密情報を格納します。

ソース コードからシークレットを保持する方法の 1 つとして文字列ベースのシークレットを設定する開発者用[環境変数](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables)開発用コンピューターでします。 (これらの構成セクションで入れ子になった) 階層の名前を持つ機密情報の格納を完全名のシークレットの階層を含む環境変数の名前を作成し、環境変数を使用する場合は、コロン (:) で区切られます。

たとえば、デバッグにログ記録: LogLevel:Default 環境変数の設定、次の JSON ファイルから、構成値と等価のようになります。

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

環境変数からこれらの値にアクセスするに、アプリケーションは IConfigurationRoot オブジェクトを構築するときに、その ConfigurationBuilder で AddEnvironmentVariables を呼び出すだけが必要です。

環境変数がプレーン テキストとして格納されることに注意してください。 コンピューターまたは環境変数とプロセスは、セキュリティが侵害された環境変数の値が表示されるようにします。

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>ASP.NET Core シークレット マネージャーを使用して機密情報を格納します。

ASP.NET Core[シークレット Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager)ツールは、ソース コードからシークレットを保持するための別のメソッドを提供します。 シークレット マネージャー ツールを使用するには、Microsoft.Extensions.SecretManager.Tools パッケージは、プロジェクト ファイル内にツール リファレンス (DotNetCliToolReference) が含まれます。 その依存関係が存在し、復元されて、コマンドラインからのシークレットの値を設定する dotnet ユーザー シークレット コマンドを使用できます。 これらのシークレットは、ユーザーのプロファイル ディレクトリにあります (詳細は OS によって異なる場合)、ソース コードから離れた場所での JSON ファイルに格納されます。

シークレット シークレット マネージャー ツールによって設定は、機密情報を使用しているプロジェクトの UserSecretsId プロパティで構成されます。 そのため、(次のスニペットに示すように) と、プロジェクト ファイルで UserSecretsId プロパティを設定することを確認する必要があります。 プロジェクト内で一意である限り、ID として使用される実際の文字列は重要ではありません。

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

AddUserSecrets を呼び出すことにより実現は、アプリケーションでシークレット マネージャーに格納されているシークレットを使用して&lt;T&gt;構成に含める、アプリケーションのシークレットの ConfigurationBuilder インスタンスにします。 ジェネリック パラメーター T は、UserSecretId に適用されたアセンブリから型である必要があります。 通常 AddUserSecrets を使用して&lt;スタートアップ&gt;問題ありません。


>[!div class="step-by-step"]
[前](承認-net-microservices-web-applications.md) [次へ] (azure のキーの資格情報コンテナーの保護-secrets.md)
