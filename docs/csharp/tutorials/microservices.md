---
title: Docker でホストされているマイクロサービス - C
description: Docker コンテナーで実行される ASP.NET Core サービスを作成する方法を学ぶ
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 1f4b38243beb1210b1374bd701fac66b2fa72cc5
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106351"
---
# <a name="microservices-hosted-in-docker"></a>Docker でホストされているマイクロサービス

このチュートリアルでは、Docker コンテナーにおける ASP.NET Core マイクロサービスの構築および展開に必要な作業について説明します。 このチュートリアルを通して、以下のことを学びます。

* ASP.NET Core アプリケーションを生成する方法
* Docker の開発環境を作成する方法
* 既存のイメージに基づいて Docker イメージを構築する方法
* Docker コンテナーにお使いのサービスを展開する方法

この過程で、C# 言語の機能もいくつか説明します。

* C# オブジェクトを JSON ペイロードに変換する方法
* 変更できないデータ転送オブジェクトをビルドする方法
* 受信 HTTP 要求を処理し、HTTP 応答を生成する方法
* Null 許容の値型を操作する方法

このトピックの[サンプル アプリを表示またはダウンロード](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice)できます。 ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。

## <a name="why-docker"></a>Docker を使用する理由

Docker を使うと、簡単に標準的なコンピューター イメージを作成し、データ センターやパブリック クラウドでサービスをホストすることができます。 Docker ではイメージを構成することができ、必要に応じてイメージを複製してアプリケーションのインストール サイズを拡大縮小することができます。

このチュートリアルに含まれるコードはすべて、どんな .NET Core 環境でも動作します。
Docker インストールの追加タスクは、ASP.NET Core アプリケーションで機能します。 

## <a name="prerequisites"></a>必須コンポーネント

お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。 インストールの手順については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。
このアプリケーションは、Windows、Linux、macOS または Docker コンテナーで実行できます。
お好みのコード エディターをインストールしてください。 次の説明では、オープン ソースのクロス プラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用しています。 しかし、他の使い慣れたツールを使用しても構いません。

