---
title: "チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b60d4ee7908a5ed9dcb3393132ba7d0bd0a6cb5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="8582c-102">チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定</span><span class="sxs-lookup"><span data-stu-id="8582c-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="8582c-103">現在開いているソリューション内のプロジェクトで定義された、コンポーネント場合、自動的に表示されます、**ツールボックス**操作は必要とします。</span><span class="sxs-lookup"><span data-stu-id="8582c-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="8582c-104">手動で設定することができます、**ツールボックス**を使用して、カスタム コンポーネントで、[選択ツールボックス項目 ダイアログ ボックス (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)、ですが、**ツールボックス**考慮ソリューションの内の項目は、ビルドの次のすべての特性を持つ出力を。</span><span class="sxs-lookup"><span data-stu-id="8582c-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="8582c-105">実装して<xref:System.ComponentModel.IComponent>です。</span><span class="sxs-lookup"><span data-stu-id="8582c-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="8582c-106">いない<xref:System.ComponentModel.ToolboxItemAttribute>'éý'`false`です。</span><span class="sxs-lookup"><span data-stu-id="8582c-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="8582c-107">いない<xref:System.ComponentModel.DesignTimeVisibleAttribute>'éý'`false`です。</span><span class="sxs-lookup"><span data-stu-id="8582c-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8582c-108">**ツールボックス**に従わなかった場合、参照チェーンのため、ソリューションのプロジェクトで構築されていないアイテムは表示されません。</span><span class="sxs-lookup"><span data-stu-id="8582c-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="8582c-109">このチュートリアルでは、カスタム コンポーネントに自動的にでの表示方法、**ツールボックス**コンポーネントをビルドします。</span><span class="sxs-lookup"><span data-stu-id="8582c-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="8582c-110">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="8582c-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="8582c-111">Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8582c-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="8582c-112">カスタム コンポーネントを作成します。</span><span class="sxs-lookup"><span data-stu-id="8582c-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="8582c-113">カスタム コンポーネントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8582c-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="8582c-114">アンロードし、カスタム コンポーネントを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="8582c-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="8582c-115">完了したら、\outputfromtestproviderdebugmode.txt、**ツールボックス**作成したコンポーネントが格納されます。</span><span class="sxs-lookup"><span data-stu-id="8582c-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8582c-116">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8582c-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8582c-117">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8582c-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8582c-118">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8582c-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="8582c-119">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="8582c-119">Creating the Project</span></span>  
 <span data-ttu-id="8582c-120">まず、プロジェクトを作成し、フォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="8582c-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="8582c-121">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="8582c-121">To create the project</span></span>  
  
1.  <span data-ttu-id="8582c-122">`ToolboxExample` という Windows ベースのアプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8582c-122">Create a Windows-based application project called `ToolboxExample`.</span></span>  
  
     <span data-ttu-id="8582c-123">詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8582c-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="8582c-124">新しいコンポーネントをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="8582c-124">Add a new component to the project.</span></span> <span data-ttu-id="8582c-125">それを呼び出す`DemoComponent`です。</span><span class="sxs-lookup"><span data-stu-id="8582c-125">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="8582c-126">詳細については、次を参照してください。 [NIB: 方法: 新しいプロジェクト項目の追加](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)です。</span><span class="sxs-lookup"><span data-stu-id="8582c-126">For more information, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span>  
  
3.  <span data-ttu-id="8582c-127">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="8582c-127">Build the project.</span></span>  
  
