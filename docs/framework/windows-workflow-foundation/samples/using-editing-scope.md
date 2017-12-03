---
title: "編集スコープの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd0752502bdbd7da9d749ae4f71ea869a4c1ec95
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-editing-scope"></a><span data-ttu-id="001a9-102">編集スコープの使用</span><span class="sxs-lookup"><span data-stu-id="001a9-102">Using Editing Scope</span></span>
<span data-ttu-id="001a9-103">このサンプルでは、変更のセットを 1 つの分割不可能な単位で元に戻せるように、変更のセットをバッチ処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="001a9-103">This sample demonstrates how to batch a set of changes so that they can be undone in a single atomic unit.</span></span> <span data-ttu-id="001a9-104">既定では、アクティビティ デザイナー作者が実行した操作は、"元に戻す/やり直し" システムに自動的に統合されます。</span><span class="sxs-lookup"><span data-stu-id="001a9-104">By default, the actions taken by an activity designer author are automatically integrated into the Undo/Redo system.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="001a9-105">使用例</span><span class="sxs-lookup"><span data-stu-id="001a9-105">Demonstrates</span></span>  
 <span data-ttu-id="001a9-106">編集スコープ、元に戻す、およびやり直し。</span><span class="sxs-lookup"><span data-stu-id="001a9-106">Editing scope and Undo and Redo.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="001a9-107">説明</span><span class="sxs-lookup"><span data-stu-id="001a9-107">Discussion</span></span>  
 <span data-ttu-id="001a9-108">このサンプルでは、1 つの作業単位内で <xref:System.Activities.Presentation.Model.ModelItem> ツリーに対する変更のセットをバッチ処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="001a9-108">This sample demonstrates how to batch a set of changes to the <xref:System.Activities.Presentation.Model.ModelItem> tree within a single unit of work.</span></span> <span data-ttu-id="001a9-109">WPF デザイナーから <xref:System.Activities.Presentation.Model.ModelItem> 値に直接バインドする場合、変更が自動的に適用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="001a9-109">Note that when binding to <xref:System.Activities.Presentation.Model.ModelItem> values directly from a WPF designer, changes are applied automatically.</span></span> <span data-ttu-id="001a9-110">このサンプルでは、1 つの変更ではなく、バッチ処理する複数の変更を命令型コードによって行うときに実行する必要がある操作を示します。</span><span class="sxs-lookup"><span data-stu-id="001a9-110">This sample demonstrates what must be done when multiple changes to be batched are being made through imperative code, rather than a single change.</span></span>  
  
 <span data-ttu-id="001a9-111">このサンプルでは、3 つのアクティビティを追加します。</span><span class="sxs-lookup"><span data-stu-id="001a9-111">In this sample, three activities are added.</span></span> <span data-ttu-id="001a9-112">編集が開始されると、<xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> が <xref:System.Activities.Presentation.Model.ModelItem> のインスタンスで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="001a9-112">When editing begins, <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> is called on an instance of <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="001a9-113">この編集スコープ内で <xref:System.Activities.Presentation.Model.ModelItem> ツリーに対して行った変更を、バッチ処理します。</span><span class="sxs-lookup"><span data-stu-id="001a9-113">Changes made to the <xref:System.Activities.Presentation.Model.ModelItem> tree within this editing scope are batched.</span></span> <span data-ttu-id="001a9-114"><xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> コマンドは、このインスタンスを制御するために使用できる <xref:System.Activities.Presentation.Model.EditingScope> を返します。</span><span class="sxs-lookup"><span data-stu-id="001a9-114">The <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> command returns an <xref:System.Activities.Presentation.Model.EditingScope>, which can be used to control this instance.</span></span> <span data-ttu-id="001a9-115"><xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> または <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> を呼び出して、編集スコープをコミットするか元に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="001a9-115">Either <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> or <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> can be called to either commit or revert the editing scope.</span></span>  
  
 <span data-ttu-id="001a9-116"><xref:System.Activities.Presentation.Model.EditingScope> オブジェクトを入れ子にすることもできます。これにより、変更の複数のセットをより大きな編集スコープの一部として追跡したり、個別に制御したりできます。</span><span class="sxs-lookup"><span data-stu-id="001a9-116">You can also nest <xref:System.Activities.Presentation.Model.EditingScope> objects, which allows for multiple sets of changes to be tracked as part of a larger editing scope and can be controlled individually.</span></span> <span data-ttu-id="001a9-117">この機能を使用する可能性があるシナリオとしては、複数のダイアログからの変更について、すべての変更を 1 つの分割不可能な操作として扱いながら、別々にコミットしたり元に戻したりする必要がある場合が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="001a9-117">A scenario that may use this feature would be when changes from multiple dialogs must be committed or reverted separately, with all changes being treated as a single atomic operation.</span></span> <span data-ttu-id="001a9-118">このサンプルでは、<xref:System.Collections.ObjectModel.ObservableCollection%601> 型の <xref:System.Activities.Presentation.Model.ModelEditingScope> を使用して、編集スコープをスタックします。</span><span class="sxs-lookup"><span data-stu-id="001a9-118">In this sample, the editing scopes are stacked using an <xref:System.Collections.ObjectModel.ObservableCollection%601> of type <xref:System.Activities.Presentation.Model.ModelEditingScope>.</span></span> <span data-ttu-id="001a9-119"><xref:System.Collections.ObjectModel.ObservableCollection%601> を使用すると、デザイナー画面で入れ子の深さを確認できます。</span><span class="sxs-lookup"><span data-stu-id="001a9-119">The <xref:System.Collections.ObjectModel.ObservableCollection%601> is used so that the depth of the nesting can be observed on the designer surface.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="001a9-120">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="001a9-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="001a9-121">サンプルをビルドして実行し、左にあるボタンを使用してワークフローを変更します。</span><span class="sxs-lookup"><span data-stu-id="001a9-121">Build and run the sample, and then use the buttons on the left to modify the workflow.</span></span>  
  
