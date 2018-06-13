---
title: 非同期通信
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 9eafeab89aefb181ae016dc0219f9155d9bd2a25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515161"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="2f99f-102">非同期通信</span><span class="sxs-lookup"><span data-stu-id="2f99f-102">Asynchronous Communication</span></span>
<span data-ttu-id="2f99f-103">このサンプルでは、既定の 2 つの異なる Windows Workflow Foundation (WF) サービスの間の通信の非同期的の実行方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2f99f-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2f99f-104">使用例</span><span class="sxs-lookup"><span data-stu-id="2f99f-104">Demonstrates</span></span>  
 <span data-ttu-id="2f99f-105">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] サービス間の非同期通信</span><span class="sxs-lookup"><span data-stu-id="2f99f-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="2f99f-106">説明</span><span class="sxs-lookup"><span data-stu-id="2f99f-106">Discussion</span></span>  
 <span data-ttu-id="2f99f-107">このサンプルでは、.NET Framework が提供するメッセージング アクティビティを使用して、[!INCLUDE[wf1](../../../../includes/wf1-md.md)] アプリケーション間の非同期通信がどのように行われるのかを示します。</span><span class="sxs-lookup"><span data-stu-id="2f99f-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="2f99f-108">このサンプルは、次の 3 つのプロジェクトで構成されています。</span><span class="sxs-lookup"><span data-stu-id="2f99f-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="2f99f-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="2f99f-109">CreditCheckService</span></span>  
 <span data-ttu-id="2f99f-110">このサービスは、特定の個人のクレジット スコアまたは取得する項目の値を受け取り、その個人にクレジットを与えるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="2f99f-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="2f99f-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="2f99f-111">RentalApprovalService</span></span>  
 <span data-ttu-id="2f99f-112">このサービスは、特定のクレジットを必要としている個人から申請を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2f99f-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="2f99f-113">このサービスは `CreditCheckService` と非同期で通信して、クレジットの申請が有効かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="2f99f-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="2f99f-114">Client</span><span class="sxs-lookup"><span data-stu-id="2f99f-114">Client</span></span>  
 <span data-ttu-id="2f99f-115">クライアントは `RentalApprovalService` と同期通信を行い、クレジットが承認されているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="2f99f-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2f99f-116">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="2f99f-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2f99f-117">右クリックし、 **AsynchronousCommunication**ソリューションと選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="2f99f-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="2f99f-118">**共通プロパティ****スタートアップ プロジェクト**を選択し、**マルチ スタートアップ プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="2f99f-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="2f99f-119">移動**RentalApprovalService**一覧の最初の位置に続く**CreditCheckService**で始まり、**クライアント**です。</span><span class="sxs-lookup"><span data-stu-id="2f99f-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="2f99f-120">設定、**開始**3 つすべてのプロジェクトのアクション。</span><span class="sxs-lookup"><span data-stu-id="2f99f-120">Set the **Start** action on all three projects.</span></span>  
  
4.  <span data-ttu-id="2f99f-121">をクリックして**OK**、f5 キーを押して、サンプルを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="2f99f-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2f99f-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="2f99f-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2f99f-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2f99f-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2f99f-124">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="2f99f-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2f99f-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2f99f-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
