---
title: "フィード フォーマッタ (JSON)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9ce141c2292d4afe6900aba93c972b63abb2056
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="feed-formatter-json"></a><span data-ttu-id="af49a-102">フィード フォーマッタ (JSON)</span><span class="sxs-lookup"><span data-stu-id="af49a-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="af49a-103">このサンプルでは、カスタムの <xref:System.ServiceModel.Syndication.SyndicationFeed> および <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> を使用することにより JSON (JavaScript Object Notation) 形式の <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> クラスのインスタンスをシリアル化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="af49a-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="af49a-104">サンプルのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="af49a-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="af49a-105">このサンプルは `JsonFeedFormatter` を継承する <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> という名前のクラスを実行します。</span><span class="sxs-lookup"><span data-stu-id="af49a-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="af49a-106">`JsonFeedFormatter` クラスは <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> に依存し、JSON 形式でデータの読み取りと書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="af49a-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="af49a-107">内部的には、フォーマッタは `JsonSyndicationFeed` および `JsonSyndicationItem` という名前のデータ コントラクト型のカスタム セットを使用し、シリアライザによって生成される JSON データの形式を制御します。</span><span class="sxs-lookup"><span data-stu-id="af49a-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="af49a-108">これらの実装の詳細はエンド ユーザーには表示されず、標準的な <xref:System.ServiceModel.Syndication.SyndicationFeed> および <xref:System.ServiceModel.Syndication.SyndicationItem> クラスに対する呼び出しを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="af49a-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="af49a-109">JSON フィードの書き込み</span><span class="sxs-lookup"><span data-stu-id="af49a-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="af49a-110">次のコード例に示すように、JSON フィードの書き込みは `JsonFeedFormatter` (このサンプルで実装) を <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> と共に使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="af49a-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
```  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
```  
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="af49a-111">JSON フィードの読み取り</span><span class="sxs-lookup"><span data-stu-id="af49a-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="af49a-112">次のコードに示すように、JSON 形式のデータのストリームからの <xref:System.ServiceModel.Syndication.SyndicationFeed> の取得は `JsonFeedFormatter` を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="af49a-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="af49a-113">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="af49a-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="af49a-114">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="af49a-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="af49a-115">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="af49a-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="af49a-116">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="af49a-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="af49a-117">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="af49a-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="af49a-118">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="af49a-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="af49a-119">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="af49a-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af49a-120">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="af49a-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="af49a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="af49a-121">See Also</span></span>