2.  <span data-ttu-id="001a9-122">をクリックして**のスコープの編集を開く**です。</span><span class="sxs-lookup"><span data-stu-id="001a9-122">Click **Open Editing Scope**.</span></span>  
  
    1.  <span data-ttu-id="001a9-123">このコマンドにより、編集スコープを作成して編集スタックにプッシュする <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="001a9-123">This command calls <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> that creates an editing scope and pushes it onto the editing stack.</span></span>  
  
    2.  <span data-ttu-id="001a9-124">次に、選択した <xref:System.Activities.Presentation.Model.ModelItem> に 3 つのアクティビティを追加します。</span><span class="sxs-lookup"><span data-stu-id="001a9-124">Three activities are then added to the selected <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="001a9-125">編集スコープを <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> によって開かなかった場合は、3 つの新しいアクティビティがデザイナー キャンバスに表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="001a9-125">Note that if the editing scope had not been opened with <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, three new activities would appear on the designer canvas.</span></span> <span data-ttu-id="001a9-126">この操作は <xref:System.Activities.Presentation.Model.EditingScope> 内で保留中のままであるので、デザイナーはまだ更新されません。</span><span class="sxs-lookup"><span data-stu-id="001a9-126">Because this operation is still pending within the <xref:System.Activities.Presentation.Model.EditingScope>, the designer is not yet updated.</span></span>  
  
3.  <span data-ttu-id="001a9-127">キーを押して**Close Editing Scope**編集スコープをコミットします。</span><span class="sxs-lookup"><span data-stu-id="001a9-127">Press **Close Editing Scope** to commit the editing scope.</span></span> <span data-ttu-id="001a9-128">3 つのアクティビティがデザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="001a9-128">Three activities appear in the designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="001a9-129">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="001a9-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="001a9-130">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="001a9-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="001a9-131">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="001a9-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="001a9-132">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="001a9-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
