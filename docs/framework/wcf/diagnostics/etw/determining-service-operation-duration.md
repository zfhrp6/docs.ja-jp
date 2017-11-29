---
title: "サービス操作の実行時間の確認"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63a8c92713ee452da2439475ac526229d1e5741c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="30489-102">サービス操作の実行時間の確認</span><span class="sxs-lookup"><span data-stu-id="30489-102">Determining service operation duration</span></span>
<span data-ttu-id="30489-103">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションで分析トレースを有効にしている場合、イベント ログを調べるだけでサービス操作の実行時間を簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="30489-103">If analytic tracing is enabled in a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="30489-104">ここでは、サービス操作の実行にかかる時間を確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="30489-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="30489-105">サービス操作の実行時間の確認</span><span class="sxs-lookup"><span data-stu-id="30489-105">Determining service operation execution duration</span></span>  
  
1.  <span data-ttu-id="30489-106">クリックしてイベント ビューアーを開いて**開始**、**実行**、」と入力して`eventvwr.exe`です。</span><span class="sxs-lookup"><span data-stu-id="30489-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="30489-107">分析トレースを有効にしていない場合は展開**Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーション サーバー-アプリケーション**.</span><span class="sxs-lookup"><span data-stu-id="30489-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="30489-108">選択**ビュー**、 **分析およびデバッグ ログ**です。</span><span class="sxs-lookup"><span data-stu-id="30489-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="30489-109">右クリック**分析**選択**ログの有効化**です。</span><span class="sxs-lookup"><span data-stu-id="30489-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="30489-110">サービス操作が実行された後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="30489-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3.  <span data-ttu-id="30489-111">次に、サービス プロジェクトおよびそのサービスと対話するクライアント プロジェクトが含まれている [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="30489-111">Next, open a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="30489-112">このようなアプリケーションを作成するには、次の[チュートリアル入門](../../../../../docs/framework/wcf/getting-started-tutorial.md)です。</span><span class="sxs-lookup"><span data-stu-id="30489-112">You can create such an application by following the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  <span data-ttu-id="30489-113">ある場合、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]サンプルのインストール、開くことができます、[作業の開始](../../../../../docs/framework/wcf/samples/getting-started-sample.md)チュートリアルに完成したプロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="30489-113">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="30489-114">キーを押してサーバー アプリケーションを実行**f5 キーを押して**です。</span><span class="sxs-lookup"><span data-stu-id="30489-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="30489-115">右クリックして、クライアント アプリケーションを実行、**クライアント**プロジェクトを選択して**デバッグ**、**新しいインスタンスを開始**です。</span><span class="sxs-lookup"><span data-stu-id="30489-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5.  <span data-ttu-id="30489-116">イベント ビューアーで、分析ログを更新し、イベント ID でイベントを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="30489-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="30489-117">イベント ID を持つイベントを探します[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)です。</span><span class="sxs-lookup"><span data-stu-id="30489-117">Look for events with Event ID [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span></span>  <span data-ttu-id="30489-118">これらのイベントは、完了した操作、およびその操作にかかった時間を示します。</span><span class="sxs-lookup"><span data-stu-id="30489-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="30489-119">次のイベントは、追加操作の時間を示しています。</span><span class="sxs-lookup"><span data-stu-id="30489-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
