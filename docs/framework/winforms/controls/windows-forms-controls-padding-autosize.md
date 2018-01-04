---
title: "チュートリアル : Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 797a432bb8cfd3af3b5f030be8f71c78a1a393e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a><span data-ttu-id="14330-102">チュートリアル : Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト</span><span class="sxs-lookup"><span data-stu-id="14330-102">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>
<span data-ttu-id="14330-103">フォーム上のコントロールを正確に配置することは、多くのアプリケーションで優先度の高い作業です。</span><span class="sxs-lookup"><span data-stu-id="14330-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="14330-104">**Windows フォーム デザイナー**これを実現するさまざまなレイアウト ツールを提供します。</span><span class="sxs-lookup"><span data-stu-id="14330-104">The **Windows Forms Designer** gives you many layout tools to accomplish this.</span></span> <span data-ttu-id="14330-105">最も重要な 3 つが、 <xref:System.Windows.Forms.Control.Margin%2A>、 <xref:System.Windows.Forms.Control.Padding%2A>、および<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティで、すべての Windows フォーム コントロール上に存在します。</span><span class="sxs-lookup"><span data-stu-id="14330-105">Three of the most important are the <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, and <xref:System.Windows.Forms.Control.AutoSize%2A> properties, which are present on all Windows Forms controls.</span></span>  
  
 <span data-ttu-id="14330-106"><xref:System.Windows.Forms.Control.Margin%2A> プロパティは、その他のコントロールで、コントロールの枠線からの指定された距離を保持するコントロールの周囲のスペースを定義します。</span><span class="sxs-lookup"><span data-stu-id="14330-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="14330-107"><xref:System.Windows.Forms.Control.Padding%2A> プロパティは、コントロールの内容 (<xref:System.Windows.Forms.Control.Text%2A> プロパティの値など) で、コントロールの枠線からの指定した距離を保持するコントロールの内部のスペースを定義します。</span><span class="sxs-lookup"><span data-stu-id="14330-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="14330-108">次の図は、コントロールの <xref:System.Windows.Forms.Control.Padding%2A> プロパティと <xref:System.Windows.Forms.Control.Margin%2A> プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="14330-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="14330-109">![フォーム コントロールの Windows のパディングとマージン](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="14330-109">![Padding And Margin for Windows Forms Controls](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="14330-110"><xref:System.Windows.Forms.Control.AutoSize%2A>プロパティ、コントロールの内容を自動的にサイズに通知します。</span><span class="sxs-lookup"><span data-stu-id="14330-110">The <xref:System.Windows.Forms.Control.AutoSize%2A> property tells a control to automatically size itself to its contents.</span></span> <span data-ttu-id="14330-111">これは、サイズは変更されませんが元の値より小さくなる自体<xref:System.Windows.Forms.Control.Size%2A>プロパティ、およびそれがの値のアカウントがその<xref:System.Windows.Forms.Control.Padding%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-111">It will not resize itself to be smaller than the value of its original <xref:System.Windows.Forms.Control.Size%2A> property, and it will account for the value of its <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>  
  
 <span data-ttu-id="14330-112">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="14330-112">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="14330-113">Windows フォーム プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="14330-113">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="14330-114">コントロールのマージンの設定</span><span class="sxs-lookup"><span data-stu-id="14330-114">Setting Margins for Your Controls</span></span>  
  
-   <span data-ttu-id="14330-115">コントロールの余白を設定</span><span class="sxs-lookup"><span data-stu-id="14330-115">Setting Padding for Your Controls</span></span>  
  
