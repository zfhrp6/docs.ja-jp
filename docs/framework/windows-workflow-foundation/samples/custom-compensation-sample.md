---
title: カスタム補正のサンプル
ms.date: 03/30/2017
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
ms.openlocfilehash: 55161a46bebca2cce41803ca405cb2b1df57b3fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514325"
---
# <a name="custom-compensation-sample"></a><span data-ttu-id="12cbc-102">カスタム補正のサンプル</span><span class="sxs-lookup"><span data-stu-id="12cbc-102">Custom Compensation Sample</span></span>
<span data-ttu-id="12cbc-103">このサンプルでは、<xref:System.Activities.Statements.CompensableActivity> とその補正ハンドラーを使用してカスタム補正ロジックを定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="12cbc-103">This sample shows how to use <xref:System.Activities.Statements.CompensableActivity> and its compensation handler to define custom compensation logic.</span></span> <span data-ttu-id="12cbc-104">このサンプルでは、トラック レンタル会社のシナリオをモデル化しています。</span><span class="sxs-lookup"><span data-stu-id="12cbc-104">The scenario modeled in this sample is a Truck Rental Agency.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="12cbc-105">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="12cbc-105">Sample Details</span></span>  
 <span data-ttu-id="12cbc-106">シミュレートする手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="12cbc-106">The steps simulated are:</span></span>  
  
1.  <span data-ttu-id="12cbc-107">ユーザーが日付を指定してトラック レンタルの見積もりを要求します。</span><span class="sxs-lookup"><span data-stu-id="12cbc-107">The user requests truck rental quotes for a given date.</span></span>  
  
2.  <span data-ttu-id="12cbc-108">トラック会社 3 社に連絡して、3 つの見積もりを入手します。</span><span class="sxs-lookup"><span data-stu-id="12cbc-108">Three truck companies are contacted and the three quotes are provided.</span></span>  
  
3.  <span data-ttu-id="12cbc-109">ユーザーがトラックの見積もりを 1 つ選択し、クレジット カードでの注文に進みます。</span><span class="sxs-lookup"><span data-stu-id="12cbc-109">The user selects one truck quote and proceeds to order by credit card.</span></span>  
  
4.  <span data-ttu-id="12cbc-110">アプリケーションで、他の 2 つのトラックの見積もりが取り消されます。</span><span class="sxs-lookup"><span data-stu-id="12cbc-110">The application cancels the other two truck quotes.</span></span>  
  
5.  <span data-ttu-id="12cbc-111">利用予定日の 10 日前を過ぎてからの取り消しの場合にプレミアム アカウント以外には払い戻しされないサービス手数料が、アプリケーションで請求されます。</span><span class="sxs-lookup"><span data-stu-id="12cbc-111">The application charges a service fee that is non-refundable for non-premium accounts if cancelation happens 10 days or less prior to the reservation date.</span></span>  
  
6.  <span data-ttu-id="12cbc-112">アプリケーションで、トラックのレンタル料金が請求されます。</span><span class="sxs-lookup"><span data-stu-id="12cbc-112">The application charges the truck rental fee.</span></span>  
  
7.  <span data-ttu-id="12cbc-113">アプリケーションは、利用予定日になるか顧客が予約を取り消すか、どちらか早い方まで待機します。</span><span class="sxs-lookup"><span data-stu-id="12cbc-113">The application waits until the reservation date or until the customer decided to cancel the reservation, whichever comes first.</span></span>  
  
8.  <span data-ttu-id="12cbc-114">顧客が予約を取り消した場合、次のロジックに従って <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> カスタム補正ロジックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="12cbc-114">If the customer cancels the reservation, the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> custom compensation logic runs according to the following logic:</span></span>  
  
    1.  <span data-ttu-id="12cbc-115">顧客がプレミアム アカウントでなく、かつ利用予定日の 10 日前を過ぎている場合、サービス手数料が請求されます。それ以外の場合は、サービス手数料が返金されます。</span><span class="sxs-lookup"><span data-stu-id="12cbc-115">If the customer has a non-premium account and it is less than 10 days prior to the reservation date, then the service fee is still charged; otherwise, the application refunds the service fee.</span></span>  
  
    2.  <span data-ttu-id="12cbc-116">残りの補正可能なアクティビティ (トラックの注文 + トラックの注文料金) については、既定の補正ロジックに従って、逆の順序で補正が実行されます。</span><span class="sxs-lookup"><span data-stu-id="12cbc-116">The rest of the compensable activities (truck order + truck order fee) are run according to the default compensation logic, which is to compensate in reverse order of execution.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="12cbc-117">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="12cbc-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="12cbc-118">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、CustomCompensation.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="12cbc-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomCompensation.sln solution.</span></span> <span data-ttu-id="12cbc-119">このソリューションは \WF\Basic\Compensation\CustomCompensation ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="12cbc-119">It is located in the \WF\Basic\Compensation\CustomCompensation directory.</span></span>  
  
2.  <span data-ttu-id="12cbc-120">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="12cbc-120">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="12cbc-121">Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="12cbc-121">Press CTRL + F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="12cbc-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="12cbc-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="12cbc-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="12cbc-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="12cbc-124">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="12cbc-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="12cbc-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="12cbc-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`