4.  <span data-ttu-id="8582c-128">**ツール** メニューをクリックして、**オプション**項目。</span><span class="sxs-lookup"><span data-stu-id="8582c-128">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="8582c-129">をクリックして**全般**下にある、 **Windows フォーム デザイナー**項目のことを確認して、 **AutoToolboxPopulate**オプションに設定されて**True**です。</span><span class="sxs-lookup"><span data-stu-id="8582c-129">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="8582c-130">カスタム コンポーネントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8582c-130">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="8582c-131">次の手順では、フォームでカスタム コンポーネントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8582c-131">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="8582c-132">**ツールボックス**自動的に新しいコンポーネントのアカウントは、これは他のコンポーネントまたはコントロールの作成と同じくらい簡単です。</span><span class="sxs-lookup"><span data-stu-id="8582c-132">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="8582c-133">カスタム コンポーネントのインスタンスを作成するには</span><span class="sxs-lookup"><span data-stu-id="8582c-133">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="8582c-134">プロジェクトのフォームを開いて、**フォーム デザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="8582c-134">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="8582c-135">**ツールボックス**と呼ばれる新しいタブをクリックして**ToolboxExample コンポーネント**です。</span><span class="sxs-lookup"><span data-stu-id="8582c-135">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="8582c-136">タブをクリックすると表示されます**と**です。</span><span class="sxs-lookup"><span data-stu-id="8582c-136">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8582c-137">パフォーマンス上の理由から、コンポーネントの自動設定された領域で、**ツールボックス**カスタムのビットマップを表示しないと、<xref:System.Drawing.ToolboxBitmapAttribute>はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8582c-137">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="8582c-138">カスタムのコンポーネントのアイコンを表示する、**ツールボックス**を使用して、**ツールボックス アイテムの選択**ダイアログ ボックスで、コンポーネントの読み込みをします。</span><span class="sxs-lookup"><span data-stu-id="8582c-138">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="8582c-139">コンポーネントをフォームにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8582c-139">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="8582c-140">コンポーネントのインスタンスが作成され、追加、**コンポーネント トレイ**です。</span><span class="sxs-lookup"><span data-stu-id="8582c-140">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="8582c-141">アンロードして、カスタム コンポーネントを再読み込み</span><span class="sxs-lookup"><span data-stu-id="8582c-141">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="8582c-142">**ツールボックス**の各コンポーネントのではアカウントには、プロジェクトが読み込まれ、プロジェクトが読み込まれると、プロジェクトのコンポーネントへの参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="8582c-142">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="8582c-143">アンロードとコンポーネントを再読み込みのツールボックスへの影響をテストするには</span><span class="sxs-lookup"><span data-stu-id="8582c-143">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="8582c-144">ソリューションからプロジェクトをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="8582c-144">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="8582c-145">プロジェクトのアンロードの詳細については、次を参照してください。 [NIB: 方法:: アンロードし、プロジェクトの再読み込み](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b)です。</span><span class="sxs-lookup"><span data-stu-id="8582c-145">For more information about unloading projects, see [NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span></span> <span data-ttu-id="8582c-146">保存するメッセージが表示されたら、選択**はい**です。</span><span class="sxs-lookup"><span data-stu-id="8582c-146">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="8582c-147">新しい**Windows アプリケーション**プロジェクトがソリューションにします。</span><span class="sxs-lookup"><span data-stu-id="8582c-147">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="8582c-148">フォームを開いて、**デザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="8582c-148">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="8582c-149">**ToolboxExample コンポーネント**前のプロジェクトからタブは削除します。</span><span class="sxs-lookup"><span data-stu-id="8582c-149">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="8582c-150">再読み込み、`ToolboxExample`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="8582c-150">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="8582c-151">**ToolboxExample コンポーネント** タブのようになりましたが再表示されます。</span><span class="sxs-lookup"><span data-stu-id="8582c-151">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8582c-152">次の手順</span><span class="sxs-lookup"><span data-stu-id="8582c-152">Next Steps</span></span>  
 <span data-ttu-id="8582c-153">このチュートリアルで説明する、**ツールボックス**、プロジェクトのコンポーネントの考慮ですが、**ツールボックス**コントロールもです。</span><span class="sxs-lookup"><span data-stu-id="8582c-153">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="8582c-154">追加と管理プロジェクトをソリューションから削除して、独自のカスタム コントロールをテストします。</span><span class="sxs-lookup"><span data-stu-id="8582c-154">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8582c-155">参照</span><span class="sxs-lookup"><span data-stu-id="8582c-155">See Also</span></span>  
 [<span data-ttu-id="8582c-156">一般に、Windows フォーム デザイナー、オプション ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="8582c-156">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 <span data-ttu-id="8582c-157">[方法: [ツールボックス] タブの操作](http://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)</span><span class="sxs-lookup"><span data-stu-id="8582c-157">[How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)</span></span>  
 <span data-ttu-id="8582c-158">[[ツールボックス アイテムの選択] ダイアログ ボックス (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)</span><span class="sxs-lookup"><span data-stu-id="8582c-158">[Choose Toolbox Items Dialog Box (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)</span></span>  
 [<span data-ttu-id="8582c-159">Windows フォームへのコントロールの追加</span><span class="sxs-lookup"><span data-stu-id="8582c-159">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