-   <span data-ttu-id="14330-116">自動的に、コントロールのサイズ変更</span><span class="sxs-lookup"><span data-stu-id="14330-116">Automatically Sizing Your Controls</span></span>  
  
 <span data-ttu-id="14330-117">終了すると、これらの重要なレイアウト機能が果たす役割について理解できます。</span><span class="sxs-lookup"><span data-stu-id="14330-117">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14330-118">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="14330-118">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="14330-119">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14330-119">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="14330-120">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14330-120">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="14330-121">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="14330-121">Prerequisites</span></span>  
 <span data-ttu-id="14330-122">このチュートリアルを完了するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="14330-122">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="14330-123">作成し、Visual Studio がインストールされているコンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="14330-123">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="14330-124">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="14330-124">Creating the Project</span></span>  
 <span data-ttu-id="14330-125">最初にプロジェクトを作成し、フォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="14330-125">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="14330-126">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="14330-126">To create the project</span></span>  
  
1.  <span data-ttu-id="14330-127">作成、 **Windows アプリケーション**というプロジェクト`LayoutExample`です。</span><span class="sxs-lookup"><span data-stu-id="14330-127">Create a **Windows Application** project called `LayoutExample`.</span></span> <span data-ttu-id="14330-128">詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)です。</span><span class="sxs-lookup"><span data-stu-id="14330-128">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) .</span></span>  
  
2.  <span data-ttu-id="14330-129">フォームを選択、 **Windows フォーム デザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="14330-129">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="setting-margins-for-your-controls"></a><span data-ttu-id="14330-130">コントロールのマージンの設定</span><span class="sxs-lookup"><span data-stu-id="14330-130">Setting Margins for Your Controls</span></span>  
 <span data-ttu-id="14330-131">使用して、コントロールの間で既定の間隔を設定することができます、<xref:System.Windows.Forms.Control.Margin%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-131">You can set the default distance between your controls using the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span> <span data-ttu-id="14330-132">コントロールを移動するときに別のコントロールに十分な数を閉じるには、2 つのコントロールの余白を示すスナップ線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="14330-132">When you move a control close enough to another control, you will see a snapline that shows the margins for the two controls.</span></span> <span data-ttu-id="14330-133">移動中のコントロールは、余白で定義された距離にもスナップされます。</span><span class="sxs-lookup"><span data-stu-id="14330-133">The control you are moving will also snap to the distance defined by the margins.</span></span>  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a><span data-ttu-id="14330-134">Margin プロパティを使用して、フォーム上のコントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="14330-134">To arrange controls on your form using the Margin property</span></span>  
  
1.  <span data-ttu-id="14330-135">2 つをドラッグして<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="14330-135">Drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="14330-136">いずれかを選択、<xref:System.Windows.Forms.Button>を制御し、ほぼに触れることまで、その他の近くに移動します。</span><span class="sxs-lookup"><span data-stu-id="14330-136">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other, until they are almost touching.</span></span>  
  
     <span data-ttu-id="14330-137">それらの間に表示されるスナップ線を観察します。</span><span class="sxs-lookup"><span data-stu-id="14330-137">Observe the snapline that appears between them.</span></span> <span data-ttu-id="14330-138">この距離は、2 つのコントロールの<xref:System.Windows.Forms.Control.Margin%2A>値。</span><span class="sxs-lookup"><span data-stu-id="14330-138">This distance is the sum of the two controls' <xref:System.Windows.Forms.Control.Margin%2A> values.</span></span> <span data-ttu-id="14330-139">移動中のコントロールは、この距離にスナップされます。</span><span class="sxs-lookup"><span data-stu-id="14330-139">The control you are moving snaps to this distance.</span></span> <span data-ttu-id="14330-140">詳細については、「[チュートリアル: Windows フォームを使用するスナップ線上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)です。</span><span class="sxs-lookup"><span data-stu-id="14330-140">For details, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
3.  <span data-ttu-id="14330-141">変更、<xref:System.Windows.Forms.Control.Margin%2A>を展開して、コントロールのいずれかのプロパティ、<xref:System.Windows.Forms.Control.Margin%2A>内のエントリ、**プロパティ**ウィンドウと設定、 <xref:System.Windows.Forms.Padding.All%2A> 20 プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-141">Change the <xref:System.Windows.Forms.Control.Margin%2A> property of one of the controls by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 20.</span></span>  
  
