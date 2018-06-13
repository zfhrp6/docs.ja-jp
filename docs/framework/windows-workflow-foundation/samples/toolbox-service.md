---
title: ツールボックス サービス
ms.date: 03/30/2017
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
ms.openlocfilehash: 0b3ea56d28d202bd8356fea1783b6675a708631d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516192"
---
# <a name="toolbox-service"></a><span data-ttu-id="31d3a-102">ツールボックス サービス</span><span class="sxs-lookup"><span data-stu-id="31d3a-102">Toolbox Service</span></span>
<span data-ttu-id="31d3a-103">このサンプルでは、ワークフローのコンテキストに基づいて [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ツールボックス アクティビティを更新する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="31d3a-103">This sample demonstrates how to update the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] Toolbox activities based on the context of the workflow.</span></span> <span data-ttu-id="31d3a-104">このサンプルには、カスタム アクティビティが選択されているかどうかに基づいてツールボックスの内容を変更するワークフローが含まれています。</span><span class="sxs-lookup"><span data-stu-id="31d3a-104">The sample contains a workflow that changes the toolbox contents based on whether a custom activity is selected.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="31d3a-105">説明</span><span class="sxs-lookup"><span data-stu-id="31d3a-105">Discussion</span></span>  
 <span data-ttu-id="31d3a-106">ワークフローの作成中には、通常、状況に応じてツールボックスが変化することが求められます。</span><span class="sxs-lookup"><span data-stu-id="31d3a-106">During workflow authoring, customers generally want their Toolbox to be context sensitive.</span></span> <span data-ttu-id="31d3a-107">たとえば、特定のアクティビティをワークフローに追加すると、別のアクティビティがいくつかツールボックスに表示されるようにすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="31d3a-107">For example, the user may want to ensure that the Toolbox shows a few additional activities when a specific activity is added to the workflow.</span></span> <span data-ttu-id="31d3a-108">アクティビティをワークフローから削除したときは、ドメインの要件に基づいてツールボックスが適切に応答する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31d3a-108">If the activities are removed from the workflow, the toolbox should react appropriately based on the domain requirements.</span></span>  
  
 <span data-ttu-id="31d3a-109">ホストを変更したワークフロー デザイナーでは、ツールボックス コントロールを制御し、ワークフローのモデル変更に基づいて、ホストによってツールボックス コントロールで適切な変更がトリガーされるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="31d3a-109">In a re-hosted workflow designer, you control the Toolbox control and can ensure that based on the Model changes in the workflow, the host triggers appropriate changes in the Toolbox control.</span></span> <span data-ttu-id="31d3a-110">ただし、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] では、ツールボックスをユーザーが制御することはないので、その内容を変更するにはインターフェイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="31d3a-110">However, in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], the toolbox is not controlled by the user and thus an interface is required to modify its contents.</span></span> <span data-ttu-id="31d3a-111">`IActivityToolboxService` がそのインターフェイスに当たります。</span><span class="sxs-lookup"><span data-stu-id="31d3a-111">`IActivityToolboxService` is that interface.</span></span>  
  
 <span data-ttu-id="31d3a-112">この API には、次の 4 つのメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="31d3a-112">The API provides the following four methods.</span></span>  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="31d3a-113">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="31d3a-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="31d3a-114">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、WorkflowSimulator.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="31d3a-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WorkflowSimulator.sln solution file.</span></span>  
  
2.  <span data-ttu-id="31d3a-115">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="31d3a-115">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="31d3a-116">Workflow.xaml ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="31d3a-116">Open the Workflow.xaml file.</span></span>  
  
4.  <span data-ttu-id="31d3a-117">追加、 **[customactivity]** にドラッグして、ツールボックスから削除します。</span><span class="sxs-lookup"><span data-stu-id="31d3a-117">Add a **CustomActivity** by dragging and dropping it from the toolbox.</span></span> <span data-ttu-id="31d3a-118">ツールボックス カテゴリの追加と呼ばれることに注意してください: **New WF Category**の他のアクティビティと**割り当てる**です。</span><span class="sxs-lookup"><span data-stu-id="31d3a-118">Notice that an additional Toolbox category called: **New WF Category** with an additional activity **Assign**.</span></span>  
  
5.  <span data-ttu-id="31d3a-119">現在の選択を解除、 **[customactivity]** 別のアクティビティをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="31d3a-119">Now unselect the **CustomActivity** by dragging another activity into it.</span></span>  
  
6.  <span data-ttu-id="31d3a-120">項目**割り当てる**カテゴリで**New WF Category**ツールボックスの下では削除されました。</span><span class="sxs-lookup"><span data-stu-id="31d3a-120">The item **Assign** in the category **New WF Category** under Toolbox is now removed.</span></span> <span data-ttu-id="31d3a-121">また、このカテゴリには項目がほかにないので、カテゴリも削除されます。</span><span class="sxs-lookup"><span data-stu-id="31d3a-121">Also, because there are no more items left in the category, the category is removed as well.</span></span>  
  
7.  <span data-ttu-id="31d3a-122">選択、 **[customactivity]** 再度とカテゴリと**割り当てる**アクティビティが再度追加します。</span><span class="sxs-lookup"><span data-stu-id="31d3a-122">Select the **CustomActivity** again and the category and **Assign** activity is added back.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="31d3a-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="31d3a-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="31d3a-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="31d3a-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="31d3a-125">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="31d3a-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31d3a-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="31d3a-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
