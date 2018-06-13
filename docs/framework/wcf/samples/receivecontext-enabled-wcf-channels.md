---
title: ReceiveContext が有効な WCF チャネル
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: 3e5ac914ae4d0c97ed617ea4a8d5a893ec740179
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502935"
---
# <a name="receivecontext-enabled-wcf-channels"></a><span data-ttu-id="f6677-102">ReceiveContext が有効な WCF チャネル</span><span class="sxs-lookup"><span data-stu-id="f6677-102">ReceiveContext-Enabled WCF Channels</span></span>
<span data-ttu-id="f6677-103">このサンプルでは、<xref:System.ServiceModel.Channels.ReceiveContext> を有効にした WCF チャネルの有用性を示します。</span><span class="sxs-lookup"><span data-stu-id="f6677-103">This sample demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span> <span data-ttu-id="f6677-104">このサンプルでは、NetMSMQ チャネルを使用して 2 つの数値の積を見つけるサービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="f6677-104">The sample implements a service to find the product of two numbers using a NetMSMQ channel.</span></span>  
  
 <span data-ttu-id="f6677-105"><xref:System.ServiceModel.Channels.ReceiveContext> クラスを使用すると、メッセージの内容を検査した後でも、メッセージにアクセスするか、メッセージをキューに残してさらに処理するかをアプリケーションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="f6677-105">The <xref:System.ServiceModel.Channels.ReceiveContext> class enables an application to decide whether to access the message or leave it in the queue for further processing, even after the contents of the message have been inspected.</span></span> <span data-ttu-id="f6677-106">このサンプルでは、クライアントがランダムな整数をトランザクション キューに送信します。</span><span class="sxs-lookup"><span data-stu-id="f6677-106">In this sample, a client sends random integers to a transactional queue.</span></span> <span data-ttu-id="f6677-107">`ProductCalculator` サービスはメッセージを受信し、そのメッセージの内容 (整数) を検索して、積が計算できるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f6677-107">The `ProductCalculator` service receives the messages and inspects the message contents, which are integers, to determine whether the product can be computed.</span></span> <span data-ttu-id="f6677-108">サービス操作で積が計算されない場合、メッセージはキューに戻されます。このメッセージはキューをリッスンするサービスでもう一度受信できます。</span><span class="sxs-lookup"><span data-stu-id="f6677-108">If the service operation does not compute the product, the message is put back into the queue and can be received again by the service listening on the queue.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f6677-109">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f6677-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f6677-110">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f6677-110">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f6677-111">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="f6677-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6677-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f6677-112">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f6677-113">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="f6677-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="f6677-114">Microsoft Message Queuing (MSMQ) がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f6677-114">Ensure that Microsoft Message Queuing (MSMQ) is installed.</span></span>  
  
    1.  <span data-ttu-id="f6677-115">MSMQ を [!INCLUDE[lserver](../../../../includes/lserver-md.md)] にインストールするには</span><span class="sxs-lookup"><span data-stu-id="f6677-115">To install MSMQ on [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="f6677-116">**サーバー マネージャー**をクリックして**機能**します。</span><span class="sxs-lookup"><span data-stu-id="f6677-116">In **Server Manager**, click **Features**.</span></span>  
  
        2.  <span data-ttu-id="f6677-117">右側のペインで**機能の概要**をクリックして**機能の追加**です。</span><span class="sxs-lookup"><span data-stu-id="f6677-117">In the right pane under **Features Summary**, click **Add Features**.</span></span>  
  
        3.  <span data-ttu-id="f6677-118">結果ウィンドウで、展開**メッセージ キュー**です。</span><span class="sxs-lookup"><span data-stu-id="f6677-118">In the resulting window, expand **Message Queuing**.</span></span>  
  
        4.  <span data-ttu-id="f6677-119">展開**メッセージ キュー サービス**です。</span><span class="sxs-lookup"><span data-stu-id="f6677-119">Expand **Message Queuing Services**.</span></span>  
  
        5.  <span data-ttu-id="f6677-120">をクリックして**ディレクトリ サービス統合**(コンピューターの場合、ドメインに参加している)、をクリックして**HTTP サポート**です。</span><span class="sxs-lookup"><span data-stu-id="f6677-120">Click **Directory Services Integration** (for computers joined to a domain), and then click **HTTP Support**.</span></span>  
  
        6.  <span data-ttu-id="f6677-121">をクリックして **[次へ]**、クリックして**インストール**です。</span><span class="sxs-lookup"><span data-stu-id="f6677-121">Click **Next**, and then click **Install**.</span></span>  
  
    2.  <span data-ttu-id="f6677-122">MSMQ を [!INCLUDE[wv](../../../../includes/wv-md.md)] にインストールするには</span><span class="sxs-lookup"><span data-stu-id="f6677-122">To install MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="f6677-123">**[コントロール パネル]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="f6677-123">Open **Control Panel**.</span></span>  
  
        2.  <span data-ttu-id="f6677-124">をクリックして**プログラム**し、**プログラムと機能**をクリックして**Windows の機能のオンとオフを**です。</span><span class="sxs-lookup"><span data-stu-id="f6677-124">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
        3.  <span data-ttu-id="f6677-125">展開**Microsoft メッセージ キュー (MSMQ) Server**、展開**Microsoft メッセージ キュー (MSMQ) Server Core**、次のメッセージ キュー機能をインストールする チェック ボックスを選択。</span><span class="sxs-lookup"><span data-stu-id="f6677-125">Expand **Microsoft Message Queue (MSMQ) Server**, expand **Microsoft Message Queue (MSMQ) Server Core**, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
            -   <span data-ttu-id="f6677-126">[メッセージ キュー サーバー]</span><span class="sxs-lookup"><span data-stu-id="f6677-126">Message Queuing Server</span></span>  
  
            -   <span data-ttu-id="f6677-127">[MSMQ Active Directory Domain Services Integration] (ドメインに参加するコンピューターの場合)</span><span class="sxs-lookup"><span data-stu-id="f6677-127">MSMQ Active Directory Domain Services Integration (for computers joined to a domain)</span></span>  
  
            -   <span data-ttu-id="f6677-128">[MSMQ HTTP サポート]</span><span class="sxs-lookup"><span data-stu-id="f6677-128">MSMQ HTTP Support</span></span>  
  
        4.  <span data-ttu-id="f6677-129">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6677-129">Click **OK**.</span></span>  
  
        5.  <span data-ttu-id="f6677-130">コンピューターを再起動するメッセージが表示されたら、クリックして**OK**インストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="f6677-130">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
2.  <span data-ttu-id="f6677-131">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] がコンピューターにインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f6677-131">Ensure that [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is installed on the computer.</span></span>  
  
3.  <span data-ttu-id="f6677-132">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、ReceiveContextProductGenerator.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f6677-132">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ReceiveContextProductGenerator.sln solution file.</span></span>  
  
4.  <span data-ttu-id="f6677-133">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f6677-133">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="f6677-134">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f6677-134">To run the solution, press CTRL+F5.</span></span>