Docker エンジンをインストールする必要もあります。 お使いのプラットフォームに関する手順については、[Docker インストールのページ](http://www.docker.com/products/docker)を参照してください。
Docker は、多くの Linux ディストリビューション、macOS、または Windows にインストールすることができます。 上記のページには、インストールが可能なものについてそれぞれ説明が含まれています。

## <a name="create-the-application"></a>アプリケーションを作成する

すべてのツールをインストールしたら、お気に入りのシェルを使用して次のコマンドを実行し、"WeatherMicroservice" というディレクトリに新しい ASP.NET Core アプリケーションを作成します。

```console
dotnet new web -o WeatherMicroservice
```

`dotnet` コマンドは、.NET 開発に必要なツールを実行します。 動詞はそれぞれ、別々のコマンドを実行します。

.NET Core プロジェクトを作成するには、`dotnet new` コマンドを使用します。

`dotnet new` コマンドの後の `-o WeatherMicroservice` オプションは、ASP.NET Core アプリケーションの作成場所を指定するために使用されます。

このマイクロサービスでは、できる限り単純で軽量な Web アプリケーションが必要なため、"ASP.NET Core Empty" テンプレートを、テンプレートの短い名前 `web` を指定して使用しました。

テンプレートによって 4 つのファイルが作成されます。

* Startup.cs ファイル。 このファイルには、アプリケーションの基礎が含まれています。
* Program.cs ファイル。 このファイルには、アプリケーションのエントリ ポイントが含まれています。
* WeatherMicroservice.csproj ファイル。 これがアプリケーションのビルド ファイルです。
* Properties/launchSettings.json ファイル。 このファイルには、IDE で使用されるデバッグの設定が含まれています。

これで、テンプレートで生成されたアプリケーションを実行できるようになりました。

```console
dotnet run
```

このコマンドは、最初にアプリケーションのビルドに必要な依存関係を復元してから、アプリケーションをビルドします。

既定の構成では `http://localhost:5000` がリッスンされます。 ブラウザーを開いてそのページに移動すると、"Hello World!" という メッセージが表示されます。

完了したら、<kbd>Ctrl</kbd>+<kbd>C</kbd> キーを押してアプリケーションをシャットダウンできます。

### <a name="anatomy-of-an-aspnet-core-application"></a>ASP.NET Core アプリケーションの構造

アプリケーションがビルドされたので、この機能が実装される仕組みを見てみましょう。 生成されたファイルのうち、この時点で特に重要なのは、WeatherMicroservice.json と Startup.cs の 2 つです。 

csproj.json には、プロジェクトに関する情報が格納されています。
最も興味深い 2 つのノードは、`<TargetFramework>` と `<PackageReference>` です。

`<TargetFramework>` ノードは、このアプリケーションで実行する .NET のバージョンを指定します。

各 `<PackageReference>` ノードは、このアプリケーションに必要なパッケージを指定するのに使用されます。

アプリケーションは Startup.cs に実装されます。 このファイルにはスタートアップ クラスが含まれています。

これら 2 つのメソッドは ASP.NET Core インフラストラクチャによって呼び出され、アプリケーションを構成および実行します。 `ConfigureServices` メソッドではこのアプリケーションに必要なサービスが記述されます。 簡潔なマイクロサービスを作成するので、依存関係が構成される必要はありません。 `Configure` メソッドでは受信 HTTP 要求のハンドラ―が構成されます。 このテンプレートでは、あらゆる要求に 'Hello World!' というテキストで応答する単純なハンドラーが生成されます。

## <a name="build-a-microservice"></a>マイクロサービスの構築

これから構築するサービスは、世界中のあらゆる場所から天気予報を提供するものです。 実際に稼働するアプリケーションでは、通常なんらかのサービスを呼び出して気象データを取得します。 このサンプルでは、ランダムな天気予報を生成します。 

ランダムな天気予報サービスを実装するには、タスクをいくつか実行する必要があります。

* 受信要求を解析し、緯度と経度を読み取る。
* ランダムな予報データを生成する。
* そのランダムな予報データを、C# オブジェクトから JSON パケットに変換する。
* 応答ヘッダーを設定して、サービスが JSON を送り返すことを示す。
* 応答を書き込む。

以降のセクションで、これらの手順をそれぞれ順を追って説明します。

### <a name="parsing-the-query-string"></a>クエリ文字列の解析

クエリ文字列の解析から始めます。 サービスは、次の形式で、クエリ文字列の 'lat' 引数および 'long' 引数を受け取ります。

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

変更が必要なものは、スタートアップ クラス内の `app.Run` への引数として定義されているラムダ式にすべてあります。

ラムダ式の引数は、要求の `HttpContext` です。 そのプロパティの 1 つは `Request` オブジェクトです。 `Request` オブジェクトには `Query` プロパティが含まれており、このプロパティには、要求のクエリ文字列のすべての値のディクショナリが含まれています。 最初に追加するのは、緯度の値と経度の値の検索です。

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

`Query` のディクショナリ値は `StringValue` 型です。 その型には、文字列のコレクションを含めることができます。 この天気予報サービスでは、各値は 1 つの文字列です。 そのために、上記のコードには `FirstOrDefault()` への呼び出しが含まれています。 

次に、文字列を double 型に変換する必要があります。 文字列を double 型に変換するには `double.TryParse()` メソッドを使用します。

```csharp
bool TryParse(string s, out double result);
```

このメソッドは C# の out パラメーターを活用して、入力文字列を double 型に変換できるかどうかを示します。 文字列が double 型の有効な表現を表している場合、メソッドは true を返し、`result` 引数にその値が含まれます。 文字列が有効な double 型の値を表していない場合、メソッドは false を返します。

その API は、*null 許容の double 型*を返す*拡張メソッド*を使用して適応させることができます。 *null 許容の値型*は、いくつかの値型を表す型で、欠落した値、すなわち null 値を保持できます。 null 許容型は、型宣言に `?` 文字を追加することで表されます。 

拡張メソッドは静的メソッドとして定義されますが、最初のパラメーターに `this` 修飾子を追加することにより、そのクラスのメンバーとして呼び出すことができます。 拡張メソッドは、静的クラスでのみ定義できます。 解析の拡張メソッドを含むクラスの定義を次に示します。

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

拡張メソッドを呼び出す前に、現在のカルチャをインバリアントに変更します。

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

これにより、既定のカルチャに関係なく、アプリケーションが任意のサーバー上で同じように数を分析できるようになります。

これで、拡張メソッドを使用して、クエリ文字列の引数を double 型に変換することができます。

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

解析コードを簡単にテストするために、引数の値が含まれるように応答を更新します。

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

この時点で、Web アプリケーションを実行して、解析コードが機能しているかどうかを確認することができます。 ブラウザーで Web 要求に値を追加すると、更新された結果が表示されます。

### <a name="build-a-random-weather-forecast"></a>ランダムな天気予報の構築

次のタスクは、ランダムな天気予報の構築です。 天気予報に使用する値を格納するデータ コンテナーから始めましょう。

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions =
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HighTemperatureFahrenheit { get; }
    public int LowTemperatureFahrenheit { get; }
    public int AverageWindSpeedMph { get; }
    public string Condition { get; }
}
```

次に、これらの値をランダムに設定するコンストラクターを構築します。 このコンストラクターは、緯度と経度の値を使用して `Random` 値ジェネレーターに値を設定します。 つまり同じ場所の予報は同じということになります。 緯度と経度の引数を変更すると、異なる予報が得られます (異なる値を与えたため)。

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

これで、応答メソッドで 5 日間の予報を生成できるようになりました。

```csharp
if (latitude.HasValue && longitude.HasValue)
{
    var forecast = new List<WeatherReport>();
    for (var days = 1; days <= 5; days++)
    {
        forecast.Add(new WeatherReport(latitude.Value, longitude.Value, days));
    }
}
```

### <a name="build-the-json-response"></a>JSON 応答のビルド

サーバー上の最後のコード作業は、`WeatherReport` リストを JSON ドキュメントに変換し、それをクライアントに送信して返すことです。 まず JSON ドキュメントを作成しましょう。 Newtonsoft JSON シリアライザーを、依存関係の一覧に追加します。 これは次の `dotnet` コマンドを使用して行うことができます。

```console
dotnet add package Newtonsoft.Json
```

すると、`JsonConvert` クラスを使用して、文字列にオブジェクトを書き込めるようになります。

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

上記のコードは、予報オブジェクト (一連の `WeatherForecast` オブジェクト) を JSON ドキュメントに変換します。 応答ドキュメントを作成したら、コンテンツの種類を `application/json` に設定し、文字列を書き込みます。

これで、アプリケーションが実行され、ランダムな予報が返されます。

## <a name="build-a-docker-image"></a>Docker イメージの構築

最後のタスクは、Docker でのアプリケーションの実行です。 アプリケーションを表す Docker イメージを実行する Docker コンテナーを作成します。

***Docker イメージ***は、アプリケーションを実行するための環境を定義するファイルです。

***Docker コンテナー***は、Docker イメージの実行インスタンスを表します。

たとえて言うと、*Docker イメージ*は*クラス*として、*Docker コンテナー*はオブジェクトまたはそのクラスのインスタンスとして、考えることができます。  

これには、次の Dockerfile が役立ちます。

```
FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

