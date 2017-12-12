---
title: "既存のサービス コントラクトを使用するワークフロー サービスを作成する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb58664b57261eb09886ec0e8f97fcdbe45cdd4f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="0a13d-102">既存のサービス コントラクトを使用するワークフロー サービスを作成する方法</span><span class="sxs-lookup"><span data-stu-id="0a13d-102">How to: Create a workflow service that consumes an existing service contract</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="0a13d-103"> では、コントラクト優先ワークフローの開発という形で、Web サービスとワークフローの統合が向上しています。</span><span class="sxs-lookup"><span data-stu-id="0a13d-103"> features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="0a13d-104">コントラクト優先ワークフローの開発ツールでは、コードのコントラクトを先に設計できます。</span><span class="sxs-lookup"><span data-stu-id="0a13d-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="0a13d-105">その後、ツールボックス内に、コントラクト内の操作用のアクティビティ テンプレートが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="0a13d-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a13d-106">このトピックでは、コントラクト優先ワークフロー サービスを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a13d-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="0a13d-107">コントラクト優先ワークフロー サービス開発を参照してください[コントラクト最初のワークフロー サービス開発](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md)です。</span><span class="sxs-lookup"><span data-stu-id="0a13d-107"> contract-first workflow service development, see [Contract First Workflow Service Development](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="0a13d-108">ワークフロー プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="0a13d-108">Creating the workflow project</span></span>  
  
1.  <span data-ttu-id="0a13d-109">[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] で、**[ファイル]**、**[新しいプロジェクト]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="0a13d-109">In [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], select **File**, **New Project**.</span></span> <span data-ttu-id="0a13d-110">選択、 **WCF**ノードの下、 **c#**内のノード、**テンプレート**ツリー、および選択、 **WCF ワークフロー サービス アプリケーション**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="0a13d-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2.  <span data-ttu-id="0a13d-111">新しいプロジェクトの名前`ContractFirst` をクリック**Ok**です。</span><span class="sxs-lookup"><span data-stu-id="0a13d-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="0a13d-112">サービス コントラクトの作成</span><span class="sxs-lookup"><span data-stu-id="0a13d-112">Creating the service contract</span></span>  
  
1.  <span data-ttu-id="0a13d-113">プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の追加...**.</span><span class="sxs-lookup"><span data-stu-id="0a13d-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="0a13d-114">選択、**コード**、左側のノードと**クラス**右側のテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="0a13d-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="0a13d-115">新しいクラスの名前を`IBookService` をクリック**Ok**です。</span><span class="sxs-lookup"><span data-stu-id="0a13d-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="0a13d-116">表示されるコード ウィンドウの上部で、`System.Servicemodel` に対する Using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="0a13d-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  <span data-ttu-id="0a13d-117">サンプルのクラス定義を次のインターフェイス定義に変更します。</span><span class="sxs-lookup"><span data-stu-id="0a13d-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  <span data-ttu-id="0a13d-118">キーを押してプロジェクトをビルド**Ctrl + Shift + B**です。</span><span class="sxs-lookup"><span data-stu-id="0a13d-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="0a13d-119">サービス コントラクトのインポート</span><span class="sxs-lookup"><span data-stu-id="0a13d-119">Importing the service contract</span></span>  
  
1.  <span data-ttu-id="0a13d-120">プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**サービス コントラクトのインポート**です。</span><span class="sxs-lookup"><span data-stu-id="0a13d-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="0a13d-121">**\<現在のプロジェクト >**すべてのサブノードを開き、選択**IBookService**です。</span><span class="sxs-lookup"><span data-stu-id="0a13d-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="0a13d-122">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a13d-122">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="0a13d-123">ダイアログが表示され、操作が正常に完了したことと、プロジェクトをビルドすると、生成されたアクティビティがツールボックスに表示されることが示されます。</span><span class="sxs-lookup"><span data-stu-id="0a13d-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="0a13d-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a13d-124">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="0a13d-125">キーを押してプロジェクトをビルド**Ctrl + Shift + B**インポートしたアクティビティがツールボックスに表示されるように、します。</span><span class="sxs-lookup"><span data-stu-id="0a13d-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4.  <span data-ttu-id="0a13d-126">**ソリューション エクスプ ローラー**Service1.xamlx を開きます。</span><span class="sxs-lookup"><span data-stu-id="0a13d-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="0a13d-127">ワークフロー サービスがデザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a13d-127">The workflow service will appear in the designer.</span></span>  
  
5.  <span data-ttu-id="0a13d-128">選択、**シーケンス**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="0a13d-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="0a13d-129">[プロパティ] ウィンドウ、**しています.**</span><span class="sxs-lookup"><span data-stu-id="0a13d-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="0a13d-130">ボタンをクリックして、 **ImplementedContract**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0a13d-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="0a13d-131">**型コレクション エディター**ウィンドウが表示されたら、をクリックして、**型**ドロップダウン リストを選択し、**型を参照しています.**</span><span class="sxs-lookup"><span data-stu-id="0a13d-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="0a13d-132">エントリです。</span><span class="sxs-lookup"><span data-stu-id="0a13d-132">entry.</span></span> <span data-ttu-id="0a13d-133">**型の参照と選択 .Net**ダイアログで、 **\<現在のプロジェクト >**すべてのサブノードを開き、選択**IBookService**です。</span><span class="sxs-lookup"><span data-stu-id="0a13d-133">In the **Browse and Select a .Net Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="0a13d-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a13d-134">Click **OK**.</span></span> <span data-ttu-id="0a13d-135">**型コレクション エディター**ダイアログ ボックスで、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="0a13d-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6.  <span data-ttu-id="0a13d-136">選択し、削除、 **ReceiveRequest**と**SendResponse**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="0a13d-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7.  <span data-ttu-id="0a13d-137">ツールボックスからドラッグして、 **Buy_ReceiveAndSendReply**と**Checkout_Receive**上にアクティビティ、**シーケンシャル サービス**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="0a13d-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
