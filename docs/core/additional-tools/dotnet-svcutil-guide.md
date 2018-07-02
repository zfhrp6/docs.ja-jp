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
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a><span data-ttu-id="46331-103">Microsoft WCF dotnet-svcutil ツール</span><span class="sxs-lookup"><span data-stu-id="46331-103">Microsoft WCF dotnet-svcutil tool</span></span>

<span data-ttu-id="46331-104">Windows Communication Foundation (WCF) **dotnet-svcutil** ツールは、ネットワーク上の場所で Web サービスから、あるいは WSDL ファイルからメタデータを取得し、Web サービス操作にアクセスするクライアント プロキシ メソッドを格納する WCF クラスを生成する .NET Core CLI ツールです。</span><span class="sxs-lookup"><span data-stu-id="46331-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="46331-105">.NET Framework プロジェクトの [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ツールと同様に、**dotnet-svcutil** は、.NET Core プロジェクトおよび .NET Standard プロジェクトと互換性のある Web サービス参照を生成するためのコマンドライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="46331-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="46331-106">**dotnet-svcutil** ツールは、Visual Studio 2017 v15.5 で最初に用意された Visual Studio 接続済みサービス プロバイダーである、[**WCF Web Service Reference**](wcf-web-service-reference-guide.md) に対する代わりのオプションです。</span><span class="sxs-lookup"><span data-stu-id="46331-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="46331-107">.NET Core CLI ツールとしての **dotnet-svcutil** ツールは、Linux、macOS、および Windows 上で利用可能なクロスプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="46331-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="46331-108">信頼できるソースのサービスのみを参照してください。</span><span class="sxs-lookup"><span data-stu-id="46331-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="46331-109">信頼できないソースの参照を追加すると、セキュリティが損なわれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="46331-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46331-110">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="46331-110">Prerequisites</span></span>

* <span data-ttu-id="46331-111">[.NET Core SDK](https://www.microsoft.com/net/download) v1.0.4 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="46331-111">[.NET Core SDK](https://www.microsoft.com/net/download) v1.0.4 or later versions</span></span>
* <span data-ttu-id="46331-112">任意のコード エディター</span><span class="sxs-lookup"><span data-stu-id="46331-112">Your favorite code editor</span></span>

## <a name="getting-started"></a><span data-ttu-id="46331-113">作業の開始</span><span class="sxs-lookup"><span data-stu-id="46331-113">Getting started</span></span>

<span data-ttu-id="46331-114">次の例では、Web サービス参照を .NET Core コンソール プロジェクトに追加してサービスを呼び出すために必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="46331-114">The following example walks you through the steps required to add a web service reference to a .NET Core console project and invoke the service.</span></span> <span data-ttu-id="46331-115">_HelloSvcutil_ という名前の .NET Core コンソール アプリケーションを作成し、次のコントラクトを実装する Web サービスへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="46331-115">You will create a .NET Core console application named _HelloSvcutil_ and will add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="46331-116">この例では、Web サービスが次のアドレスでホストされると仮定します。`http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="46331-116">For this example, the web service will be assumed to be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="46331-117">Windows、macOS、または Linux のコマンド ウィンドウから次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="46331-117">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="46331-118">次の例に示すように、_HelloSvcutil_ という名前のディレクトリをプロジェクト用に作成し、現在のディレクトリに指定します。</span><span class="sxs-lookup"><span data-stu-id="46331-118">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. <span data-ttu-id="46331-119">次に示すように、[`dotnet new`](../tools/dotnet-new.md) コマンドを使用して、このディレクトリに新しい C# コンソール プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="46331-119">Create a new C# console project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

```console
dotnet new console
```

3. <span data-ttu-id="46331-120">`HelloSvcutil.csproj` プロジェクト ファイルをエディターで開いて `Project` 要素を編集し、次のコードを使用して [`dotnet-svcutil` NuGet パッケージ](https://nuget.org/packages/dotnet-svcutil)を CLI ツールの参照として追加します。</span><span class="sxs-lookup"><span data-stu-id="46331-120">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.0" />
</ItemGroup>
```

4. <span data-ttu-id="46331-121">次に示すように、[`dotnet restore`](../tools/dotnet-restore.md) コマンドを使用して _dotnet-svcutil_ パッケージを復元します。</span><span class="sxs-lookup"><span data-stu-id="46331-121">Restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

5. <span data-ttu-id="46331-122">次に示すように、_svcutil_ コマンドを使用して _dotnet_ を実行し、Web サービス参照ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="46331-122">Run _dotnet_ with the _svcutil_ command to generate the web service reference file as follows:</span></span>

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
<span data-ttu-id="46331-123">生成したファイルは _HelloSvcutil/ServiceReference1/Reference.cs_ として保存されます。</span><span class="sxs-lookup"><span data-stu-id="46331-123">The generated file is saved as _HelloSvcutil/ServiceReference1/Reference.cs_.</span></span> <span data-ttu-id="46331-124">また、_dotnet_svcutil_ ツールでは、プロキシ コードで必要とされる適切な WCF パッケージをパッケージ参照としてプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="46331-124">The _dotnet_svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

6. <span data-ttu-id="46331-125">次に示すように、[`dotnet restore`](../tools/dotnet-restore.md) コマンドを使用して WCF パッケージを復元します。</span><span class="sxs-lookup"><span data-stu-id="46331-125">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

7. <span data-ttu-id="46331-126">`Program.cs` ファイルをエディターで開いて `Main()` メソッドを編集し、自動生成されたコードを次のコードに置き換えて Web サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="46331-126">Open the `Program.cs` file in your editor, edit the `Main()` method, and replace the auto-generated code with the following code to invoke the web service:</span></span>

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. <span data-ttu-id="46331-127">次に示すように、[`dotnet run`](../tools/dotnet-run.md) コマンドを使用してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="46331-127">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

```console
dotnet run
```
<span data-ttu-id="46331-128">"Hello dotnet-svcutil!" という出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="46331-128">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="46331-129">`dotnet-svcutil` ツールのパラメーターの詳細な説明については、次に示すように、help パラメーターを渡してツールを呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="46331-129">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>

```console
dotnet svcutil --help
```

## <a name="next-steps"></a><span data-ttu-id="46331-130">次の手順</span><span class="sxs-lookup"><span data-stu-id="46331-130">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="46331-131">フィードバックと質問</span><span class="sxs-lookup"><span data-stu-id="46331-131">Feedback & questions</span></span>

<span data-ttu-id="46331-132">質問やフィードバックがありましたら、[GitHub で問題を提起してください](https://github.com/dotnet/wcf/issues/new)。</span><span class="sxs-lookup"><span data-stu-id="46331-132">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="46331-133">[GitHub の WCF リポジトリ](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)で既存の質問や問題を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="46331-133">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="46331-134">リリース ノート</span><span class="sxs-lookup"><span data-stu-id="46331-134">Release notes</span></span>

* <span data-ttu-id="46331-135">既知の問題を含む最新のリリース情報については、[リリース ノート](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="46331-135">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

### <a name="information"></a><span data-ttu-id="46331-136">情報</span><span class="sxs-lookup"><span data-stu-id="46331-136">Information</span></span>

* [<span data-ttu-id="46331-137">dotnet-svcutil NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="46331-137">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