4.  <span data-ttu-id="14330-142">いずれかを選択、<xref:System.Windows.Forms.Button>を制御し、もう一方の近くに移動します。</span><span class="sxs-lookup"><span data-stu-id="14330-142">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other.</span></span>  
  
     <span data-ttu-id="14330-143">スナップ線を定義する、余白の値の合計が長いと、コントロールが他のコントロールから、広範囲にスナップされます。</span><span class="sxs-lookup"><span data-stu-id="14330-143">The snapline defining the sum of the margin values is longer and that the control snaps to a greater distance from the other control.</span></span>  
  
5.  <span data-ttu-id="14330-144">変更、<xref:System.Windows.Forms.Control.Margin%2A>を展開して選択したコントロールのプロパティ、<xref:System.Windows.Forms.Control.Margin%2A>内のエントリ、**プロパティ**ウィンドウと設定、 <xref:System.Windows.Forms.Padding.Top%2A> 5 プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-144">Change the <xref:System.Windows.Forms.Control.Margin%2A> property of the selected control by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.Top%2A> property to 5.</span></span>  
  
6.  <span data-ttu-id="14330-145">その他のコントロールの下の選択したコントロールを移動し、スナップ線が短いことを確認します。</span><span class="sxs-lookup"><span data-stu-id="14330-145">Move the selected control below the other control and observe that the snapline is shorter.</span></span> <span data-ttu-id="14330-146">選択したコントロールを他のコントロールの左側に移動し、スナップ線が手順 4. で計測された値を保持することを確認します。</span><span class="sxs-lookup"><span data-stu-id="14330-146">Move the selected control to the left of the other control and observe that the snapline retains the value observed in step 4.</span></span>  
  
7.  <span data-ttu-id="14330-147">側面のそれぞれを設定することができます、<xref:System.Windows.Forms.Control.Margin%2A>プロパティ、 <xref:System.Windows.Forms.Padding.Left%2A>、 <xref:System.Windows.Forms.Padding.Top%2A>、 <xref:System.Windows.Forms.Padding.Right%2A>、 <xref:System.Windows.Forms.Padding.Bottom%2A>、別の値に設定できるはすべてに同じ値を<xref:System.Windows.Forms.Padding.All%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-147">You can set each of the aspects of the <xref:System.Windows.Forms.Control.Margin%2A> property, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, to different values, or you can set them all to the same value with the <xref:System.Windows.Forms.Padding.All%2A> property.</span></span>  
  
## <a name="setting-padding-for-your-controls"></a><span data-ttu-id="14330-148">コントロールの余白を設定</span><span class="sxs-lookup"><span data-stu-id="14330-148">Setting Padding for Your Controls</span></span>  
 <span data-ttu-id="14330-149">アプリケーションに必要な正確なレイアウトを実現するために、コントロールが子コントロールを含む多くの場合。</span><span class="sxs-lookup"><span data-stu-id="14330-149">To achieve the precise layout required for your application, your controls will often contain child controls.</span></span> <span data-ttu-id="14330-150">親コントロールの境界線に子コントロールの境界線の近接度を指定する場合は、使用、親コントロールの<xref:System.Windows.Forms.Control.Padding%2A>と共に子コントロールのプロパティ<xref:System.Windows.Forms.Control.Margin%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-150">When you want to specify the proximity of the child control's border to the parent control's border, use the parent control's <xref:System.Windows.Forms.Control.Padding%2A> property in conjunction with the child control's <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span> <span data-ttu-id="14330-151"><xref:System.Windows.Forms.Control.Padding%2A>コントロールのコンテンツの近接度を制御するプロパティを使用しても (たとえば、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティ)、境界線をします。</span><span class="sxs-lookup"><span data-stu-id="14330-151">The <xref:System.Windows.Forms.Control.Padding%2A> property is also used to control the proximity of a control's content (for example, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property) to its borders.</span></span>  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a><span data-ttu-id="14330-152">埋め込みを使用して、フォーム上のコントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="14330-152">To arrange controls on your form using padding</span></span>  
  