その内容を見てみましょう。

最初の行は、アプリケーションのビルドに使用するソース イメージを指定します。

```
FROM microsoft/dotnet:2.1-sdk AS build
```

Docker では、ソース テンプレートに基づいてマシン イメージを構成することができます。 つまり、開始時にすべてのマシン パラメーターを指定する必要はなく、変更箇所のみを指定すればよいことになります。 ここでの変更は、このアプリケーションの組み込みです。

このサンプルでは、`dotnet` イメージの `2.1-sdk` バージョンを使用します。 Docker の稼働環境を作成するにはこれが最も簡単な方法です。 このイメージには、.NET Core ランタイムと .NET Core SDK が含まれています。
これにより、開始してビルドするのが容易になりますが、より大きなイメージが作成されるため、このイメージをアプリケーションのビルドに使用して、実行には別のイメージを使用します。

次の行は、アプリケーションを設定してビルドします。

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

これでプロジェクト ファイルが現在のディレクトリから Docker VM にコピーされ、すべてのパッケージが復元されます。 .Net CLI を使用するということは、Docker イメージに .NET Core SDK を含める必要があるということになります。 その後、アプリケーションの残りの部分がコピーされ、`dotnet
publish` コマンドによってアプリケーションがビルドされパッケージ化されます。

最後に、アプリケーションを実行する 2 番目の Docker イメージを作成します。

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

このイメージでは、`dotnet` イメージの `2.1-aspnetcore-runtime` バージョンを使用します。このバージョンには、ASP.NET Core アプリケーションを実行するために必要なすべてのものが含まれていますが、.NET Core SDK は含まれていません。 つまり、このイメージを使用して .NET Core アプリケーションをビルドすることはできませんが、最終イメージを小さくすることができます。

