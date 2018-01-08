---
title: "チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 028b66fea2b35e7b36760ec7c606f81ca2301620
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a><span data-ttu-id="a7dc3-102">チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="a7dc3-102">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>
<span data-ttu-id="a7dc3-103">フォーム上のコントロールを正確に配置することは、多くのアプリケーションで優先度の高い作業です。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="a7dc3-104">Windows フォーム デザイナーでは、これを実現するさまざまなレイアウト ツールを提供します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-104">The Windows Forms Designer gives you many layout tools to accomplish this.</span></span> <span data-ttu-id="a7dc3-105">最も重要な 1 つは、<xref:System.Windows.Forms.Design.Behavior.SnapLine>機能します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-105">One of the most important is the <xref:System.Windows.Forms.Design.Behavior.SnapLine> feature.</span></span>  
  
 <span data-ttu-id="a7dc3-106">スナップ線では、他のコントロールとコントロールを整列する位置を正確を示します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-106">Snaplines show you precisely where to line up controls with other controls.</span></span> <span data-ttu-id="a7dc3-107">Windows ユーザー インターフェイスのガイドラインに従って、コントロール間の余白の推奨距離も示します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-107">They also show you the recommended distances for margins between controls, as specified by the Windows User Interface Guidelines.</span></span> <span data-ttu-id="a7dc3-108">詳細については、「[ユーザー インターフェイスの設計と開発](http://go.microsoft.com/FWLink/?LinkId=83878)です。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-108">For details, see [User Interface Design and Development](http://go.microsoft.com/FWLink/?LinkId=83878).</span></span>  
  
 <span data-ttu-id="a7dc3-109">スナップ線しやすいように、鮮明でコントロールを整列させるプロフェッショナルな外観と動作 (ルック アンド フィール)。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-109">Snaplines make it easy to align your controls, for crisp, professional appearance and behavior (look and feel).</span></span>  
  
 <span data-ttu-id="a7dc3-110">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="a7dc3-111">Windows フォーム プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="a7dc3-111">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="a7dc3-112">スペーシングとスナップ線を使用して、コントロールの配置</span><span class="sxs-lookup"><span data-stu-id="a7dc3-112">Spacing and Aligning Controls Using Snaplines</span></span>  
  
-   <span data-ttu-id="a7dc3-113">フォームまたはコンテナーのマージンに整列</span><span class="sxs-lookup"><span data-stu-id="a7dc3-113">Aligning to Form and Container Margins</span></span>  
  
-   <span data-ttu-id="a7dc3-114">グループ化されたコントロールに合わせて調整</span><span class="sxs-lookup"><span data-stu-id="a7dc3-114">Aligning to Grouped Controls</span></span>  
  
-   <span data-ttu-id="a7dc3-115">スナップ線を使用して、サイズのアウトラインでコントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-115">Using Snaplines to Place a Control by Outlining Its Size</span></span>  
  
-   <span data-ttu-id="a7dc3-116">ツールボックスからコントロールをドラッグしたときに、スナップ線を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-116">Using Snaplines When Dragging a Control from the Toolbox</span></span>  
  
-   <span data-ttu-id="a7dc3-117">スナップ線を使用して、コントロールのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-117">Resizing Controls Using Snaplines</span></span>  
  
-   <span data-ttu-id="a7dc3-118">コントロールのテキストとラベルの整列</span><span class="sxs-lookup"><span data-stu-id="a7dc3-118">Aligning a Label to a Control's Text</span></span>  
  
-   <span data-ttu-id="a7dc3-119">キーボード ナビゲーションをスナップ線を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-119">Using Snaplines with Keyboard Navigation</span></span>  
  
-   <span data-ttu-id="a7dc3-120">スナップ線とレイアウト パネル</span><span class="sxs-lookup"><span data-stu-id="a7dc3-120">Snaplines and Layout Panels</span></span>  
  
-   <span data-ttu-id="a7dc3-121">スナップ線を無効にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-121">Disabling Snaplines</span></span>  
  
 <span data-ttu-id="a7dc3-122">完了したら、レイアウトにスナップ線機能が果たす役割について理解があります。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-122">When you are finished, you will have an understanding of the layout role played by the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7dc3-123">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-123">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a7dc3-124">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-124">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a7dc3-125">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-125">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="a7dc3-126">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="a7dc3-126">Creating the Project</span></span>  
 <span data-ttu-id="a7dc3-127">最初にプロジェクトを作成し、フォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-127">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="a7dc3-128">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-128">To create the project</span></span>  
  
1.  <span data-ttu-id="a7dc3-129">"SnaplineExample"と呼ばれる Windows ベースのアプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-129">Create a Windows-based application project called "SnaplineExample".</span></span> <span data-ttu-id="a7dc3-130">詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-130">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="a7dc3-131">フォーム デザイナーでフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-131">Select the form in the Forms Designer.</span></span>  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a><span data-ttu-id="a7dc3-132">スペーシングとスナップ線を使用して、コントロールの配置</span><span class="sxs-lookup"><span data-stu-id="a7dc3-132">Spacing and Aligning Controls Using Snaplines</span></span>  
 <span data-ttu-id="a7dc3-133">スナップ線では、フォーム上のコントロールを配置するための正確かつ直感的な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-133">Snaplines give you an accurate and intuitive way to align controls on your form.</span></span> <span data-ttu-id="a7dc3-134">別のコントロールやコントロールのセットは整列する位置の近くまたは複数の選択したコントロールを移動するときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-134">They appear when you are moving a selected control or controls near a position that would align with another control or set of controls.</span></span> <span data-ttu-id="a7dc3-135">選択内容は「スナップ」推奨位置に過去の他のコントロールに移動するとします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-135">Your selection will "snap" to the suggested position as you move it past the other controls.</span></span>  
  
#### <a name="to-arrange-controls-using-snaplines"></a><span data-ttu-id="a7dc3-136">スナップ線を使用してコントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-136">To arrange controls using snaplines</span></span>  
  
1.  <span data-ttu-id="a7dc3-137">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-137">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="a7dc3-138">移動、<xref:System.Windows.Forms.Button>フォームの右下隅にコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-138">Move the <xref:System.Windows.Forms.Button> control to the lower-right corner of the form.</span></span> <span data-ttu-id="a7dc3-139">注スナップ線として表示される<xref:System.Windows.Forms.Button>コントロール下およびフォームの右側の境界線のアプローチです。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-139">Note the snaplines that appear as the <xref:System.Windows.Forms.Button> control approaches the bottom and right borders of the form.</span></span> <span data-ttu-id="a7dc3-140">これらのスナップ線は、コントロールの枠線とフォームの推奨される距離を表示します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-140">These snaplines display the recommended distance between the borders of the control and the form.</span></span>  
  
3.  <span data-ttu-id="a7dc3-141">移動、<xref:System.Windows.Forms.Button>注スナップ線が表示される、フォームの境界線を制御します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-141">Move the <xref:System.Windows.Forms.Button> control around the borders of the form and note where the snaplines appear.</span></span> <span data-ttu-id="a7dc3-142">完了したら、移動、<xref:System.Windows.Forms.Button>フォームの中央付近コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-142">When you are finished, move the <xref:System.Windows.Forms.Button> control near the center of the form.</span></span>  
  
4.  <span data-ttu-id="a7dc3-143">別のドラッグ<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-143">Drag another <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
5.  <span data-ttu-id="a7dc3-144">2 番目の移動<xref:System.Windows.Forms.Button>が最初にほぼレベルになるまでを制御します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-144">Move the second <xref:System.Windows.Forms.Button> control until it is nearly level with the first.</span></span> <span data-ttu-id="a7dc3-145">両方のボタンのテキストのベースラインに表示されるスナップ線をメモし、移動中のコントロールが他のコントロールにレベルだけである位置にスナップすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-145">Note the snapline that appears at the text baseline of both buttons, and note that the control you are moving snaps to a position that is exactly level with the other control.</span></span>  
  
6.  <span data-ttu-id="a7dc3-146">2 番目の移動<xref:System.Windows.Forms.Button>最初のすぐ上に配置されるまでを制御します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-146">Move the second <xref:System.Windows.Forms.Button> control until it is positioned directly above the first.</span></span> <span data-ttu-id="a7dc3-147">スナップ線が両方のボタンの左と右の端に表示され、コントロールが他のコントロールを正確に配置される位置に移動のスナップを注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-147">Note the snaplines that appear along the left and right edges of both buttons, and note that the control you are moving snaps to a position that is exactly aligned with the other control.</span></span>  
  
7.  <span data-ttu-id="a7dc3-148">いずれかを選択、<xref:System.Windows.Forms.Button>を制御し、ほぼに触れることまで、その他の近くに移動します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-148">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the other, until they are almost touching.</span></span> <span data-ttu-id="a7dc3-149">それらの間に表示されるスナップ線に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-149">Note the snapline that appears between them.</span></span> <span data-ttu-id="a7dc3-150">推奨される、コントロールの境界線間この距離です。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-150">This distance is the recommended distance between the borders of the controls.</span></span> <span data-ttu-id="a7dc3-151">また、移動中のコントロールがこの位置にスナップすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-151">Also note that the control you are moving snaps to this position.</span></span>  
  
8.  <span data-ttu-id="a7dc3-152">2 つをドラッグして<xref:System.Windows.Forms.Panel>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-152">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto your form.</span></span>  
  
9. <span data-ttu-id="a7dc3-153">いずれかの移動、<xref:System.Windows.Forms.Panel>が最初にほぼレベルになるまでを制御します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-153">Move one of the <xref:System.Windows.Forms.Panel> controls until it is nearly level with the first.</span></span> <span data-ttu-id="a7dc3-154">スナップ線が両方のコントロールの上部と下部の端に沿って表示され、移動中のコントロールが他のコントロールにレベルだけである位置にスナップすることに注意してください。 注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-154">Note the snaplines that appear along the top and bottom edges of both controls, and note that the control you are moving snaps to a position that is exactly level with the other control.</span></span>  
  
## <a name="aligning-to-form-and-container-margins"></a><span data-ttu-id="a7dc3-155">フォームまたはコンテナーのマージンに整列</span><span class="sxs-lookup"><span data-stu-id="a7dc3-155">Aligning to Form and Container Margins</span></span>  
 <span data-ttu-id="a7dc3-156">スナップ線を使用して、一貫した方法でコントロールをフォームやコンテナーのマージンを配置するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-156">Snaplines help you to align your controls to form and container margins in a consistent manner.</span></span>  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a><span data-ttu-id="a7dc3-157">フォームとコンテナーの余白にコントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-157">To align controls to form and container margins</span></span>  
  
1.  <span data-ttu-id="a7dc3-158">いずれかを選択、<xref:System.Windows.Forms.Button>を制御し、スナップ線が表示されるまで、フォームの右罫線の近くに移動します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-158">Select one of the <xref:System.Windows.Forms.Button> controls and move it close to the right border of the form until a snapline appears.</span></span> <span data-ttu-id="a7dc3-159">右罫線のスナップ線の距離は、コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティと、フォームの<xref:System.Windows.Forms.Control.Padding%2A>プロパティの値。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-159">The snapline's distance from the right border is the sum of the control's <xref:System.Windows.Forms.Control.Margin%2A> property and the form's <xref:System.Windows.Forms.Control.Padding%2A> property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7dc3-160">場合、フォームの<xref:System.Windows.Forms.Control.Padding%2A>0,0,0,0 にプロパティが設定されている、Windows フォーム デザイナーは、フォームをシャドウ<xref:System.Windows.Forms.Control.Padding%2A>9,9,9,9 の値。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-160">If the form's <xref:System.Windows.Forms.Control.Padding%2A> property is set to 0,0,0,0, the Windows Forms Designer gives the form a shadowed <xref:System.Windows.Forms.Control.Padding%2A> value of 9,9,9,9.</span></span> <span data-ttu-id="a7dc3-161">この動作をオーバーライドするには、0,0,0,0 以外の値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-161">To override this behavior, assign a value other than 0,0,0,0.</span></span>  
  
1.  <span data-ttu-id="a7dc3-162">値を変更、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Margin%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Margin%2A>内のエントリ、**プロパティ**ウィンドウと設定、<xref:System.Windows.Forms.Padding.All%2A>プロパティを 0 にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-162">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Margin%2A> property by expanding the <xref:System.Windows.Forms.Control.Margin%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 0.</span></span> <span data-ttu-id="a7dc3-163">詳細については、「[チュートリアル: レイアウトを Windows フォーム コントロールを Padding Margin、および AutoSize プロパティ](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-163">For details, see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).</span></span>  
  
