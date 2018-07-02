---
title: Docker でホストされているマイクロサービス - C
description: Docker コンテナーで実行される ASP.NET Core サービスを作成する方法を学ぶ
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: b043b0109bcf8a67867d2c73a5ab22e43a4963cf
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208003"
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="37f3c-103">Docker でホストされているマイクロサービス</span><span class="sxs-lookup"><span data-stu-id="37f3c-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="37f3c-104">このチュートリアルでは、Docker コンテナーにおける ASP.NET Core マイクロサービスの構築および展開に必要な作業について説明します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="37f3c-105">このチュートリアルを通して、以下のことを学びます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="37f3c-106">ASP.NET Core アプリケーションを生成する方法</span><span class="sxs-lookup"><span data-stu-id="37f3c-106">How to generate an ASP.NET Core application.</span></span>
* <span data-ttu-id="37f3c-107">Docker の開発環境を作成する方法</span><span class="sxs-lookup"><span data-stu-id="37f3c-107">How to create a development Docker environment.</span></span>
* <span data-ttu-id="37f3c-108">既存のイメージに基づいて Docker イメージを構築する方法</span><span class="sxs-lookup"><span data-stu-id="37f3c-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="37f3c-109">Docker コンテナーにお使いのサービスを展開する方法</span><span class="sxs-lookup"><span data-stu-id="37f3c-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="37f3c-110">この過程で、C# 言語の機能もいくつか説明します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="37f3c-111">C# オブジェクトを JSON ペイロードに変換する方法</span><span class="sxs-lookup"><span data-stu-id="37f3c-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="37f3c-112">変更できないデータ転送オブジェクトをビルドする方法</span><span class="sxs-lookup"><span data-stu-id="37f3c-112">How to build immutable Data Transfer Objects.</span></span>
* <span data-ttu-id="37f3c-113">受信 HTTP 要求を処理し、HTTP 応答を生成する方法</span><span class="sxs-lookup"><span data-stu-id="37f3c-113">How to process incoming HTTP Requests and generate the HTTP Response.</span></span>
* <span data-ttu-id="37f3c-114">Null 許容の値型を操作する方法</span><span class="sxs-lookup"><span data-stu-id="37f3c-114">How to work with nullable value types.</span></span>

<span data-ttu-id="37f3c-115">このトピックの[サンプル アプリを表示またはダウンロード](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice)できます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="37f3c-116">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37f3c-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="why-docker"></a><span data-ttu-id="37f3c-117">Docker を使用する理由</span><span class="sxs-lookup"><span data-stu-id="37f3c-117">Why Docker?</span></span>

<span data-ttu-id="37f3c-118">Docker を使うと、簡単に標準的なコンピューター イメージを作成し、データ センターやパブリック クラウドでサービスをホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="37f3c-119">Docker ではイメージを構成することができ、必要に応じてイメージを複製してアプリケーションのインストール サイズを拡大縮小することができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="37f3c-120">このチュートリアルに含まれるコードはすべて、どんな .NET Core 環境でも動作します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="37f3c-121">Docker インストールの追加タスクは、ASP.NET Core アプリケーションで機能します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="37f3c-122">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="37f3c-122">Prerequisites</span></span>