これを行うには、最初のイメージからビルドされたアプリケーションを 2 番目のイメージにコピーします。

`ENTRYPOINT` コマンドは、サービスを開始するコマンドを Docker に通知します。

## <a name="building-and-running-the-image-in-a-container"></a>コンテナー内でのイメージのビルドと実行

イメージを構築して Docker コンテナー内でサービスを実行しましょう。 ローカル ディレクトリにあるすべてのファイルをイメージにコピーする必要はありません。 代わりに、コンテナーでアプリケーションをビルドします。 `.dockerignore` ファイルを作成して、イメージにコピーしないディレクトリを指定します。 ビルド資産はいっさいコピーしません。 `.dockerignore` ファイルに、ビルド ディレクトリおよび発行のディレクトリを指定します。

```
bin/*
obj/*
out/*
```

`docker build` コマンドを使用してイメージを作成します。 自分のコードが含まれているディレクトリで、次のコマンドを実行します。

```console
docker build -t weather-microservice .
```

このコマンドは、Dockerfile 内のすべての情報を基にコンテナー イメージを作成するものです。 `-t` 引数によって、このコンテナー イメージのタグ、つまり名前が提供されます。 上記のコマンド ラインで Docker コンテナーに使用したタグは `weather-microservice` です。 このコマンドが完了したら、新しいサービスを実行するコンテナーの準備は完了です。 

次のコマンドを実行して、コンテナーを起動しサービスを開始します。

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

`-d` オプションは、コンテナ―を現在のターミナルからデタッチして実行することを意味します。 つまり、お使いの端末にはコマンドの出力は表示されないということです。 `-p` オプションは、サービスとホストの間のポート マッピングを示しています。 ここでは、コンテナー上でポート 80 上のすべての受信要求をポート 80 に転送するように命令しています。 80 の使用は、サービスがリッスンしているポート (実稼働アプリケーションの既定のポート) と一致します。 `--name` 引数は実行中のコンテナーに名前を付けます。 この名前は、そのコンテナーの操作に使用するのに便利です。

次のコマンドにより、イメージが実行されているかどうかを確認できます。

```console
docker ps
```

コンテナーが実行されている場合は、実行中のプロセスをリストした行が表示されます。 (1 つだけかもしれません。)

ブラウザーを開いて localhost に移動し、緯度と経度を指定して、サービスをテストすることができます。

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a>実行中のコンテナーへのアタッチ

コマンド ウィンドウでサービスを実行したとき、要求ごとに診断情報が表示されました。 この情報は、コンテナーがデタッチ モードで実行されているときは表示されません。 Docker の attach コマンドを使用すると、実行中のコンテナーにアタッチして、ログ情報が表示されるようにできます。  コマンド ウィンドウから次のコマンドを実行します。

```console
docker attach --sig-proxy=false hello-docker
```

`--sig-proxy=false` 引数は、<kbd>Ctrl</kbd>+<kbd>C</kbd> コマンドがコンテナー プロセスには送信されるのではなく、`docker attach` コマンドを停止するものであることを意味します。 最後の引数は、`docker run` コマンドでコンテナーに与えられた名前です。 

> [!NOTE]
> Docker が割り当てられたコンテナー ID を使用して、任意のコンテナーを参照することもできます。 `docker run` でコンテナーに名前を指定していない場合は、コンテナー ID を使用する必要があります。

ブラウザーを開き、サービスに移動します。 アタッチされている実行中のコンテナーのコマンド ウィンドウ内で診断メッセージが表示されます。

<kbd>Ctrl</kbd>+<kbd>C</kbd> キーを押して、アタッチ プロセスを停止します。

コンテナー操作を終了したら、停止することができます。

```console
docker stop hello-docker
```

コンテナーとイメージは引き続き再起動できます。  コンテナーをコンピューターから削除する場合は、このコマンドを使用します。

```console
docker rm hello-docker
```

使用していないイメージをコンピューターから削除する場合は、このコマンドを使用します。

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a>まとめ 

このチュートリアルでは、ASP.NET Core マイクロサービスを構築し、単純な機能をいくつか追加しました。

そのサービスの Docker コンテナー イメージを構築し、コンピューターでそのコンテナーを実行しました。 サービスにターミナル ウィンドウをアタッチし、サービスからの診断メッセージを確認しました。

その流れで、C# 言語の機能のうちいくつかが実際に動作していることを確認しました。