2.  <span data-ttu-id="a7dc3-164">移動、<xref:System.Windows.Forms.Button>スナップ線が表示されるまでフォームの右罫線の近くに制御します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-164">Move the <xref:System.Windows.Forms.Button> control close to the right border of the form until a snapline appears.</span></span> <span data-ttu-id="a7dc3-165">この距離は、フォームの値によって指定された<xref:System.Windows.Forms.Control.Padding%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-165">This distance is now given by the value of the form's <xref:System.Windows.Forms.Control.Padding%2A> property.</span></span>  
  
3.  <span data-ttu-id="a7dc3-166">ドラッグ、<xref:System.Windows.Forms.GroupBox>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-166">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="a7dc3-167">値を変更、<xref:System.Windows.Forms.GroupBox>コントロールの<xref:System.Windows.Forms.Control.Padding%2A>プロパティを展開して、<xref:System.Windows.Forms.Control.Padding%2A>内のエントリ、**プロパティ**ウィンドウと設定、 <xref:System.Windows.Forms.Padding.All%2A> 10 プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-167">Change the value of the <xref:System.Windows.Forms.GroupBox> control's <xref:System.Windows.Forms.Control.Padding%2A> property by expanding the <xref:System.Windows.Forms.Control.Padding%2A> entry in the **Properties** window and setting the <xref:System.Windows.Forms.Padding.All%2A> property to 10.</span></span>  
  
