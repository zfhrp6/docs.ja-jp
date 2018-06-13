---
title: 相関電卓
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 77e13b3ca913d2432cfe5d4a95e83764effbb109
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514142"
---
# <a name="correlated-calculator"></a><span data-ttu-id="623cb-102">相関電卓</span><span class="sxs-lookup"><span data-stu-id="623cb-102">Correlated Calculator</span></span>
<span data-ttu-id="623cb-103">このサンプルでは、メッセージ内のパラメーターに基づくコンテンツ ベースの相関関係と共に、デザイナーでメッセージング アクティビティ (<xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply>) を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="623cb-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="623cb-104">このシナリオでは、電卓の操作はパラレルなコンボイで行われます。</span><span class="sxs-lookup"><span data-stu-id="623cb-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="623cb-105">インスタンスおよび (`CalculatorId` に基づく) 相関関係は、最初のメッセージがワークフローに送信されたときに作成され、それ以降の同じ `CalculatorId` を持つメッセージは、リセット操作が呼び出されるまでそのインスタンスにディスパッチされます。</span><span class="sxs-lookup"><span data-stu-id="623cb-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="623cb-106">クライアントは、コード ベースのクライアント プロキシを使用してサービスと通信する WPF アプリケーションとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="623cb-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="623cb-107">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="623cb-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="623cb-108">昇格されたアクセス許可で [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を起動し、For.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="623cb-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="623cb-109">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] が含まれるフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="623cb-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="623cb-110">Devenv.exe を右クリックし **管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="623cb-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="623cb-111">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、CorrelatedCalculator.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="623cb-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="623cb-112">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="623cb-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="623cb-113">サービス プロジェクトを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="623cb-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="623cb-114">サービスの準備ができ、メッセージのリッスンを開始したら、ソリューション エクスプローラーで、Client プロジェクトを右クリックして実行します。</span><span class="sxs-lookup"><span data-stu-id="623cb-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="623cb-115">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="623cb-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="623cb-116">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="623cb-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="623cb-117">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="623cb-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="623cb-118">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="623cb-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`