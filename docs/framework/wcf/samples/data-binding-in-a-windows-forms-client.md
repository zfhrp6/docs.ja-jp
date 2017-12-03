---
title: "Windows フォーム クライアントのデータ バインディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 905d010c1ecdab1fc7b2c99e6d720b85ad40be32
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="data-binding-in-a-windows-forms-client"></a><span data-ttu-id="4f384-102">Windows フォーム クライアントのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="4f384-102">Data Binding in a Windows Forms Client</span></span>
<span data-ttu-id="4f384-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスによって返されたデータを Windows フォーム アプリケーションでバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4f384-103">This sample demonstrates how to bind to data returned by a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Windows Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f384-104">このサンプルのセットアップ手順とビルド手順については、この記事の最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f384-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>  
  
 <span data-ttu-id="4f384-105">このサンプルでは、要求/応答通信パターンを定義するコントラクトを実装するサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="4f384-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="4f384-106">このサンプルは、クライアントの Windows フォーム アプリケーション (.exe) と、インターネット インフォメーション サービス (IIS) によってホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で構成されています。</span><span class="sxs-lookup"><span data-stu-id="4f384-106">The sample consists of a client Windows Forms application (.exe) and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="4f384-107">コントラクトは `IWeatherService` インターフェイスによって定義されます。このインターフェイスでは、`GetWeatherData` という名前の操作が公開されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-107">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="4f384-108">この操作は都市名の配列を受け付け、各都市の予想最高気温と最低気温を表す `WeatherData` オブジェクトの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="4f384-108">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="4f384-109">データ バインディングは、Windows フォーム アプリケーションのクライアントで発生します。</span><span class="sxs-lookup"><span data-stu-id="4f384-109">The data binding occurs on the client in the Windows Forms application.</span></span> <span data-ttu-id="4f384-110">`DataGridView` は Windows フォーム デザイナで定義し、データをグラフィック表示します。</span><span class="sxs-lookup"><span data-stu-id="4f384-110">A `DataGridView` is defined in the Windows Forms designer, which is a graphical representation of the data.</span></span> <span data-ttu-id="4f384-111">さらに、`BindingSource` という中継局も作成されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-111">An intermediary named `BindingSource` is also created.</span></span> <span data-ttu-id="4f384-112">`BindingSource` のデータ ソースは、サービスによって返されるデータ配列に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-112">The data source of `BindingSource` is set to the data array returned by the service.</span></span> <span data-ttu-id="4f384-113">`BindingSource` の目的は、データとデータ ビュー間を間接化するレイヤを提供することです。</span><span class="sxs-lookup"><span data-stu-id="4f384-113">The purpose of the `BindingSource` is to provide a layer of indirection between the data and the data view.</span></span> <span data-ttu-id="4f384-114">データとの対話 (移動、並べ替え、フィルタ処理、更新など) はすべて、`BindingSource` コンポーネントを呼び出すことによって実行します。</span><span class="sxs-lookup"><span data-stu-id="4f384-114">All interaction with the data, such as navigating, sorting, filtering, and updating, is accomplished with calls to the `BindingSource` component.</span></span> <span data-ttu-id="4f384-115">`DataGridView` へのデータ バインディングを行うには、`datasource` の `DataGridView` を `BindingSource` オブジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="4f384-115">To accomplish data binding to the `DataGridView`, the `datasource` of the `DataGridView` is then set to the `BindingSource` object.</span></span> <span data-ttu-id="4f384-116">これで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスから返されるすべてのデータがユーザーに対してグラフィック表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-116">All of the data returned from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is then displayed graphically to the user.</span></span>  <span data-ttu-id="4f384-117">ユーザーがボタンをクリックするたびに、返されたデータはデータ バインドされた `DataGridView` で自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-117">Every time the user clicks the button, the returned data is automatically updated in the data-bound `DataGridView`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4f384-118">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="4f384-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4f384-119">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="4f384-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4f384-120">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4f384-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4f384-121">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="4f384-121">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4f384-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="4f384-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4f384-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4f384-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4f384-124">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="4f384-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f384-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4f384-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a><span data-ttu-id="4f384-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f384-126">See Also</span></span>