5.  <span data-ttu-id="a7dc3-168">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**に、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-168">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
6.  <span data-ttu-id="a7dc3-169">移動、<xref:System.Windows.Forms.Button>の右側の境界線に近いコントロール、<xref:System.Windows.Forms.GroupBox>スナップ線が表示されるまでを制御します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-169">Move the <xref:System.Windows.Forms.Button> control close to the right border of the <xref:System.Windows.Forms.GroupBox> control until a snapline appears.</span></span> <span data-ttu-id="a7dc3-170">移動、<xref:System.Windows.Forms.Button>内の制御、<xref:System.Windows.Forms.GroupBox>コントロールと、スナップ線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-170">Move the <xref:System.Windows.Forms.Button> control within the <xref:System.Windows.Forms.GroupBox> control and note where the snaplines appear.</span></span>  
  
## <a name="aligning-to-grouped-controls"></a><span data-ttu-id="a7dc3-171">グループ化されたコントロールに合わせて調整</span><span class="sxs-lookup"><span data-stu-id="a7dc3-171">Aligning to Grouped Controls</span></span>  
 <span data-ttu-id="a7dc3-172">グループ化されたコントロールを配置するスナップ線を使用することができます内で制御と同様、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-172">You can use snaplines to align grouped controls as well as controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
