---
title: "チュートリアル - 型プロバイダー (f#) を使用して Web サービスにアクセスします。"
description: "F# 3.0 で使用可能な Web サービス記述言語 (WSDL) 型プロバイダーを使用して WSDL サービスにアクセスする方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 2929198172a4e9f908daa64af19208e07859263f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a><span data-ttu-id="22929-104">チュートリアル : 型プロバイダーを使用した Web サービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="22929-104">Walkthrough: Accessing a Web Service by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="22929-105">このガイドでは、f# 3.0 用に作成された、更新されます。</span><span class="sxs-lookup"><span data-stu-id="22929-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="22929-106">最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](https://fsharp.github.io/FSharp.Data/) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22929-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="22929-107">API リファレンス リンクで msdn を実行します。</span><span class="sxs-lookup"><span data-stu-id="22929-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="22929-108">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="22929-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="22929-109">このチュートリアルでは、F# 3.0 で利用可能な Web サービス記述言語 (WSDL) 型プロバイダーを使用して WSDL サービスにアクセスする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="22929-109">This walkthrough shows you how to use the Web Services Description Language (WSDL) type provider that is available in F# 3.0 to access a WSDL service.</span></span> <span data-ttu-id="22929-110">他の .NET 言語では、svcutil.exe を呼び出すか、または Web 参照を追加して Web サービスにアクセスするためのコードを生成します。たとえば、C# プロジェクトの場合は、Visual Studio で svcutil.exe を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="22929-110">In other .NET languages, you generate the code to access the web service by calling svcutil.exe, or by adding a web reference in, for example, a C# project to get Visual Studio to call svcutil.exe for you.</span></span> <span data-ttu-id="22929-111">F# では、WSDL 型プロバイダーを使用する追加オプションがあるので、WsdlService 型を作成するコードを記述するとすぐに型が生成されて使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="22929-111">In F#, you have the additional option of using the WSDL type provider, so as soon as you write the code that creates the WsdlService type, the types are generated and become available.</span></span> <span data-ttu-id="22929-112">このプロセスは、コードを記述するときに利用できるサービスに依存します。</span><span class="sxs-lookup"><span data-stu-id="22929-112">This process relies on the service being available when you are writing the code.</span></span>

<span data-ttu-id="22929-113">このチュートリアルでは、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="22929-113">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="22929-114">このチュートリアルを正しく行うには、以下の作業を順に行ってください。</span><span class="sxs-lookup"><span data-stu-id="22929-114">You must complete them in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="22929-115">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="22929-115">Creating the project</span></span>
<br />

- <span data-ttu-id="22929-116">型プロバイダーの構成</span><span class="sxs-lookup"><span data-stu-id="22929-116">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="22929-117">Web サービスの呼び出しと結果の処理</span><span class="sxs-lookup"><span data-stu-id="22929-117">Calling the web service, and processing the results</span></span>
<br />


## <a name="creating-the-project"></a><span data-ttu-id="22929-118">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="22929-118">Creating the project</span></span>
<span data-ttu-id="22929-119">この手順では、プロジェクトを作成し、WSDL 型プロバイダーを使用するために適切な参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="22929-119">In the step, you create a project and add the appropriate references to use a WSDL type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="22929-120">F# プロジェクトを作成してセットアップするには</span><span class="sxs-lookup"><span data-stu-id="22929-120">To create and set up an F# project</span></span>

1. <span data-ttu-id="22929-121">新しい F# コンソール アプリケーション プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="22929-121">Open a new F# Console Application project.</span></span>
<br />

2. <span data-ttu-id="22929-122">**ソリューション エクスプ ローラー**、ショートカット メニューを開き、プロジェクトの**参照** ノードを選択し**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="22929-122">In **Solution Explorer**, open the shortcut menu for the project's **Reference** node, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="22929-123">**アセンブリ**領域で、選択**Framework**をクリックし、使用可能なアセンブリの一覧で、選択**System.Runtime.Serialization**と**System.ServiceModel**です。</span><span class="sxs-lookup"><span data-stu-id="22929-123">In the **Assemblies** area, choose **Framework**, and then, in the list of available assemblies, choose **System.Runtime.Serialization** and **System.ServiceModel**.</span></span>
<br />

4. <span data-ttu-id="22929-124">**アセンブリ**領域で、選択**拡張**です。</span><span class="sxs-lookup"><span data-stu-id="22929-124">In the **Assemblies** area, choose **Extensions**.</span></span>
<br />

5. <span data-ttu-id="22929-125">使用可能なアセンブリの一覧で選択**FSharp.Data.TypeProviders**を選択し、 **[ok]**をこれらのアセンブリへの参照を追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="22929-125">In the list of available assemblies, choose **FSharp.Data.TypeProviders**, and then choose the **OK** button to add references to these assemblies.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="22929-126">型プロバイダーの構成</span><span class="sxs-lookup"><span data-stu-id="22929-126">Configuring the type provider</span></span>
<span data-ttu-id="22929-127">この手順では、WSDL 型プロバイダーを使用して TerraServer Web サービスの型を生成します。</span><span class="sxs-lookup"><span data-stu-id="22929-127">In this step, you use the WSDL type provider to generate types for the TerraServer web service.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="22929-128">型プロバイダーを構成して型を生成するには</span><span class="sxs-lookup"><span data-stu-id="22929-128">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="22929-129">型プロバイダーの名前空間を開くには、以下のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="22929-129">Add the following line of code to open the type provider namespace.</span></span>
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. <span data-ttu-id="22929-130">Web サービスで型プロバイダーを呼び出すには、以下のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="22929-130">Add the following line of code to invoke the type provider with a web service.</span></span> <span data-ttu-id="22929-131">この例では、TerraServer Web サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="22929-131">In this example, use the TerraServer web service.</span></span>
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "https://terraserver-usa.com/TerraService2.asmx?WSDL" https://msrmaps.com/TerraService2.asmx?WSDL">
```

  <span data-ttu-id="22929-132">サービス URI にスペル ミスがある場合、サービス自体が停止している場合、または動作していない場合は、このコード行の下に赤の波線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="22929-132">A red squiggle appears under this line of code if the service URI is misspelled or if the service itself is down or isn’t performing.</span></span> <span data-ttu-id="22929-133">コードをポイントすると、問題を説明するエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="22929-133">If you point to the code, an error message describes the problem.</span></span> <span data-ttu-id="22929-134">同じ情報を見つけることができます、**エラー一覧**ウィンドウまたは、**出力ウィンドウ**をビルドした後です。</span><span class="sxs-lookup"><span data-stu-id="22929-134">You can find the same information in the **Error List** window or in the **Output Window** after you build.</span></span>
<br />  <span data-ttu-id="22929-135">WSDL 接続の構成設定を指定するには、プロジェクトの app.config ファイルを使用する方法と、型プロバイダーの宣言で静的な型パラメーターを使用する方法の 2 とおりあります。</span><span class="sxs-lookup"><span data-stu-id="22929-135">There are two ways to specify configuration settings for a WSDL connection, by using the app.config file for the project, or by using the static type parameters in the type provider declaration.</span></span> <span data-ttu-id="22929-136">svcutil.exe を使用すると、適切な構成ファイル要素を生成できます。</span><span class="sxs-lookup"><span data-stu-id="22929-136">You can use svcutil.exe to generate appropriate configuration file elements.</span></span> <span data-ttu-id="22929-137">Svcutil.exe を使用して、web サービスの構成情報を生成する方法の詳細については、次を参照してください。 [ServiceModel メタデータ ユーティリティ ツールと #40 です。Svcutil.exe &#41;](https://msdn.microsoft.com/library/aa347733.aspx).</span><span class="sxs-lookup"><span data-stu-id="22929-137">For more information about using svcutil.exe to generate configuration information for a web service, see [ServiceModel Metadata Utility Tool &#40;Svcutil.exe&#41;](https://msdn.microsoft.com/library/aa347733.aspx).</span></span> <span data-ttu-id="22929-138">WSDL 型プロバイダーの静的な型パラメーターの詳細を参照してください。 [WsdlService 型プロバイダー](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)です。</span><span class="sxs-lookup"><span data-stu-id="22929-138">For a full description of the static type parameters for the WSDL type provider, see [WsdlService Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span></span>
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a><span data-ttu-id="22929-139">Web サービスの呼び出しと結果の処理</span><span class="sxs-lookup"><span data-stu-id="22929-139">Calling the web service, and processing the results</span></span>
<span data-ttu-id="22929-140">各 Web サービスには、メソッド呼び出しのパラメーターとして使用される独自の型のセットがあります。</span><span class="sxs-lookup"><span data-stu-id="22929-140">Each web service has its own set of types that are used as parameters for its method calls.</span></span> <span data-ttu-id="22929-141">この手順では、これらのパラメーターを準備して Web メソッドを呼び出し、返される情報を処理します。</span><span class="sxs-lookup"><span data-stu-id="22929-141">In this step, you prepare these parameters, call a web method, and process the information that it returns.</span></span>


#### <a name="to-call-the-web-service-and-process-the-results"></a><span data-ttu-id="22929-142">Web サービスを呼び出して結果を処理するには</span><span class="sxs-lookup"><span data-stu-id="22929-142">To call the web service, and process the results</span></span>

1. <span data-ttu-id="22929-143">Web サービスにはタイムアウトや機能停止の可能性があるので、例外処理ブロックに Web サービス呼び出しを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="22929-143">The web service might time out or stop functioning, so you should include the web service call in an exception handling block.</span></span> <span data-ttu-id="22929-144">Web サービスからデータを取得するには、次のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="22929-144">Write the following code to try to get data from the web service.</span></span>
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

<span data-ttu-id="22929-145">Web サービスなどのために必要なデータ型を作成することに注意してください。**場所**と**場所**、WsdlService 入れ子にされた型の型として、 **TerraService**です。</span><span class="sxs-lookup"><span data-stu-id="22929-145">Notice that you create the data types that are needed for the web service, such as **Place** and **Location**, as nested types under the WsdlService type **TerraService**.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="22929-146">参照</span><span class="sxs-lookup"><span data-stu-id="22929-146">See Also</span></span>
[<span data-ttu-id="22929-147">WsdlService 型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="22929-147">WsdlService Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[<span data-ttu-id="22929-148">型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="22929-148">Type Providers</span></span>](index.md)
