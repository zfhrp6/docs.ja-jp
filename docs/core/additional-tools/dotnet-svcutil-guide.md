---
title: Microsoft WCF dotnet-svcutil ツール
description: .NET Framework プロジェクトの WCF svcutil ツールと同様に、.NET Core プロジェクトと ASP.NET Core プロジェクトの機能を追加する Microsoft WCF dotnet-svcutil ツールの概要。
author: mlacouture
ms.author: jralexander
ms.date: 06/04/2018
ms.openlocfilehash: c40dd9b437afe7381244b944228b6b2efe046eb2
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753423"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a>Microsoft WCF dotnet-svcutil ツール

Windows Communication Foundation (WCF) **dotnet-svcutil** ツールは、ネットワーク上の場所で Web サービスから、あるいは WSDL ファイルからメタデータを取得し、Web サービス操作にアクセスするクライアント プロキシ メソッドを格納する WCF クラスを生成する .NET Core CLI ツールです。

.NET Framework プロジェクトの [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ツールと同様に、**dotnet-svcutil** は、.NET Core プロジェクトおよび .NET Standard プロジェクトと互換性のある Web サービス参照を生成するためのコマンドライン ツールです。

**dotnet-svcutil** ツールは、Visual Studio 2017 v15.5 で最初に用意された Visual Studio 接続済みサービス プロバイダーである、[**WCF Web Service Reference**](wcf-web-service-reference-guide.md) に対する代わりのオプションです。 .NET Core CLI ツールとしての **dotnet-svcutil** ツールは、Linux、macOS、および Windows 上で利用可能なクロスプラットフォームです。

> [!IMPORTANT]
> 信頼できるソースのサービスのみを参照してください。 信頼できないソースの参照を追加すると、セキュリティが損なわれる可能性があります。

## <a name="prerequisites"></a>必須コンポーネント

* [.NET Core SDK](https://www.microsoft.com/net/download) v1.0.4 以降のバージョン
* 任意のコード エディター

## <a name="getting-started"></a>作業の開始

次の例では、Web サービス参照を .NET Core コンソール プロジェクトに追加してサービスを呼び出すために必要な手順について説明します。 _HelloSvcutil_ という名前の .NET Core コンソール アプリケーションを作成し、次のコントラクトを実装する Web サービスへの参照を追加します。

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

この例では、Web サービスが次のアドレスでホストされると仮定します。`http://contoso.com/SayHello.svc`

Windows、macOS、または Linux のコマンド ウィンドウから次の手順を実行します。

1. 次の例に示すように、_HelloSvcutil_ という名前のディレクトリをプロジェクト用に作成し、現在のディレクトリに指定します。

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. 次に示すように、[`dotnet new`](../tools/dotnet-new.md) コマンドを使用して、このディレクトリに新しい C# コンソール プロジェクトを作成します。

```console
dotnet new console
```

3. `HelloSvcutil.csproj` プロジェクト ファイルをエディターで開いて `Project` 要素を編集し、次のコードを使用して [`dotnet-svcutil` NuGet パッケージ](https://nuget.org/packages/dotnet-svcutil)を CLI ツールの参照として追加します。

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.0" />
</ItemGroup>
```

4. 次に示すように、[`dotnet restore`](../tools/dotnet-restore.md) コマンドを使用して _dotnet-svcutil_ パッケージを復元します。

```console
dotnet restore
```

5. 次に示すように、_svcutil_ コマンドを使用して _dotnet_ を実行し、Web サービス参照ファイルを生成します。

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
生成したファイルは _HelloSvcutil/ServiceReference1/Reference.cs_ として保存されます。 また、_dotnet_svcutil_ ツールでは、プロキシ コードで必要とされる適切な WCF パッケージをパッケージ参照としてプロジェクトに追加します。

6. 次に示すように、[`dotnet restore`](../tools/dotnet-restore.md) コマンドを使用して WCF パッケージを復元します。

```console
dotnet restore
```

7. `Program.cs` ファイルをエディターで開いて `Main()` メソッドを編集し、自動生成されたコードを次のコードに置き換えて Web サービスを呼び出します。

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. 次に示すように、[`dotnet run`](../tools/dotnet-run.md) コマンドを使用してアプリケーションを実行します。

```console
dotnet run
```
"Hello dotnet-svcutil!" という出力が表示されます。

`dotnet-svcutil` ツールのパラメーターの詳細な説明については、次に示すように、help パラメーターを渡してツールを呼び出してください。

```console
dotnet svcutil --help
```

## <a name="next-steps"></a>次の手順

### <a name="feedback--questions"></a>フィードバックと質問

質問やフィードバックがありましたら、[GitHub で問題を提起してください](https://github.com/dotnet/wcf/issues/new)。 [GitHub の WCF リポジトリ](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)で既存の質問や問題を確認することもできます。

### <a name="release-notes"></a>リリース ノート

* 既知の問題を含む最新のリリース情報については、[リリース ノート](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md)のページを参照してください。

### <a name="information"></a>情報

* [dotnet-svcutil NuGet パッケージ](https://nuget.org/packages/dotnet-svcutil)