#### <a name="to-align-to-grouped-controls"></a><span data-ttu-id="a7dc3-173">グループ化されたコントロールに合わせて調整するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-173">To align to grouped controls</span></span>  
  
1.  <span data-ttu-id="a7dc3-174">フォーム上のコントロールの 2 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-174">Select two of the controls on your form.</span></span> <span data-ttu-id="a7dc3-175">選択範囲を移動し、選択内容とその他のコントロール間に表示されるスナップ ラインに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-175">Move the selection around and note the snaplines that appear between your selection and the other controls.</span></span>  
  
2.  <span data-ttu-id="a7dc3-176">ドラッグ、<xref:System.Windows.Forms.GroupBox>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-176">Drag a <xref:System.Windows.Forms.GroupBox> control from the **Toolbox** onto your form.</span></span>  
  
3.  <span data-ttu-id="a7dc3-177">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**に、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-177">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the <xref:System.Windows.Forms.GroupBox> control.</span></span>  
  
4.  <span data-ttu-id="a7dc3-178">いずれかを選択、<xref:System.Windows.Forms.Button>を制御し、移動、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-178">Select one of the <xref:System.Windows.Forms.Button> controls and move it around the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a7dc3-179">注スナップ線の端に表示される<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-179">Note the snaplines that appear at the edges of the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a7dc3-180">なお、スナップ線の端に表示されますが、<xref:System.Windows.Forms.Button>コントロールに含まれています、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-180">Also note the snaplines that appear at the edges of the <xref:System.Windows.Forms.Button> control that is contained by the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a7dc3-181">コンテナー コントロールの子であるコントロールでは、スナップ線もサポートします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-181">Controls that are children of a container control also support snaplines.</span></span>  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a><span data-ttu-id="a7dc3-182">スナップ線を使用して、サイズのアウトラインでコントロールを配置するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-182">Using Snaplines to Place a Control by Outlining Its Size</span></span>  
 <span data-ttu-id="a7dc3-183">スナップ線に整列させることは、ときに最初に配置するにフォームを制御します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-183">Snaplines help you align controls when you first place them on a form.</span></span>  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a><span data-ttu-id="a7dc3-184">によって、サイズのアウトライン コントロールを配置するスナップ線を使用するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-184">To use snaplines to place a control by outlining its size</span></span>  
  
1.  <span data-ttu-id="a7dc3-185">**ツールボックス**で <xref:System.Windows.Forms.Button> コントロール アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-185">In the **Toolbox**, click the <xref:System.Windows.Forms.Button> control icon.</span></span> <span data-ttu-id="a7dc3-186">フォームにドラッグしないでください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-186">Do not drag it onto the form.</span></span>  
  
2.  <span data-ttu-id="a7dc3-187">フォームのデザイン画面上には、マウス ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-187">Move the mouse pointer over the form's design surface.</span></span> <span data-ttu-id="a7dc3-188">ポインターが <xref:System.Windows.Forms.Button> コントロール アイコンが付いた十字カーソルに変わることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-188">Note that the pointer changes to a crosshair with the <xref:System.Windows.Forms.Button> control icon attached.</span></span> <span data-ttu-id="a7dc3-189">なお、表示されるスナップ ラインの位置を揃えるを提案する、<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-189">Also note the snaplines that appear to suggest aligned positions for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
3.  <span data-ttu-id="a7dc3-190">マウス ボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-190">Click and hold the mouse button.</span></span>  
  
4.  <span data-ttu-id="a7dc3-191">フォーム上のマウス ポインターをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-191">Drag the mouse pointer around the form.</span></span> <span data-ttu-id="a7dc3-192">アウトラインを描画すること、位置、およびコントロールのサイズを示すに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-192">Note that an outline is drawn, indicating the position and the size of the control.</span></span>  
  
5.  <span data-ttu-id="a7dc3-193">フォーム上の別のコントロールと揃うまでドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-193">Drag the pointer until it aligns with another control on the form.</span></span> <span data-ttu-id="a7dc3-194">整列を示すスナップ線が表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-194">Note that a snapline appears to indicate alignment.</span></span>  
  
