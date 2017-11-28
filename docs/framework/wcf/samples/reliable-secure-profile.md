---
title: Reliable Secure Profile
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 6b73565409e26456ad09067066455ef2459b2e3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-secure-profile"></a><span data-ttu-id="70ac3-102">Reliable Secure Profile</span><span class="sxs-lookup"><span data-stu-id="70ac3-102">Reliable Secure Profile</span></span>
<span data-ttu-id="70ac3-103">このサンプルを作成する方法を示します[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]と[Reliable Secure Profile](http://go.microsoft.com/fwlink/?LinkId=178140) (RSP)。</span><span class="sxs-lookup"><span data-stu-id="70ac3-103">This sample demonstrates how to compose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and [Reliable Secure Profile](http://go.microsoft.com/fwlink/?LinkId=178140) (RSP).</span></span> <span data-ttu-id="70ac3-104">このサンプルの実装、 [Make Connection](http://go.microsoft.com/fwlink/?LinkId=178141) RSP 仕様に基づいて信頼性の高いセキュリティで保護されたバインディングを作成するセキュリティで保護されたチャネルをチャネルと共に、信頼できるメッセージング、および必要に応じて構成できます。</span><span class="sxs-lookup"><span data-stu-id="70ac3-104">This sample demonstrates the implementation of a [Make Connection](http://go.microsoft.com/fwlink/?LinkId=178141) channel which can be composed together with Reliable Messaging and optionally a secure channel to create a Reliable Secure Binding based on the RSP specification.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="70ac3-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="70ac3-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="70ac3-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="70ac3-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="70ac3-107">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="70ac3-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="70ac3-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="70ac3-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a><span data-ttu-id="70ac3-109">説明</span><span class="sxs-lookup"><span data-stu-id="70ac3-109">Discussion</span></span>  
 <span data-ttu-id="70ac3-110">このサンプルでは、信頼できる非同期の双方向メッセージ交換シナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="70ac3-110">This sample demonstrates a reliable asynchronous two-way message exchange scenario.</span></span> <span data-ttu-id="70ac3-111">サービスには双方向コントラクトがあり、クライアントには双方向コールバック コントラクトが実装されます。</span><span class="sxs-lookup"><span data-stu-id="70ac3-111">The service has a duplex contract and the client implements the duplex callback contract.</span></span> <span data-ttu-id="70ac3-112">クライアントからサービスに対して要求が開始され、要求に対しては個別の接続で応答する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70ac3-112">The client initiates a request to a service, for which a response is expected on a separate connection.</span></span> <span data-ttu-id="70ac3-113">要求メッセージは信頼できる方法で送信されます。</span><span class="sxs-lookup"><span data-stu-id="70ac3-113">The request message is sent reliably.</span></span> <span data-ttu-id="70ac3-114">クライアントでは、終端にある待機エンドポイントを開きません。</span><span class="sxs-lookup"><span data-stu-id="70ac3-114">The client does not want to open a listening endpoint at its end.</span></span> <span data-ttu-id="70ac3-115">したがって、クライアントは "Make Connection" 要求を使用してサービスをポーリングし、サービスはこの "Make Connection" 要求のバック チャネルで応答を返信します。</span><span class="sxs-lookup"><span data-stu-id="70ac3-115">Thus, it polls the service with ‘Make Connection’ requests for the service to send back the response on the back channel of this ‘Make Connection’ request.</span></span> <span data-ttu-id="70ac3-116">このサンプルでは、クライアントで待機エンドポイントを公開せずに (また、ファイアウォールの例外を設けずに)、HTTP を介してセキュリティで保護された信頼できる双方向通信を実現する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="70ac3-116">This sample demonstrates how to have secure reliable duplex communication over HTTP without the client exposing a listening endpoint (and creating a firewall exception).</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="70ac3-117">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="70ac3-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="70ac3-118">開く、 **ReliableSecureProfile**ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="70ac3-118">Open the **ReliableSecureProfile** solution.</span></span>  
  
2.  <span data-ttu-id="70ac3-119">右クリックして、**サービス**でプロジェクトを**ソリューション エクスプ ローラー****デバッグ**、**新しいインスタンスを開始**コンテキスト メニューからです。</span><span class="sxs-lookup"><span data-stu-id="70ac3-119">Right click the **Service** project in **Solution Explorer**, select **Debug**, **Start new instance** from the context menu.</span></span> <span data-ttu-id="70ac3-120">サービス ホストが開始されます。</span><span class="sxs-lookup"><span data-stu-id="70ac3-120">This starts up the service host.</span></span>  
  
3.  <span data-ttu-id="70ac3-121">右クリックして、**クライアント**でプロジェクトを**ソリューション エクスプ ローラー****デバッグ**、**新しいインスタンスを開始**コンテキスト メニューからです。</span><span class="sxs-lookup"><span data-stu-id="70ac3-121">Right click the **Client** project in **Solution Explorer**, select **Debug**, **Start new instance** from the context menu.</span></span> <span data-ttu-id="70ac3-122">クライアントが開始されます。</span><span class="sxs-lookup"><span data-stu-id="70ac3-122">This starts up the client.</span></span>  
  
4.  <span data-ttu-id="70ac3-123">クライアント コンソール ウィンドウのプロンプトに任意の文字列を入力し、Enter キーを押します。入力文字列がサービスに送信され、この文字列のハッシュが計算されます。</span><span class="sxs-lookup"><span data-stu-id="70ac3-123">Type in any string in the prompt on the client console window and click ENTER.This sends the input string to the service, which computes a hash of this string.</span></span>  
  
5.  <span data-ttu-id="70ac3-124">クライアント コンソール ウィンドウに結果を表示するためにサービスから双方向コールバック コントラクト操作がコールバックされたら、クライアント ウィンドウで結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="70ac3-124">View the result on the client windows when the service calls back the duplex callback contract operation to display the result on the client console window.</span></span> <span data-ttu-id="70ac3-125">実行に時間のかかるデータ処理操作を再現するために、サービスからの応答は意図的に遅延されます。</span><span class="sxs-lookup"><span data-stu-id="70ac3-125">There is an intentional delay on the service to simulate a long running operation of processing the data.</span></span>  
  
6.  <span data-ttu-id="70ac3-126">HTTP トラフィックの監視 (ネットワーク モニター、Fiddler などのオンライン ネットワーク監視ツールを使用) により、Reliable Secure Profile で規定されているように通信のシーケンスがクライアントとサービスの間で確立されていること、およびどのようにクライアントが "Make Connection" 要求を使用してサービスをポーリングしているかが示されます。</span><span class="sxs-lookup"><span data-stu-id="70ac3-126">Monitoring the HTTP traffic (by any of the online network monitoring tools like Network Monitor, Fiddler and so on) shows that a sequence for communication is established between the client and the service as laid down by the Reliable Secure Profile, and how the client polls the service with ‘Make Connection’ requests.</span></span> <span data-ttu-id="70ac3-127">サービスでは、処理した応答を返信できる状態になると、最後の "Make Connection" 要求のバック チャネルを使用して、結果を返信します。</span><span class="sxs-lookup"><span data-stu-id="70ac3-127">When the service gets ready to send back the processed response, it uses the back channel of the last ‘Make Connection’ request to send back the results.</span></span>  
  
7.  <span data-ttu-id="70ac3-128">サービス コンソール ウィンドウで Enter キーを押してサービスを終了します。</span><span class="sxs-lookup"><span data-stu-id="70ac3-128">Press ENTER on the service console window to close the service.</span></span> <span data-ttu-id="70ac3-129">クライアント コンソール ウィンドウで Enter キーを押してクライアントを終了します。</span><span class="sxs-lookup"><span data-stu-id="70ac3-129">Press ENTER on the client console window to close the client.</span></span>