<span data-ttu-id="37f3c-123">お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-123">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="37f3c-124">インストールの手順については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37f3c-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="37f3c-125">このアプリケーションは、Windows、Linux、macOS または Docker コンテナーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-125">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="37f3c-126">お好みのコード エディターをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="37f3c-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="37f3c-127">次の説明では、オープン ソースのクロス プラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="37f3c-128">しかし、他の使い慣れたツールを使用しても構いません。</span><span class="sxs-lookup"><span data-stu-id="37f3c-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="37f3c-129">Docker エンジンをインストールする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="37f3c-130">お使いのプラットフォームに関する手順については、[Docker インストールのページ](http://www.docker.com/products/docker)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37f3c-130">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="37f3c-131">Docker は、多くの Linux ディストリビューション、macOS、または Windows にインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="37f3c-132">上記のページには、インストールが可能なものについてそれぞれ説明が含まれています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-132">The page referenced above contains sections to each of the available installations.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="37f3c-133">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="37f3c-133">Create the Application</span></span>

<span data-ttu-id="37f3c-134">すべてのツールをインストールしたら、新しい ASP.NET Core アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-134">Now that you've installed all the tools, create a new ASP.NET Core application.</span></span> <span data-ttu-id="37f3c-135">これを行うには、"WeatherMicroservice" という新しいディレクトリを作成し、お好みのシェルで、そのディレクトリ内で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-135">To do that, create a new directory called "WeatherMicroservice" and execute the following command in that directory in your favorite shell:</span></span>

```console
dotnet new web
```

<span data-ttu-id="37f3c-136">`dotnet` コマンドは、.NET 開発に必要なツールを実行します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-136">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="37f3c-137">動詞はそれぞれ、別々のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-137">Each verb executes a different command.</span></span>

<span data-ttu-id="37f3c-138">.NET Core プロジェクトを作成するには、`dotnet new` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-138">The `dotnet new` command is used to create .Net Core projects.</span></span>

<span data-ttu-id="37f3c-139">このマイクロサービスでは、できる限り単純で軽量な Web アプリケーションが必要なため、"ASP.NET Core Empty" テンプレートを、テンプレートの短い名前 `web` を指定して使用しました。</span><span class="sxs-lookup"><span data-stu-id="37f3c-139">For this microservice, we want the simplest, most lightweight web application possible, so we used the "ASP.NET Core Empty" template, by specifying its short name, `web`.</span></span>

<span data-ttu-id="37f3c-140">テンプレートによって 4 つのファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-140">The template creates four files for you:</span></span>

* <span data-ttu-id="37f3c-141">Startup.cs ファイル。</span><span class="sxs-lookup"><span data-stu-id="37f3c-141">A Startup.cs file.</span></span> <span data-ttu-id="37f3c-142">このファイルには、アプリケーションの基礎が含まれています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-142">This contains the basis of the application.</span></span>
* <span data-ttu-id="37f3c-143">Program.cs ファイル。</span><span class="sxs-lookup"><span data-stu-id="37f3c-143">A Program.cs file.</span></span> <span data-ttu-id="37f3c-144">このファイルには、アプリケーションのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-144">This contains the entry point of the application.</span></span>
* <span data-ttu-id="37f3c-145">WeatherMicroservice.csproj ファイル。</span><span class="sxs-lookup"><span data-stu-id="37f3c-145">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="37f3c-146">これがアプリケーションのビルド ファイルです。</span><span class="sxs-lookup"><span data-stu-id="37f3c-146">This is the build file for the application.</span></span>
* <span data-ttu-id="37f3c-147">Properties/launchSettings.json ファイル。</span><span class="sxs-lookup"><span data-stu-id="37f3c-147">A Properties/launchSettings.json file.</span></span> <span data-ttu-id="37f3c-148">このファイルには、IDE で使用されるデバッグの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-148">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="37f3c-149">これで、テンプレートで生成されたアプリケーションを実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="37f3c-149">Now you can run the template generated application:</span></span>

```console
dotnet run
```

<span data-ttu-id="37f3c-150">このコマンドは、最初にアプリケーションのビルドに必要な依存関係を復元してから、アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="37f3c-150">This command will first restore dependencies required to build the application and then it will build the application.</span></span>

<span data-ttu-id="37f3c-151">既定の構成では `http://localhost:5000` がリッスンされます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-151">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="37f3c-152">ブラウザーを開いてそのページに移動すると、"Hello World!" という</span><span class="sxs-lookup"><span data-stu-id="37f3c-152">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="37f3c-153">メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-153">message.</span></span>

<span data-ttu-id="37f3c-154">完了したら、<kbd>Ctrl</kbd>+<kbd>C</kbd> キーを押してアプリケーションをシャットダウンできます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-154">When you're done, you can shut down the application by pressing <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="37f3c-155">ASP.NET Core アプリケーションの構造</span><span class="sxs-lookup"><span data-stu-id="37f3c-155">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="37f3c-156">アプリケーションがビルドされたので、この機能が実装される仕組みを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="37f3c-156">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="37f3c-157">生成されたファイルのうち、この時点で特に重要なのは、WeatherMicroservice.json と Startup.cs の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="37f3c-157">There are two of the generated files that are particularly interesting at this point: WeatherMicroservice.csproj and Startup.cs.</span></span> 

<span data-ttu-id="37f3c-158">csproj.json には、プロジェクトに関する情報が格納されています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-158">The .csproj file contains information about the project.</span></span>
<span data-ttu-id="37f3c-159">最も興味深い 2 つのノードは、`<TargetFramework>` と `<PackageReference>` です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-159">The two nodes that are most interesting are `<TargetFramework>` and `<PackageReference>`.</span></span>

<span data-ttu-id="37f3c-160">`<TargetFramework>` ノードは、このアプリケーションで実行する .NET のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-160">The `<TargetFramework>` node specifies the version of .NET that will run this application.</span></span>

<span data-ttu-id="37f3c-161">各 `<PackageReference>` ノードは、このアプリケーションに必要なパッケージを指定するのに使用されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-161">Each `<PackageReference>` node is used to specify a package that is needed for this application.</span></span>

<span data-ttu-id="37f3c-162">アプリケーションは Startup.cs に実装されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-162">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="37f3c-163">このファイルにはスタートアップ クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-163">This file contains the startup class.</span></span>

<span data-ttu-id="37f3c-164">これら 2 つのメソッドは ASP.NET Core インフラストラクチャによって呼び出され、アプリケーションを構成および実行します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-164">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="37f3c-165">`ConfigureServices` メソッドではこのアプリケーションに必要なサービスが記述されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-165">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="37f3c-166">簡潔なマイクロサービスを作成するので、依存関係が構成される必要はありません。</span><span class="sxs-lookup"><span data-stu-id="37f3c-166">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="37f3c-167">`Configure` メソッドでは受信 HTTP 要求のハンドラ―が構成されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-167">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="37f3c-168">このテンプレートでは、あらゆる要求に 'Hello World!' というテキストで応答する単純なハンドラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-168">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="37f3c-169">マイクロサービスの構築</span><span class="sxs-lookup"><span data-stu-id="37f3c-169">Build a microservice</span></span>

<span data-ttu-id="37f3c-170">これから構築するサービスは、世界中のあらゆる場所から天気予報を提供するものです。</span><span class="sxs-lookup"><span data-stu-id="37f3c-170">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="37f3c-171">実際に稼働するアプリケーションでは、通常なんらかのサービスを呼び出して気象データを取得します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-171">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="37f3c-172">このサンプルでは、ランダムな天気予報を生成します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-172">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="37f3c-173">ランダムな天気予報サービスを実装するには、タスクをいくつか実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-173">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="37f3c-174">受信要求を解析し、緯度と経度を読み取る。</span><span class="sxs-lookup"><span data-stu-id="37f3c-174">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="37f3c-175">ランダムな予報データを生成する。</span><span class="sxs-lookup"><span data-stu-id="37f3c-175">Generate some random forecast data.</span></span>
* <span data-ttu-id="37f3c-176">そのランダムな予報データを、C# オブジェクトから JSON パケットに変換する。</span><span class="sxs-lookup"><span data-stu-id="37f3c-176">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="37f3c-177">応答ヘッダーを設定して、サービスが JSON を送り返すことを示す。</span><span class="sxs-lookup"><span data-stu-id="37f3c-177">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="37f3c-178">応答を書き込む。</span><span class="sxs-lookup"><span data-stu-id="37f3c-178">Write the response.</span></span>

<span data-ttu-id="37f3c-179">以降のセクションで、これらの手順をそれぞれ順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-179">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="37f3c-180">クエリ文字列の解析</span><span class="sxs-lookup"><span data-stu-id="37f3c-180">Parsing the Query String</span></span>

<span data-ttu-id="37f3c-181">クエリ文字列の解析から始めます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-181">You'll begin by parsing the query string.</span></span> <span data-ttu-id="37f3c-182">サービスは、次の形式で、クエリ文字列の 'lat' 引数および 'long' 引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-182">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

<span data-ttu-id="37f3c-183">変更が必要なものは、スタートアップ クラス内の `app.Run` への引数として定義されているラムダ式にすべてあります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-183">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="37f3c-184">ラムダ式の引数は、要求の `HttpContext` です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-184">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="37f3c-185">そのプロパティの 1 つは `Request` オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="37f3c-185">One of its properties is the `Request` object.</span></span> <span data-ttu-id="37f3c-186">`Request` オブジェクトには `Query` プロパティが含まれており、このプロパティには、要求のクエリ文字列のすべての値のディクショナリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-186">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="37f3c-187">最初に追加するのは、緯度の値と経度の値の検索です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-187">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="37f3c-188">`Query` のディクショナリ値は `StringValue` 型です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-188">The `Query` dictionary values are `StringValue` type.</span></span> <span data-ttu-id="37f3c-189">その型には、文字列のコレクションを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-189">That type can contain a collection of strings.</span></span> <span data-ttu-id="37f3c-190">この天気予報サービスでは、各値は 1 つの文字列です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-190">For your weather service, each value is a single string.</span></span> <span data-ttu-id="37f3c-191">そのために、上記のコードには `FirstOrDefault()` への呼び出しが含まれています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-191">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="37f3c-192">次に、文字列を double 型に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-192">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="37f3c-193">文字列を double 型に変換するには `double.TryParse()` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-193">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="37f3c-194">このメソッドは C# の out パラメーターを活用して、入力文字列を double 型に変換できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-194">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="37f3c-195">文字列が double 型の有効な表現を表している場合、メソッドは true を返し、`result` 引数にその値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-195">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="37f3c-196">文字列が有効な double 型の値を表していない場合、メソッドは false を返します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-196">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="37f3c-197">その API は、*null 許容の double 型*を返す*拡張メソッド*を使用して適応させることができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-197">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="37f3c-198">*null 許容の値型*は、いくつかの値型を表す型で、欠落した値、すなわち null 値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-198">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="37f3c-199">null 許容型は、型宣言に `?` 文字を追加することで表されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-199">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="37f3c-200">拡張メソッドは静的メソッドとして定義されますが、最初のパラメーターに `this` 修飾子を追加することにより、そのクラスのメンバーとして呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-200">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="37f3c-201">拡張メソッドは、静的クラスでのみ定義できます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-201">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="37f3c-202">解析の拡張メソッドを含むクラスの定義を次に示します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-202">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="37f3c-203">拡張メソッドを呼び出す前に、現在のカルチャをインバリアントに変更します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-203">Before calling the extension method, change the current culture to invariant:</span></span>

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

<span data-ttu-id="37f3c-204">これにより、既定のカルチャに関係なく、アプリケーションが任意のサーバー上で同じように数を分析できるようになります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-204">This ensures that your application parses numbers the same on any server, regardless of its default culture.</span></span>

<span data-ttu-id="37f3c-205">これで、拡張メソッドを使用して、クエリ文字列の引数を double 型に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-205">Now you can use the extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="37f3c-206">解析コードを簡単にテストするために、引数の値が含まれるように応答を更新します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-206">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="37f3c-207">この時点で、Web アプリケーションを実行して、解析コードが機能しているかどうかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-207">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="37f3c-208">ブラウザーで Web 要求に値を追加すると、更新された結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-208">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="37f3c-209">ランダムな天気予報の構築</span><span class="sxs-lookup"><span data-stu-id="37f3c-209">Build a random weather forecast</span></span>

<span data-ttu-id="37f3c-210">次のタスクは、ランダムな天気予報の構築です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-210">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="37f3c-211">天気予報に使用する値を格納するデータ コンテナーから始めましょう。</span><span class="sxs-lookup"><span data-stu-id="37f3c-211">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

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

<span data-ttu-id="37f3c-212">次に、これらの値をランダムに設定するコンストラクターを構築します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-212">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="37f3c-213">このコンストラクターは、緯度と経度の値を使用して `Random` 値ジェネレーターに値を設定します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-213">This constructor uses the values for the latitude and longitude to seed the `Random` number generator.</span></span> <span data-ttu-id="37f3c-214">つまり同じ場所の予報は同じということになります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-214">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="37f3c-215">緯度と経度の引数を変更すると、異なる予報が得られます (異なる値を与えたため)。</span><span class="sxs-lookup"><span data-stu-id="37f3c-215">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed).</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="37f3c-216">これで、応答メソッドで 5 日間の予報を生成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="37f3c-216">You can now generate the 5-day forecast in your response method:</span></span>

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

### <a name="build-the-json-response"></a><span data-ttu-id="37f3c-217">JSON 応答のビルド</span><span class="sxs-lookup"><span data-stu-id="37f3c-217">Build the JSON response</span></span>

<span data-ttu-id="37f3c-218">サーバー上の最後のコード作業は、`WeatherReport` リストを JSON ドキュメントに変換し、それをクライアントに送信して返すことです。</span><span class="sxs-lookup"><span data-stu-id="37f3c-218">The final code task on the server is to convert the `WeatherReport` list into JSON document, and send that back to the client.</span></span> <span data-ttu-id="37f3c-219">まず JSON ドキュメントを作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="37f3c-219">Let's start by creating the JSON document.</span></span> <span data-ttu-id="37f3c-220">Newtonsoft JSON シリアライザーを、依存関係の一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-220">You'll add the Newtonsoft JSON serializer to the list of dependencies.</span></span> <span data-ttu-id="37f3c-221">これは次の `dotnet` コマンドを使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-221">You can do that using the following `dotnet` command:</span></span>

```console
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="37f3c-222">すると、`JsonConvert` クラスを使用して、文字列にオブジェクトを書き込めるようになります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-222">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="37f3c-223">上記のコードは、予報オブジェクト (一連の `WeatherForecast` オブジェクト) を JSON ドキュメントに変換します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-223">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON document.</span></span> <span data-ttu-id="37f3c-224">応答ドキュメントを作成したら、コンテンツの種類を `application/json` に設定し、文字列を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-224">After you've constructed the response document, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="37f3c-225">これで、アプリケーションが実行され、ランダムな予報が返されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-225">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="37f3c-226">Docker イメージの構築</span><span class="sxs-lookup"><span data-stu-id="37f3c-226">Build a Docker image</span></span>

<span data-ttu-id="37f3c-227">最後のタスクは、Docker でのアプリケーションの実行です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-227">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="37f3c-228">アプリケーションを表す Docker イメージを実行する Docker コンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-228">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="37f3c-229">***Docker イメージ***は、アプリケーションを実行するための環境を定義するファイルです。</span><span class="sxs-lookup"><span data-stu-id="37f3c-229">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="37f3c-230">***Docker コンテナー***は、Docker イメージの実行インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-230">A ***Docker Container*** represents a running instance of a Docker Image.</span></span>

<span data-ttu-id="37f3c-231">たとえて言うと、*Docker イメージ*は*クラス*として、*Docker コンテナー*はオブジェクトまたはそのクラスのインスタンスとして、考えることができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-231">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="37f3c-232">これには、次の Dockerfile が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-232">The following Dockerfile will serve for our purposes:</span></span>

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

<span data-ttu-id="37f3c-233">その内容を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="37f3c-233">Let's go over its contents.</span></span>

<span data-ttu-id="37f3c-234">最初の行は、アプリケーションのビルドに使用するソース イメージを指定します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-234">The first line specifies the source image used for building the application:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
```

<span data-ttu-id="37f3c-235">Docker では、ソース テンプレートに基づいてマシン イメージを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-235">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="37f3c-236">つまり、開始時にすべてのマシン パラメーターを指定する必要はなく、変更箇所のみを指定すればよいことになります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-236">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="37f3c-237">ここでの変更は、このアプリケーションの組み込みです。</span><span class="sxs-lookup"><span data-stu-id="37f3c-237">The changes here will be to include our application.</span></span>

<span data-ttu-id="37f3c-238">このサンプルでは、`dotnet` イメージの `2.1-sdk` バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-238">In this sample, we'll use the `2.1-sdk` version of the `dotnet` image.</span></span> <span data-ttu-id="37f3c-239">Docker の稼働環境を作成するにはこれが最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-239">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="37f3c-240">このイメージには、.NET Core ランタイムと .NET Core SDK が含まれています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-240">This image includes the .NET Core runtime, and the .NET Core SDK.</span></span>
<span data-ttu-id="37f3c-241">これにより、開始してビルドするのが容易になりますが、より大きなイメージが作成されるため、このイメージをアプリケーションのビルドに使用して、実行には別のイメージを使用します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-241">That makes it easier to get started and build, but does create a larger image, so we'll use this image for building the application and a different image to run it.</span></span>

<span data-ttu-id="37f3c-242">次の行は、アプリケーションを設定してビルドします。</span><span class="sxs-lookup"><span data-stu-id="37f3c-242">The next lines setup and build your application:</span></span>

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="37f3c-243">これでプロジェクト ファイルが現在のディレクトリから Docker VM にコピーされ、すべてのパッケージが復元されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-243">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="37f3c-244">.Net CLI を使用するということは、Docker イメージに .NET Core SDK を含める必要があるということになります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-244">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="37f3c-245">その後、アプリケーションの残りの部分がコピーされ、`dotnet
publish` コマンドによってアプリケーションがビルドされパッケージ化されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-245">After that, the rest of your application gets copied, and the `dotnet
publish` command builds and packages your application.</span></span>

<span data-ttu-id="37f3c-246">最後に、アプリケーションを実行する 2 番目の Docker イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-246">Finally, we create a second Docker image that runs the application:</span></span>

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="37f3c-247">このイメージでは、`dotnet` イメージの `2.1-aspnetcore-runtime` バージョンを使用します。このバージョンには、ASP.NET Core アプリケーションを実行するために必要なすべてのものが含まれていますが、.NET Core SDK は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="37f3c-247">This image uses the `2.1-aspnetcore-runtime` version of the `dotnet` image, which contains everything necessary to run ASP.NET Core applications, but does not include the .NET Core SDK.</span></span> <span data-ttu-id="37f3c-248">つまり、このイメージを使用して .NET Core アプリケーションをビルドすることはできませんが、最終イメージを小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-248">This means this image can't be used to build .NET Core applications, but it also makes the final image smaller.</span></span>

<span data-ttu-id="37f3c-249">これを行うには、最初のイメージからビルドされたアプリケーションを 2 番目のイメージにコピーします。</span><span class="sxs-lookup"><span data-stu-id="37f3c-249">To make this work, we copy the built application from the first image to the second one.</span></span>

<span data-ttu-id="37f3c-250">`ENTRYPOINT` コマンドは、サービスを開始するコマンドを Docker に通知します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-250">The `ENTRYPOINT` command informs Docker what command starts the service.</span></span>

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="37f3c-251">コンテナー内でのイメージのビルドと実行</span><span class="sxs-lookup"><span data-stu-id="37f3c-251">Building and running the image in a container</span></span>

<span data-ttu-id="37f3c-252">イメージを構築して Docker コンテナー内でサービスを実行しましょう。</span><span class="sxs-lookup"><span data-stu-id="37f3c-252">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="37f3c-253">ローカル ディレクトリにあるすべてのファイルをイメージにコピーする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="37f3c-253">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="37f3c-254">代わりに、コンテナーでアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="37f3c-254">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="37f3c-255">`.dockerignore` ファイルを作成して、イメージにコピーしないディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-255">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="37f3c-256">ビルド資産はいっさいコピーしません。</span><span class="sxs-lookup"><span data-stu-id="37f3c-256">You don't want any of the build assets copied.</span></span> <span data-ttu-id="37f3c-257">`.dockerignore` ファイルに、ビルド ディレクトリおよび発行のディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-257">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="37f3c-258">`docker build` コマンドを使用してイメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-258">You build the image using the `docker build` command.</span></span> <span data-ttu-id="37f3c-259">自分のコードが含まれているディレクトリで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-259">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="37f3c-260">このコマンドは、Dockerfile 内のすべての情報を基にコンテナー イメージを作成するものです。</span><span class="sxs-lookup"><span data-stu-id="37f3c-260">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="37f3c-261">`-t` 引数によって、このコンテナー イメージのタグ、つまり名前が提供されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-261">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="37f3c-262">上記のコマンド ラインで Docker コンテナーに使用したタグは `weather-microservice` です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-262">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="37f3c-263">このコマンドが完了したら、新しいサービスを実行するコンテナーの準備は完了です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-263">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="37f3c-264">次のコマンドを実行して、コンテナーを起動しサービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-264">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

<span data-ttu-id="37f3c-265">`-d` オプションは、コンテナ―を現在のターミナルからデタッチして実行することを意味します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-265">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="37f3c-266">つまり、お使いの端末にはコマンドの出力は表示されないということです。</span><span class="sxs-lookup"><span data-stu-id="37f3c-266">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="37f3c-267">`-p` オプションは、サービスとホストの間のポート マッピングを示しています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-267">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="37f3c-268">ここでは、コンテナー上でポート 80 上のすべての受信要求をポート 80 に転送するように命令しています。</span><span class="sxs-lookup"><span data-stu-id="37f3c-268">Here it says that any incoming request on port 80 should be forwarded to port 80 on the container.</span></span> <span data-ttu-id="37f3c-269">80 の使用は、サービスがリッスンしているポート (実稼働アプリケーションの既定のポート) と一致します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-269">Using 80 matches the port your service is listening on, which is the default port for production applications.</span></span> <span data-ttu-id="37f3c-270">`--name` 引数は実行中のコンテナーに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-270">The `--name` argument names your running container.</span></span> <span data-ttu-id="37f3c-271">この名前は、そのコンテナーの操作に使用するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-271">It's a convenient name you can use to work with that container.</span></span>

<span data-ttu-id="37f3c-272">次のコマンドにより、イメージが実行されているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-272">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="37f3c-273">コンテナーが実行されている場合は、実行中のプロセスをリストした行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-273">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="37f3c-274">(1 つだけかもしれません。)</span><span class="sxs-lookup"><span data-stu-id="37f3c-274">(It may be the only one.)</span></span>

<span data-ttu-id="37f3c-275">ブラウザーを開いて localhost に移動し、緯度と経度を指定して、サービスをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-275">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="37f3c-276">実行中のコンテナーへのアタッチ</span><span class="sxs-lookup"><span data-stu-id="37f3c-276">Attaching to a running container</span></span>

<span data-ttu-id="37f3c-277">コマンド ウィンドウでサービスを実行したとき、要求ごとに診断情報が表示されました。</span><span class="sxs-lookup"><span data-stu-id="37f3c-277">When you ran your service in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="37f3c-278">この情報は、コンテナーがデタッチ モードで実行されているときは表示されません。</span><span class="sxs-lookup"><span data-stu-id="37f3c-278">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="37f3c-279">Docker の attach コマンドを使用すると、実行中のコンテナーにアタッチして、ログ情報が表示されるようにできます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-279">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="37f3c-280">コマンド ウィンドウから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-280">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="37f3c-281">`--sig-proxy=false` 引数は、<kbd>Ctrl</kbd>+<kbd>C</kbd> コマンドがコンテナー プロセスには送信されるのではなく、`docker attach` コマンドを停止するものであることを意味します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-281">The `--sig-proxy=false` argument means that <kbd>Ctrl</kbd>+<kbd>C</kbd> commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="37f3c-282">最後の引数は、`docker run` コマンドでコンテナーに与えられた名前です。</span><span class="sxs-lookup"><span data-stu-id="37f3c-282">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="37f3c-283">Docker が割り当てられたコンテナー ID を使用して、任意のコンテナーを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-283">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="37f3c-284">`docker run` でコンテナーに名前を指定していない場合は、コンテナー ID を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37f3c-284">If you didn't specify a name for your container in `docker run` you must use the container ID.</span></span>

<span data-ttu-id="37f3c-285">ブラウザーを開き、サービスに移動します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-285">Open a browser and navigate to your service.</span></span> <span data-ttu-id="37f3c-286">アタッチされている実行中のコンテナーのコマンド ウィンドウ内で診断メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-286">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="37f3c-287"><kbd>Ctrl</kbd>+<kbd>C</kbd> キーを押して、アタッチ プロセスを停止します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-287">Press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the attach process.</span></span>

<span data-ttu-id="37f3c-288">コンテナー操作を終了したら、停止することができます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-288">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="37f3c-289">コンテナーとイメージは引き続き再起動できます。</span><span class="sxs-lookup"><span data-stu-id="37f3c-289">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="37f3c-290">コンテナーをコンピューターから削除する場合は、このコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-290">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="37f3c-291">使用していないイメージをコンピューターから削除する場合は、このコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="37f3c-291">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="37f3c-292">まとめ</span><span class="sxs-lookup"><span data-stu-id="37f3c-292">Conclusion</span></span> 

<span data-ttu-id="37f3c-293">このチュートリアルでは、ASP.NET Core マイクロサービスを構築し、単純な機能をいくつか追加しました。</span><span class="sxs-lookup"><span data-stu-id="37f3c-293">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="37f3c-294">そのサービスの Docker コンテナー イメージを構築し、コンピューターでそのコンテナーを実行しました。</span><span class="sxs-lookup"><span data-stu-id="37f3c-294">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="37f3c-295">サービスにターミナル ウィンドウをアタッチし、サービスからの診断メッセージを確認しました。</span><span class="sxs-lookup"><span data-stu-id="37f3c-295">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="37f3c-296">その流れで、C# 言語の機能のうちいくつかが実際に動作していることを確認しました。</span><span class="sxs-lookup"><span data-stu-id="37f3c-296">Along the way, you saw several features of the C# language in action.</span></span>