1.  <span data-ttu-id="14330-153">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="14330-153">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="14330-154"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true` に変更します。</span><span class="sxs-lookup"><span data-stu-id="14330-154">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="14330-155">変更、<xref:System.Windows.Forms.Control.Padding%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Padding%2A>内のエントリ、**プロパティ**ウィンドウと設定、 <xref:System.Windows.Forms.Padding.All%2A> 5 プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-155">Change the <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 5.</span></span>  
  
     <span data-ttu-id="14330-156">コントロールを拡張する場合、新しい余白の領域を確保します。</span><span class="sxs-lookup"><span data-stu-id="14330-156">The control expands to provide room for the new padding.</span></span>  
  
4.  <span data-ttu-id="14330-157">ドラッグ、<xref:System.Windows.Forms.GroupBox>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="14330-157">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="14330-158">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**に、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-158">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="14330-159">位置、<xref:System.Windows.Forms.Button>の右下隅と揃えるためにの制御、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-159">Position the <xref:System.Windows.Forms.Button> control so it is flush with the lower-right corner of the <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
     <span data-ttu-id="14330-160">として表示されるスナップ線を観察、<xref:System.Windows.Forms.Button>下と右の境界線のコントロールが近づく、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-160">Observe the snaplines that appear as the <xref:System.Windows.Forms.Button> control approaches the bottom and right borders of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="14330-161">これらのスナップ線に対応している、<xref:System.Windows.Forms.Control.Margin%2A>のプロパティ、<xref:System.Windows.Forms.Button>です。</span><span class="sxs-lookup"><span data-stu-id="14330-161">These snaplines correspond to the <xref:System.Windows.Forms.Control.Margin%2A> property of the <xref:System.Windows.Forms.Button>.</span></span>  
  
5.  <span data-ttu-id="14330-162">変更、<xref:System.Windows.Forms.GroupBox>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Padding%2A>内のエントリ、**プロパティ**ウィンドウと設定、 <xref:System.Windows.Forms.Padding.All%2A> 20 プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-162">Change the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 20.</span></span>  
  
6.  <span data-ttu-id="14330-163">選択、<xref:System.Windows.Forms.Button>内の制御、<xref:System.Windows.Forms.GroupBox>を制御しの中央に移動、<xref:System.Windows.Forms.GroupBox>です。</span><span class="sxs-lookup"><span data-stu-id="14330-163">Select the <xref:System.Windows.Forms.Button> control within the <xref:System.Windows.Forms.GroupBox> control and move it toward the center of the <xref:System.Windows.Forms.GroupBox>.</span></span>  
  
     <span data-ttu-id="14330-164">枠線から遠隔地にスナップ線が表示される、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-164">The snaplines appear at a greater distance from the borders of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="14330-165">この距離は、の<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティおよび<xref:System.Windows.Forms.GroupBox>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-165">This distance is the sum of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Margin%2A> property and the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>  
  
## <a name="automatically-sizing-your-controls"></a><span data-ttu-id="14330-166">自動的に、コントロールのサイズ変更</span><span class="sxs-lookup"><span data-stu-id="14330-166">Automatically Sizing Your Controls</span></span>  
 <span data-ttu-id="14330-167">一部のアプリケーションでコントロールのサイズはできません、同じ実行時にデザイン時と同じ。</span><span class="sxs-lookup"><span data-stu-id="14330-167">In some applications, the size of a control will not be the same at run time as it was at design time.</span></span> <span data-ttu-id="14330-168">テキスト、<xref:System.Windows.Forms.Button>コントロール、たとえば、考慮できる、データベースからとその長さは事前にわかっていません。</span><span class="sxs-lookup"><span data-stu-id="14330-168">The text of a <xref:System.Windows.Forms.Button> control, for example, may be taken from a database, and its length will not be known in advance.</span></span>  
  
 <span data-ttu-id="14330-169">ときに、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティに設定されている`true`、そのコンテンツへのコントロールのサイズがします。</span><span class="sxs-lookup"><span data-stu-id="14330-169">When the <xref:System.Windows.Forms.Control.AutoSize%2A> property is set to `true`, the control will size itself to its content.</span></span> <span data-ttu-id="14330-170">詳細については、次を参照してください。 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="14330-170">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a><span data-ttu-id="14330-171">AutoSize プロパティを使用して、フォーム上のコントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="14330-171">To arrange controls on your form using the AutoSize property</span></span>  
  
1.  <span data-ttu-id="14330-172">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="14330-172">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="14330-173"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true` に変更します。</span><span class="sxs-lookup"><span data-stu-id="14330-173">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="14330-174">変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティを"**このボタンには、Text プロパティの長い文字列**"。</span><span class="sxs-lookup"><span data-stu-id="14330-174">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property**."</span></span>  
  
     <span data-ttu-id="14330-175">変更をコミットする場合、<xref:System.Windows.Forms.Button>コントロールの新しいテキストが収まるようにサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="14330-175">When you commit the change, the <xref:System.Windows.Forms.Button> control resizes itself to fit the new text.</span></span>  
  
