---
title: "サービス操作エラーの監視"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42506f7f32d0174b4f980f4e94d370cf4c137276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="monitoring-service-operation-failures"></a><span data-ttu-id="5dfa5-102">サービス操作エラーの監視</span><span class="sxs-lookup"><span data-stu-id="5dfa5-102">Monitoring Service Operation Failures</span></span>
<span data-ttu-id="5dfa5-103">アプリケーションに対して分析トレースが有効になっている場合、サービス エラーはイベント ビューアーで簡単に監視できます。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-103">If analytic tracing is enabled for an application, service failures can easily be monitored in the event viewer.</span></span>  <span data-ttu-id="5dfa5-104">ここでは、サービス操作が失敗したことを確認する方法、およびエラーの原因を特定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-104">This topic demonstrates how to determine when a service operation fails, and how to determine what caused the failure.</span></span>  
  
### <a name="determining-service-operation-failure-information"></a><span data-ttu-id="5dfa5-105">サービス操作エラーに関する情報の確認</span><span class="sxs-lookup"><span data-stu-id="5dfa5-105">Determining service operation failure information</span></span>  
  
1.  <span data-ttu-id="5dfa5-106">クリックしてイベント ビューアーを開いて**開始**、**実行**、」と入力して`eventvwr.exe`です。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="5dfa5-107">分析トレースを有効にしていない場合は展開**Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーション サーバー-アプリケーション**.</span><span class="sxs-lookup"><span data-stu-id="5dfa5-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="5dfa5-108">選択**ビュー**、 **分析およびデバッグ ログ**です。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="5dfa5-109">右クリック**分析**選択**ログの有効化**です。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="5dfa5-110">サービス操作が失敗した後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-110">Leave Event Viewer open so that traces can be viewed after the service operation fails.</span></span>  
  
3.  <span data-ttu-id="5dfa5-111">作成したサンプルを次に、開く、[チュートリアル入門](../../../../../docs/framework/wcf/getting-started-tutorial.md)で[!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)]実行する必要があります[!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)]を管理者として、サービスを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-111">Next, open the sample created in the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md) in [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Note that you must run [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] as an administrator so that the service can be created.</span></span> <span data-ttu-id="5dfa5-112">ある場合、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]サンプルのインストール、開くことができます、[作業の開始](../../../../../docs/framework/wcf/samples/getting-started-sample.md)チュートリアルに完成したプロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-112">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="5dfa5-113">Server プロジェクトの Program.cs ファイルで、`Divide` クラスの `CalculatorService` メソッドの先頭に次のコード行を追加します。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-113">In the Program.cs file in the Server project, add the following line of code to the start of the `Divide` method in the `CalculatorService` class:</span></span>  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  <span data-ttu-id="5dfa5-114">クライアント プロジェクトの Program.cs ファイルで、value2 に割り当てる値をゼロに変更します。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-114">In the Program.cs file in the Client project, change the value assigned to value2 to zero:</span></span>  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  <span data-ttu-id="5dfa5-115">キーを押してデバッグを行わない場合、サーバー アプリケーションを実行**ctrl キーを押しながら f5 キーを押して**です。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-115">Execute the server application without debugging by pressing **Ctrl+F5**.</span></span>  
  
7.  <span data-ttu-id="5dfa5-116">Visual Studio コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-116">Open a Visual Studio command prompt.</span></span>  <span data-ttu-id="5dfa5-117">クライアント ディレクトリに移動し、コマンド ラインからクライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-117">Navigate to the client directory and execute the client from the command line.</span></span>  
  
8.  <span data-ttu-id="5dfa5-118">イベント ビューアーで、分析ログを無効化および更新し、イベント ID でイベントを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-118">In Event Viewer, disable and refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="5dfa5-119">イベント ID を持つイベントを探して[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)サービスのエラーを記述します。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-119">Look for an event with Event ID [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), which describes the service failure.</span></span>  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5dfa5-120">イベントは、イベント ビューアーへの送信時にバッファーされます。そのため、エラー イベントはすぐに表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5dfa5-120">Events are buffered when being sent to the event viewer; the failure event may not appear right away.</span></span>
