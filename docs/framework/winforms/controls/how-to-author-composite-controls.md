---
title: "方法 : 複合コントロールを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 621d761411d5c33316d80e6dcdc9d0ec675242b2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="a88f2-102">方法 : 複合コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="a88f2-102">How to: Author Composite Controls</span></span>
<span data-ttu-id="a88f2-103">複合コントロールはさまざまな方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a88f2-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="a88f2-104">Windows デスクトップ アプリケーション プロジェクトの一部として複合コントロールを作成し、プロジェクト内のフォーム上でのみ使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a88f2-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="a88f2-105">または、Windows コントロール ライブラリ プロジェクトで複合コントロールを作成し、プロジェクトをアセンブリにコンパイルして、他のプロジェクトで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a88f2-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="a88f2-106">そのコントロールから継承することや、ビジュアル継承を使用して特殊な用途のために簡単にカスタマイズすることまでできます。</span><span class="sxs-lookup"><span data-stu-id="a88f2-106">You can even inherit from them, and use visual inheritance to customize them quickly for special purposes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a88f2-107">Web フォームで使用する複合コントロールを作成する場合は、「[カスタム ASP.NET サーバー コントロールの開発](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a88f2-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
>   
>  <span data-ttu-id="a88f2-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a88f2-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a88f2-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a88f2-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a88f2-110">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a88f2-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-author-a-composite-control"></a><span data-ttu-id="a88f2-111">複合コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="a88f2-111">To author a composite control</span></span>  
  
1.  <span data-ttu-id="a88f2-112">`DemoControlHost` という新しい **Windows アプリケーション** プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a88f2-112">Open a new **Windows Application** project called `DemoControlHost`.</span></span>  
  
2.  <span data-ttu-id="a88f2-113">**[プロジェクト]** メニューの **[ユーザー コントロールの追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a88f2-113">On the **Project**menu, click **Add User Control**.</span></span>  
  
3.  <span data-ttu-id="a88f2-114">**[新しい項目の追加]** ダイアログ ボックスで、クラス ファイル (.vb または .cs ファイル) に複合コントロールに付ける名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-114">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>  
  
4.  <span data-ttu-id="a88f2-115">**[追加]** をクリックして、複合コントロールのクラス ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-115">Click the **Add** button to create the class file for the composite control.</span></span>  
  
5.  <span data-ttu-id="a88f2-116">複合コントロールのサーフェスに **[ツールボックス]** からコントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-116">Add controls from the **Toolbox** to the composite control surface.</span></span>  
  
6.  <span data-ttu-id="a88f2-117">複合コントロールまたはその内在コントロールによって発生したイベントを処理するために、イベント プロシージャにコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-117">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>  
  
7.  <span data-ttu-id="a88f2-118">複合コントロールのデザイナーを閉じて、メッセージが表示されたらファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-118">Close the designer for the composite control, and save the file when you are prompted.</span></span>  
  
8.  <span data-ttu-id="a88f2-119">**[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a88f2-119">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="a88f2-120">カスタム コントロールが **[ツールボックス]** に表示されるようにプロジェクトをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a88f2-120">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="a88f2-121">**[ツールボックス]** の **[DemoControlHost]** タブを使用して、コントロールのインスタンスを `Form1` に追加します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-121">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>  
  
### <a name="to-author-a-control-class-library"></a><span data-ttu-id="a88f2-122">コントロール クラス ライブラリを作成するには</span><span class="sxs-lookup"><span data-stu-id="a88f2-122">To author a control class library</span></span>  
  
1.  <span data-ttu-id="a88f2-123">新しい **Windows コントロール ライブラリ** プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a88f2-123">Open a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="a88f2-124">既定では、プロジェクトに複合コントロールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a88f2-124">By default, the project contains a composite control.</span></span>  
  
2.  <span data-ttu-id="a88f2-125">上記の手順の説明に従ってコントロールとコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-125">Add controls and code as described in the procedure above.</span></span>  
  
3.  <span data-ttu-id="a88f2-126">継承クラスで変更しないコントロールを選択して、このコントロールの **Modifiers** プロパティを **Private** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-126">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>  
  
4.  <span data-ttu-id="a88f2-127">DLL をビルドします。</span><span class="sxs-lookup"><span data-stu-id="a88f2-127">Build the DLL.</span></span>  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="a88f2-128">コントロール クラス ライブラリの複合コントロールから継承するには</span><span class="sxs-lookup"><span data-stu-id="a88f2-128">To inherit from a composite control in a control class library</span></span>  
  
1.  <span data-ttu-id="a88f2-129">**[ファイル]** メニューで、**[追加]** をポイントし、**[新しいプロジェクト]** を選択して、新しい **Windows アプリケーション** プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-129">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>  
  
2.  <span data-ttu-id="a88f2-130">**ソリューション エクスプローラー**で、新しいプロジェクトの **[参照設定]** フォルダーを右クリックし、**[参照の追加]** をクリックして **[参照の追加]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="a88f2-130">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
3.  <span data-ttu-id="a88f2-131">**[プロジェクト]** タブを選択し、コントロール ライブラリ プロジェクトをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a88f2-131">Select the **Projects** tab and double-click your control library project.</span></span>  
  
4.  <span data-ttu-id="a88f2-132">**[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a88f2-132">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="a88f2-133">**ソリューション エクスプローラー**で、コントロール ライブラリ プロジェクトを右クリックし、ショートカット メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a88f2-133">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>  
  
6.  <span data-ttu-id="a88f2-134">**[新しい項目の追加]** ダイアログ ボックスの **[継承されたユーザー コントロール]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-134">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>  
  
7.  <span data-ttu-id="a88f2-135">**[継承ピッカー]** ダイアログ ボックスで、継承元のコントロールをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a88f2-135">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>  
  
     <span data-ttu-id="a88f2-136">新しいコントロールがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a88f2-136">A new control is added to your project.</span></span>  
  
8.  <span data-ttu-id="a88f2-137">新しいコントロールのビジュアル デザイナーを開き、別の内在コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="a88f2-137">Open the visual designer for the new control and add additional constituent controls.</span></span>  
  
     <span data-ttu-id="a88f2-138">DLL の複合コントロールから継承された内在コントロールを表示し、**Modifiers** プロパティが **Public** であるコントロールのプロパティを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="a88f2-138">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="a88f2-139">**Modifiers** プロパティが **Private** であるコントロールのプロパティを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="a88f2-139">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a88f2-140">参照</span><span class="sxs-lookup"><span data-stu-id="a88f2-140">See Also</span></span>  
 [<span data-ttu-id="a88f2-141">チュートリアル: Visual Basic による複合コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="a88f2-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="a88f2-142">チュートリアル: Visual C# による複合コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="a88f2-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="a88f2-143">チュートリアル: Visual Basic による Windows フォーム コントロールからの継承</span><span class="sxs-lookup"><span data-stu-id="a88f2-143">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="a88f2-144">チュートリアル: Visual C# による Windows フォーム コントロールからの継承</span><span class="sxs-lookup"><span data-stu-id="a88f2-144">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [<span data-ttu-id="a88f2-145">コントロールの種類に関するアドバイス</span><span class="sxs-lookup"><span data-stu-id="a88f2-145">Control Type Recommendations</span></span>](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [<span data-ttu-id="a88f2-146">方法: Windows フォームのコントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="a88f2-146">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="a88f2-147">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="a88f2-147">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