4.  <span data-ttu-id="14330-176">別のドラッグ<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="14330-176">Drag another <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
5.  <span data-ttu-id="14330-177">変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティを"**このボタンには、Text プロパティの長い文字列**"。</span><span class="sxs-lookup"><span data-stu-id="14330-177">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property.**"</span></span>  
  
     <span data-ttu-id="14330-178">変更をコミットする場合、<xref:System.Windows.Forms.Button>コントロール サイズ変更されない自体、およびテキストは、コントロールの右端で切り詰められます。</span><span class="sxs-lookup"><span data-stu-id="14330-178">When you commit the change, the <xref:System.Windows.Forms.Button> control does not resize itself, and the text is clipped by the right edge of the control.</span></span>  
  
6.  <span data-ttu-id="14330-179">変更、<xref:System.Windows.Forms.Control.Padding%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Padding%2A>内のエントリ、**プロパティ**ウィンドウと設定、 <xref:System.Windows.Forms.Padding.All%2A> 5 プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-179">Change the <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 5.</span></span>  
  
     <span data-ttu-id="14330-180">コントロールの内部のテキストは、すべての 4 辺にクリップされます。</span><span class="sxs-lookup"><span data-stu-id="14330-180">The text in the control's interior is clipped on all four sides.</span></span>  
  
7.  <span data-ttu-id="14330-181">変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="14330-181">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="14330-182"><xref:System.Windows.Forms.Button>コントロールのサイズは、文字列全体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="14330-182">The <xref:System.Windows.Forms.Button> control resizes itself to encompass the entire string.</span></span> <span data-ttu-id="14330-183">テキストの周辺の余白が追加されても、原因、<xref:System.Windows.Forms.Button>コントロールをすべて次の 4 つの方向に展開します。</span><span class="sxs-lookup"><span data-stu-id="14330-183">Also, padding has been added around the text, causing the <xref:System.Windows.Forms.Button> control to expand in all four directions.</span></span>  
  
8.  <span data-ttu-id="14330-184">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="14330-184">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="14330-185">フォームの右下隅近くに配置します。</span><span class="sxs-lookup"><span data-stu-id="14330-185">Position it near the lower-right corner of the form.</span></span>  
  