6.  <span data-ttu-id="a7dc3-195">マウスのボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-195">Release the mouse button.</span></span> <span data-ttu-id="a7dc3-196">アウトラインで示されるサイズと位置にコントロールを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-196">The control is created at the position and size indicated by the outline.</span></span>  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a><span data-ttu-id="a7dc3-197">ツールボックスからコントロールをドラッグしたときに、スナップ線を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-197">Using Snaplines When Dragging a Control from the Toolbox</span></span>  
 <span data-ttu-id="a7dc3-198">スナップ線に整列させることを制御からそれらをドラッグすると、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-198">Snaplines help you align controls when you drag them from the **Toolbox** onto your form.</span></span>  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a><span data-ttu-id="a7dc3-199">ツールボックスからコントロールをドラッグするときに、スナップ線を使用するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-199">To use snaplines when dragging a control from the Toolbox</span></span>  
  
1.  <span data-ttu-id="a7dc3-200">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にマウス ボタンを押したままです。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-200">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form, but do not release the mouse button.</span></span>  
  
2.  <span data-ttu-id="a7dc3-201">フォームのデザイン画面上には、マウス ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-201">Move the mouse pointer over the form's design surface.</span></span> <span data-ttu-id="a7dc3-202">位置を示すために、ポインターを変更ことに注意してください。 新しい<xref:System.Windows.Forms.Button>コントロールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-202">Note that the pointer changes to indicate the position at which the new <xref:System.Windows.Forms.Button> control will be created.</span></span>  
  
3.  <span data-ttu-id="a7dc3-203">フォーム上のマウス ポインターをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-203">Drag the mouse pointer around the form.</span></span> <span data-ttu-id="a7dc3-204">位置を揃えるに表示されるスナップ線に注意してください、<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-204">Note the snaplines that appear to suggest aligned positions for the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="a7dc3-205">その他のコントロールと整合する位置を検索します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-205">Find a position that is aligned with other controls.</span></span>  
  
4.  <span data-ttu-id="a7dc3-206">マウスのボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-206">Release the mouse button.</span></span> <span data-ttu-id="a7dc3-207">スナップ線によって示される位置にあるコントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-207">The control is created at the position indicated by the snaplines.</span></span>  
  
## <a name="resizing-controls-using-snaplines"></a><span data-ttu-id="a7dc3-208">スナップ線を使用して、コントロールのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-208">Resizing Controls Using Snaplines</span></span>  
 <span data-ttu-id="a7dc3-209">スナップ線を使用するようにサイズ変更してコントロールを配置します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-209">Snaplines help you align controls as you resize them.</span></span>  
  
#### <a name="to-resize-a-control-using-snaplines"></a><span data-ttu-id="a7dc3-210">スナップ線を使用して、コントロールのサイズを変更するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-210">To resize a control using snaplines</span></span>  
  