9. <span data-ttu-id="14330-186"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true` に変更します。</span><span class="sxs-lookup"><span data-stu-id="14330-186">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>  
  
10. <span data-ttu-id="14330-187">設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを<xref:System.Windows.Forms.AnchorStyles.Right>、<xref:System.Windows.Forms.AnchorStyles.Bottom>です。</span><span class="sxs-lookup"><span data-stu-id="14330-187">Set the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.</span></span>  
  
11. <span data-ttu-id="14330-188">変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティを"**このボタンには、Text プロパティの長い文字列**"。</span><span class="sxs-lookup"><span data-stu-id="14330-188">Change the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Text%2A> property to "**This button has a long string for its Text property.**"</span></span>  
  
     <span data-ttu-id="14330-189">変更をコミットする場合、<xref:System.Windows.Forms.Button>コントロールは左方向サイズ変更します。</span><span class="sxs-lookup"><span data-stu-id="14330-189">When you commit the change, the <xref:System.Windows.Forms.Button> control resizes itself toward the left.</span></span> <span data-ttu-id="14330-190">自動サイズ変更が反対の方向にコントロールのサイズを大きく一般に、その<xref:System.Windows.Forms.Control.Anchor%2A>プロパティの設定。</span><span class="sxs-lookup"><span data-stu-id="14330-190">In general, automatic sizing will increase the size of a control in the direction opposite its <xref:System.Windows.Forms.Control.Anchor%2A> property setting.</span></span>  
  
## <a name="autosize-and-autosizemode-properties"></a><span data-ttu-id="14330-191">AutoSize と AutoSizeMode プロパティ</span><span class="sxs-lookup"><span data-stu-id="14330-191">AutoSize and AutoSizeMode Properties</span></span>  
 <span data-ttu-id="14330-192">一部のコントロールのサポート、`AutoSizeMode`プロパティ、コントロールの自動サイズ変更動作をより詳細に制御できます。</span><span class="sxs-lookup"><span data-stu-id="14330-192">Some controls support the `AutoSizeMode` property, which gives you more fine-grained control over the automatic sizing behavior of a control.</span></span>  
  
#### <a name="to-use-the-autosizemode-property"></a><span data-ttu-id="14330-193">AutoSizeMode プロパティを使用するには</span><span class="sxs-lookup"><span data-stu-id="14330-193">To use the AutoSizeMode property</span></span>  
  
1.  <span data-ttu-id="14330-194">ドラッグ、<xref:System.Windows.Forms.Panel>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="14330-194">Drag a <xref:System.Windows.Forms.Panel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="14330-195">値を設定、<xref:System.Windows.Forms.Panel>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="14330-195">Set the value of the <xref:System.Windows.Forms.Panel> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="14330-196">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**に、<xref:System.Windows.Forms.Panel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-196">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
4.  <span data-ttu-id="14330-197">場所、<xref:System.Windows.Forms.Button>の右下隅のコントロール、<xref:System.Windows.Forms.Panel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-197">Place the <xref:System.Windows.Forms.Button> control near the lower-right corner of the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
5.  <span data-ttu-id="14330-198">選択、<xref:System.Windows.Forms.Panel>を制御し、右下のサイズ変更ハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="14330-198">Select the <xref:System.Windows.Forms.Panel> control and grab the lower-right sizing handle.</span></span> <span data-ttu-id="14330-199">サイズ変更、<xref:System.Windows.Forms.Panel>コントロールを大きくしたり小さくします。</span><span class="sxs-lookup"><span data-stu-id="14330-199">Resize the <xref:System.Windows.Forms.Panel> control to be larger and smaller.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="14330-200">サイズを変更する自由に、<xref:System.Windows.Forms.Panel>コントロールがサイズを調整できないことの位置よりも小さい、<xref:System.Windows.Forms.Button>コントロールの右下隅です。</span><span class="sxs-lookup"><span data-stu-id="14330-200">You can freely resize the <xref:System.Windows.Forms.Panel> control, but you cannot size it smaller than the position of the <xref:System.Windows.Forms.Button> control's lower-right corner.</span></span> <span data-ttu-id="14330-201">この動作は、の既定値で指定された、`AutoSizeMode`プロパティである<xref:System.Windows.Forms.AutoSizeMode.GrowOnly>です。</span><span class="sxs-lookup"><span data-stu-id="14330-201">This behavior is specified by the default value of the `AutoSizeMode` property, which is <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.</span></span>  
  
6.  <span data-ttu-id="14330-202">値を設定、<xref:System.Windows.Forms.Panel>コントロールの`AutoSizeMode`プロパティを<xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>です。</span><span class="sxs-lookup"><span data-stu-id="14330-202">Set the value of the <xref:System.Windows.Forms.Panel> control's `AutoSizeMode` property to <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.</span></span>  
  
     <span data-ttu-id="14330-203"><xref:System.Windows.Forms.Panel>コントロールのサイズを囲むように、<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-203">The <xref:System.Windows.Forms.Panel> control sizes itself to surround the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="14330-204">サイズを変更することはできません、<xref:System.Windows.Forms.Panel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-204">You cannot resize the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
7.  <span data-ttu-id="14330-205">ドラッグ、<xref:System.Windows.Forms.Button>コントロールの左上隅に向かって、<xref:System.Windows.Forms.Panel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-205">Drag the <xref:System.Windows.Forms.Button> control toward the upper-left corner of the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
     <span data-ttu-id="14330-206"><xref:System.Windows.Forms.Panel>コントロール サイズを変更し、<xref:System.Windows.Forms.Button>コントロールの新しい位置。</span><span class="sxs-lookup"><span data-stu-id="14330-206">The <xref:System.Windows.Forms.Panel> control resizes to the <xref:System.Windows.Forms.Button> control's new position.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="14330-207">次の手順</span><span class="sxs-lookup"><span data-stu-id="14330-207">Next Steps</span></span>  
 <span data-ttu-id="14330-208">Windows フォーム アプリケーションでのコントロールの配置の他の多くのレイアウト機能があります。</span><span class="sxs-lookup"><span data-stu-id="14330-208">There are many other layout features for arranging controls in your Windows Forms applications.</span></span> <span data-ttu-id="14330-209">一部の操作を試すの組み合わせを次に示します。</span><span class="sxs-lookup"><span data-stu-id="14330-209">Here are some combinations you might try:</span></span>  
  
-   <span data-ttu-id="14330-210">フォームを使用して、ビルド、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-210">Build a form using a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="14330-211">詳細については、「[チュートリアル: Windows を使用して、TableLayoutPanel をフォーム上コントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)です。</span><span class="sxs-lookup"><span data-stu-id="14330-211">For details, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span> <span data-ttu-id="14330-212">値を変更してみてください、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティだけでなく<xref:System.Windows.Forms.Control.Margin%2A>コントロールの子コントロールのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="14330-212">Try changing the values of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.Control.Padding%2A> property, as well as the <xref:System.Windows.Forms.Control.Margin%2A> property on its child controls.</span></span>  
  
-   <span data-ttu-id="14330-213">同じ実験を使用して、再試行してください、<xref:System.Windows.Forms.FlowLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-213">Try the same experiment using a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="14330-214">詳細については、「[チュートリアル: Windows を使用して、FlowLayoutPanel をフォーム上コントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)です。</span><span class="sxs-lookup"><span data-stu-id="14330-214">For details, see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).</span></span>  
  
-   <span data-ttu-id="14330-215">実験で子コントロールのドッキングと、<xref:System.Windows.Forms.Panel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14330-215">Experiment with docking child controls in a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="14330-216"><xref:System.Windows.Forms.Control.Padding%2A>プロパティは、の一般的な実現、<xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>プロパティ、およびを満たすことができる自分でこれは大文字と小文字子コントロールを配置することにより、<xref:System.Windows.Forms.Panel>コントロールおよび子コントロールの設定<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="14330-216">The <xref:System.Windows.Forms.Control.Padding%2A> property is a more general realization of the <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> property, and you can satisfy yourself that this is the case by putting a child control in a <xref:System.Windows.Forms.Panel> control and setting the child control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="14330-217">設定、<xref:System.Windows.Forms.Panel>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティをさまざまな値変化を確認します。</span><span class="sxs-lookup"><span data-stu-id="14330-217">Set the <xref:System.Windows.Forms.Panel> control's <xref:System.Windows.Forms.Control.Padding%2A> property to various values and note the effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14330-218">参照</span><span class="sxs-lookup"><span data-stu-id="14330-218">See Also</span></span>  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 [<span data-ttu-id="14330-219">AutoSize プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="14330-219">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="14330-220">チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="14330-220">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="14330-221">チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="14330-221">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="14330-222">チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="14330-222">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