1.  <span data-ttu-id="a7dc3-211">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-211">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="a7dc3-212">サイズ変更、<xref:System.Windows.Forms.Button>上隅をドラッグしてサイズ変更ハンドルのいずれかを行ったによって制御します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-212">Resize the <xref:System.Windows.Forms.Button> control by grabbing one of the corner sizing handles and dragging.</span></span> <span data-ttu-id="a7dc3-213">詳細については、「[する方法: Windows フォームでのコントロールのサイズを変更する](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-213">For details, see [How to: Resize Controls on Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).</span></span>  
  
3.  <span data-ttu-id="a7dc3-214">1 つまでのサイズ変更ハンドルをドラッグして、<xref:System.Windows.Forms.Button>コントロールの枠線が別のコントロールに揃えて配置します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-214">Drag the sizing handle until one of the <xref:System.Windows.Forms.Button> control's borders is aligned with another control.</span></span> <span data-ttu-id="a7dc3-215">スナップ線が表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-215">Note that a snapline appears.</span></span> <span data-ttu-id="a7dc3-216">また、サイズ変更ハンドルがスナップ線によって示される位置にスナップすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-216">Also note that the sizing handle snaps to the position indicated by the snapline.</span></span>  
  
4.  <span data-ttu-id="a7dc3-217">サイズ変更、<xref:System.Windows.Forms.Button>いろいろな方向を制御し、さまざまなコントロールをサイズ変更ハンドルを揃えます。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-217">Resize the <xref:System.Windows.Forms.Button> control in different directions and align the sizing handle to different controls.</span></span> <span data-ttu-id="a7dc3-218">配置を示すためにさまざまな向きでスナップ線を表示する方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-218">Note how the snaplines appear in various orientations to indicate alignment.</span></span>  
  
## <a name="aligning-a-label-to-a-controls-text"></a><span data-ttu-id="a7dc3-219">コントロールのテキストとラベルの整列</span><span class="sxs-lookup"><span data-stu-id="a7dc3-219">Aligning a Label to a Control's Text</span></span>  
 <span data-ttu-id="a7dc3-220">一部のコントロールは、他のコントロールに表示されるテキストを配置するスナップ線を提供します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-220">Some controls offer a snapline for aligning other controls to displayed text.</span></span>  
  
#### <a name="to-align-a-label-to-a-controls-text"></a><span data-ttu-id="a7dc3-221">コントロールのテキストにラベルを整列するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-221">To align a label to a control's text</span></span>  
  
1.  <span data-ttu-id="a7dc3-222">ドラッグ、<xref:System.Windows.Forms.TextBox>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-222">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="a7dc3-223">ドロップすると、<xref:System.Windows.Forms.TextBox>フォーム上に制御し、スマート タグ グリフをクリックし、選択、 **textBox1 にテキストを設定**オプション。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-223">When you drop the <xref:System.Windows.Forms.TextBox> control onto the form, click the smart-tag glyph and select the **Set text to textBox1** option.</span></span> <span data-ttu-id="a7dc3-224">詳細については、「[チュートリアル: を実行する一般的なタスクを使用してスマート タグに Windows フォーム コントロール](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-224">For details, see [Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).</span></span>  
  
2.  <span data-ttu-id="a7dc3-225">ドラッグ、<xref:System.Windows.Forms.Label>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-225">Drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto your form.</span></span>  
  
3.  <span data-ttu-id="a7dc3-226"><xref:System.Windows.Forms.Label> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値を `true` に変更します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-226">Change the value of the <xref:System.Windows.Forms.Label> control's <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="a7dc3-227">表示テキストに合わせてコントロールの枠線を調整することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-227">Note that the control's borders are adjusted to fit the display text.</span></span>  
  
4.  <span data-ttu-id="a7dc3-228">移動、<xref:System.Windows.Forms.Label>コントロールの左側に、<xref:System.Windows.Forms.TextBox>を制御するための下部エッジに揃えられます、<xref:System.Windows.Forms.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-228">Move the <xref:System.Windows.Forms.Label> control to the left of the <xref:System.Windows.Forms.TextBox> control, so it is aligned with the bottom edge of the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="a7dc3-229">2 つのコントロールの下端に沿って表示されるスナップ線に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-229">Note the snapline that appears along the bottom edges of the two controls.</span></span>  
  
5.  <span data-ttu-id="a7dc3-230">移動、<xref:System.Windows.Forms.Label>コントロールまで、少し上昇、<xref:System.Windows.Forms.Label>テキストと<xref:System.Windows.Forms.TextBox>テキストを配置します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-230">Move the <xref:System.Windows.Forms.Label> control slightly upward, until the <xref:System.Windows.Forms.Label> text and the <xref:System.Windows.Forms.TextBox> text are aligned.</span></span> <span data-ttu-id="a7dc3-231">スタイルの異なるスナップ線が表示されたら、両方のコントロールのテキスト フィールドを配置するときを示すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-231">Note the differently styled snapline that appears, indicating when the text fields of both controls are aligned.</span></span>  
  
## <a name="using-snaplines-with-keyboard-navigation"></a><span data-ttu-id="a7dc3-232">キーボード ナビゲーションをスナップ線を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-232">Using Snaplines with Keyboard Navigation</span></span>  
 <span data-ttu-id="a7dc3-233">スナップ線に整列させることは、配置、キーボードの矢印キーを使用するを制御します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-233">Snaplines help you align controls when you are arranging them using the keyboard's arrow keys.</span></span>  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a><span data-ttu-id="a7dc3-234">キーボード ナビゲーションをスナップ線を使用するには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-234">To use snaplines with keyboard navigation</span></span>  
  
1.  <span data-ttu-id="a7dc3-235">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-235">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto your form.</span></span> <span data-ttu-id="a7dc3-236">フォームの左上隅に配置します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-236">Place it in the upper-left corner of the form.</span></span>  
  
2.  <span data-ttu-id="a7dc3-237">Ctrl キーを押しながら下方向のキーを押します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-237">Press CTRL+DOWN ARROW.</span></span> <span data-ttu-id="a7dc3-238">コントロールが最初の使用可能な水平方向の配置位置をフォーム下へ移動することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-238">Note that the control moves down the form to the first available horizontal alignment position.</span></span>  
  
3.  <span data-ttu-id="a7dc3-239">コントロールがフォームの下部に達するまで、ctrl キーを押しながら下方向キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-239">Press CTRL+DOWN ARROW until the control reaches the bottom of the form.</span></span> <span data-ttu-id="a7dc3-240">フォームの下方向に移動するときに占有する位置に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-240">Note the positions it occupies as it moves down the form.</span></span>  
  
4.  <span data-ttu-id="a7dc3-241">Ctrl キーを押しながら右方向のキーを押します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-241">Press CTRL+RIGHT ARROW.</span></span> <span data-ttu-id="a7dc3-242">コントロールをフォーム上で最初の使用可能な縦方向の配置位置を移動するに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-242">Note that the control moves across the form to the first available vertical alignment position.</span></span>  
  
5.  <span data-ttu-id="a7dc3-243">コントロールがフォームの端に達するまで、ctrl キーを押しながら右方向キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-243">Press CTRL+RIGHT ARROW until the control reaches the side of the form.</span></span> <span data-ttu-id="a7dc3-244">フォーム全体を移動する際に占有する位置に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-244">Note the positions it occupies as it moves across the form.</span></span>  
  
6.  <span data-ttu-id="a7dc3-245">方向キーの組み合わせでコントロールをフォーム上を移動します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-245">Move the control around the form with a combination of arrow keys.</span></span> <span data-ttu-id="a7dc3-246">コントロールが占める位置とそれに伴うスナップ線に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-246">Note the positions the control occupies and the snaplines that accompany them.</span></span>  
  
7.  <span data-ttu-id="a7dc3-247">サイズを変更するには、shift キーを押しながら任意の方向キーを押して、 <xref:System.Windows.Forms.Button> 1 ピクセルずつコントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-247">Press SHIFT+any arrow key to resize the <xref:System.Windows.Forms.Button> control by increments of one pixel.</span></span>  
  
8.  <span data-ttu-id="a7dc3-248">サイズを変更するには、CTRL + SHIFT + 任意の方向キーを押して、<xref:System.Windows.Forms.Button>スナップ線単位で制御します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-248">Press CTRL+SHIFT+any arrow key to resize the <xref:System.Windows.Forms.Button> control in snapline increments.</span></span>  
  
## <a name="snaplines-and-layout-panels"></a><span data-ttu-id="a7dc3-249">スナップ線とレイアウト パネル</span><span class="sxs-lookup"><span data-stu-id="a7dc3-249">Snaplines and Layout Panels</span></span>  
 <span data-ttu-id="a7dc3-250">レイアウト パネル内では、スナップ線が無効になります。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-250">Snaplines are disabled within layout panels.</span></span>  
  
#### <a name="to-selectively-disable-snaplines"></a><span data-ttu-id="a7dc3-251">スナップ線を選択的に無効にするには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-251">To selectively disable snaplines</span></span>  
  
1.  <span data-ttu-id="a7dc3-252">ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-252">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="a7dc3-253"><xref:System.Windows.Forms.Button> ツールボックス **の**コントロール アイコンをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-253">Double-click the <xref:System.Windows.Forms.Button> control icon in the **Toolbox**.</span></span> <span data-ttu-id="a7dc3-254">新しいボタン コントロールが含まれているメモ、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの最初のセル。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-254">Note that a new button control appears in the <xref:System.Windows.Forms.TableLayoutPanel> control's first cell.</span></span>  
  
3.  <span data-ttu-id="a7dc3-255">ダブルクリックして、<xref:System.Windows.Forms.Button>コントロールのアイコン、**ツールボックス**さらに 2 回です。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-255">Double-click the <xref:System.Windows.Forms.Button> control icon in the **Toolbox** twice more.</span></span> <span data-ttu-id="a7dc3-256">これにより、1 つの空のセル、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-256">This leaves one empty cell in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="a7dc3-257">ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**の空のセルに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-257">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the empty cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="a7dc3-258">スナップ線が表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-258">Note that no snaplines appear.</span></span>  
  
5.  <span data-ttu-id="a7dc3-259">ドラッグ、<xref:System.Windows.Forms.Button>の制御、<xref:System.Windows.Forms.TableLayoutPanel>を制御し、移動、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-259">Drag the <xref:System.Windows.Forms.Button> control out of the <xref:System.Windows.Forms.TableLayoutPanel> control and move it around the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="a7dc3-260">スナップ線が再度表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-260">Note that snaplines appear again.</span></span>  
  
## <a name="disabling-snaplines"></a><span data-ttu-id="a7dc3-261">スナップ線を無効にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-261">Disabling Snaplines</span></span>  
 <span data-ttu-id="a7dc3-262">スナップ ガイドラインは、既定で有効にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-262">Snaplines are turned on by default.</span></span> <span data-ttu-id="a7dc3-263">スナップ線を選択的に、無効にできますか、デザイン環境で無効にできます。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-263">You can disable snaplines selectively, or you can disable them in the design environment.</span></span>  
  
#### <a name="to-selectively-disable-snaplines"></a><span data-ttu-id="a7dc3-264">スナップ線を選択的に無効にするには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-264">To selectively disable snaplines</span></span>  
  
-   <span data-ttu-id="a7dc3-265">ALT キーを押して、コントロールをフォーム上の移動中にします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-265">Press the ALT key and while moving a control around the form.</span></span>  
  
     <span data-ttu-id="a7dc3-266">スナップ線が表示されませんが、コントロールが潜在的な配置位置にスナップいないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-266">Note that no snaplines appear and the control does not snap to any potential alignment positions.</span></span>  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a><span data-ttu-id="a7dc3-267">デザイン環境のスナップ線を無効にするには</span><span class="sxs-lookup"><span data-stu-id="a7dc3-267">To disable snaplines in the design environment</span></span>  
  
1.  <span data-ttu-id="a7dc3-268">**ツール**メニューを開き、**オプション** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-268">From the **Tools** menu, open the **Options** dialog box.</span></span> <span data-ttu-id="a7dc3-269">Windows フォーム デザイナー ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-269">Open the Windows Forms Designer dialog box.</span></span> <span data-ttu-id="a7dc3-270">詳細については、「 [[全般]、Windows フォーム デザイナー、オプション ダイアログ ボックス](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834)です。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-270">For details, see [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834).</span></span>  
  
2.  <span data-ttu-id="a7dc3-271">選択、**全般**ノード。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-271">Select the **General** node.</span></span> <span data-ttu-id="a7dc3-272">**レイアウト モード**セクションからの選択を変更**スナップ線**に**SnapToGrid**です。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-272">In the **Layout Mode** section, change the selection from **SnapLines** to **SnapToGrid**.</span></span>  
  
3.  <span data-ttu-id="a7dc3-273">設定を適用するには、[ok] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-273">Click OK to apply the setting.</span></span>  
  
4.  <span data-ttu-id="a7dc3-274">フォーム上のコントロールを選択し、その他のコントロールを移動します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-274">Select a control on your form and move it around the other controls.</span></span> <span data-ttu-id="a7dc3-275">スナップ線が表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-275">Note that snaplines do not appear.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a7dc3-276">次の手順</span><span class="sxs-lookup"><span data-stu-id="a7dc3-276">Next Steps</span></span>  
 <span data-ttu-id="a7dc3-277">スナップ ガイドラインは、直観的に、フォームのコントロールの配置を提供します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-277">Snaplines offer an intuitive means of aligning controls on your form.</span></span> <span data-ttu-id="a7dc3-278">さらに詳しく調べるための推奨事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-278">Suggestions for more exploration include:</span></span>  
  
-   <span data-ttu-id="a7dc3-279">入れ子の再試行、<xref:System.Windows.Forms.GroupBox>中に別のコントロール<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-279">Try nesting a <xref:System.Windows.Forms.GroupBox> control within another <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a7dc3-280">場所、<xref:System.Windows.Forms.Button>子内のコントロール<xref:System.Windows.Forms.GroupBox>制御、および親内の別<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-280">Place a <xref:System.Windows.Forms.Button> control within the child <xref:System.Windows.Forms.GroupBox> control, and another within the parent <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a7dc3-281">移動、<xref:System.Windows.Forms.Button>スナップ線がコンテナーの境界を越える方法を表示するには、約コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-281">Move the <xref:System.Windows.Forms.Button> controls around to see how the snaplines cross container boundaries.</span></span>  
  
-   <span data-ttu-id="a7dc3-282">列を作成<xref:System.Windows.Forms.TextBox>コントロールとの対応する列<xref:System.Windows.Forms.Label>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-282">Create a column of <xref:System.Windows.Forms.TextBox> controls and a corresponding column of <xref:System.Windows.Forms.Label> controls.</span></span> <span data-ttu-id="a7dc3-283">値を設定、<xref:System.Windows.Forms.Label>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-283">Set the value of the <xref:System.Windows.Forms.Label> controls' <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="a7dc3-284">移動するスナップ線を使用して、<xref:System.Windows.Forms.Label>ためのテキストに、表示されるテキストの配置を制御、<xref:System.Windows.Forms.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-284">Use snaplines to move the <xref:System.Windows.Forms.Label> controls so their displayed text is aligned with the text in the <xref:System.Windows.Forms.TextBox> controls.</span></span>  
  
 <span data-ttu-id="a7dc3-285">Windows ユーザー インターフェイスの設計方法については、ブックを参照してください。 *Microsoft Windows ユーザー エクスペリエンス、ユーザー インターフェイスの開発者とデザイナーの Official Guidelines* Redmond、WA: Microsoft Press、1999 年。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-285">For information about Windows user interface design, see the book *Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers* Redmond, WA: Microsoft Press, 1999.</span></span> <span data-ttu-id="a7dc3-286">(USBN: 0-7356-0566-1)。</span><span class="sxs-lookup"><span data-stu-id="a7dc3-286">(USBN: 0-7356-0566-1).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7dc3-287">参照</span><span class="sxs-lookup"><span data-stu-id="a7dc3-287">See Also</span></span>  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [<span data-ttu-id="a7dc3-288">チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="a7dc3-288">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="a7dc3-289">チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="a7dc3-289">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="a7dc3-290">チュートリアル : Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト</span><span class="sxs-lookup"><span data-stu-id="a7dc3-290">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [<span data-ttu-id="a7dc3-291">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="a7dc3-291">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
