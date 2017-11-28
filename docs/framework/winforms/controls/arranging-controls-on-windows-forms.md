---
title: "Windows フォームでのコントロールの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VisualSelection
helpviewer_keywords:
- controls [Windows Forms], positioning
- Windows Forms controls, positioning on form
ms.assetid: b2d62ed8-c391-4a7e-b72e-6bbabfca73dc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5709f07edc90b9094561870d31fbe28697974ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="arranging-controls-on-windows-forms"></a><span data-ttu-id="de73e-102">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="de73e-102">Arranging Controls on Windows Forms</span></span>
<span data-ttu-id="de73e-103">さまざまな方法でフォームにコントロールを配置したり、フォームのコントロールを操作したりすることで、ユーザーが直観的に操作できる機能的なユーザー インターフェイスを構築できます。</span><span class="sxs-lookup"><span data-stu-id="de73e-103">By placing and manipulating controls on forms in different ways, you can create user interfaces that are both intuitive and functional for users.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de73e-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="de73e-104">In This Section</span></span>  
 [<span data-ttu-id="de73e-105">方法 : Windows フォーム上の複数のコントロールを配置する</span><span class="sxs-lookup"><span data-stu-id="de73e-105">How to: Align Multiple Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-align-multiple-controls-on-windows-forms.md)  
 <span data-ttu-id="de73e-106">Windows フォーム上のさまざまなコントロールの位置を揃える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-106">Gives directions for lining up the position of a number of controls on your Windows Form.</span></span>  
  
 [<span data-ttu-id="de73e-107">方法 : Windows フォームにコントロールを固定する</span><span class="sxs-lookup"><span data-stu-id="de73e-107">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 <span data-ttu-id="de73e-108">実行時にサイズを動的に変更するコントロールの設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-108">Gives directions for setting controls to resize dynamically at run time.</span></span>  
  
 [<span data-ttu-id="de73e-109">方法 : Windows フォーム間でコントロールをコピーする</span><span class="sxs-lookup"><span data-stu-id="de73e-109">How to: Copy Controls Between Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 <span data-ttu-id="de73e-110">フォーム間でコントロールを複製する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-110">Gives directions for duplicating controls between forms.</span></span>  
  
 [<span data-ttu-id="de73e-111">方法 : Windows フォーム上のコントロールをドッキングする</span><span class="sxs-lookup"><span data-stu-id="de73e-111">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 <span data-ttu-id="de73e-112">フォームの横にコントロールを "貼り付ける" 方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-112">Gives directions for making controls "stick" to the side(s) of a form.</span></span>  
  
 [<span data-ttu-id="de73e-113">方法 : Windows フォーム上のオブジェクトをレイヤー化する</span><span class="sxs-lookup"><span data-stu-id="de73e-113">How to: Layer Objects on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md)  
 <span data-ttu-id="de73e-114">Z 軸に対して上に置くコントロールを決定する方法について説明します (重ね順)。</span><span class="sxs-lookup"><span data-stu-id="de73e-114">Gives directions for establishing which controls are on top relative to the z-axis (z-order).</span></span>  
  
 [<span data-ttu-id="de73e-115">方法 : Windows フォームにコントロールをロックする</span><span class="sxs-lookup"><span data-stu-id="de73e-115">How to: Lock Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md)  
 <span data-ttu-id="de73e-116">フォームにコントロールを完全に固定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-116">Gives directions for fastening controls permanently to the form.</span></span>  
  
 [<span data-ttu-id="de73e-117">方法 : Windows フォーム上のコントロールを位置設定する</span><span class="sxs-lookup"><span data-stu-id="de73e-117">How to: Position Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-position-controls-on-windows-forms.md)  
 <span data-ttu-id="de73e-118">フォーム上のコントロールの座標を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-118">Gives directions for setting the coordinates of the controls on a form.</span></span>  
  
 [<span data-ttu-id="de73e-119">方法 : Windows フォーム上のコントロールのサイズを変更する</span><span class="sxs-lookup"><span data-stu-id="de73e-119">How to: Resize Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 <span data-ttu-id="de73e-120">フォーム上のコントロールのサイズを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-120">Gives directions for setting the size of controls on a form.</span></span>  
  
 [<span data-ttu-id="de73e-121">方法 : すべての Windows フォームにグリッド オプションを設定する</span><span class="sxs-lookup"><span data-stu-id="de73e-121">How to: Set Grid Options for All Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-set-grid-options-for-all-windows-forms.md)  
 <span data-ttu-id="de73e-122">フォームを覆うグリッドのサイズを調整する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-122">Gives directions for calibrating the size of the grid that covers a form.</span></span>  
  
 [<span data-ttu-id="de73e-123">方法 : Windows フォーム上のタブ オーダーを設定する</span><span class="sxs-lookup"><span data-stu-id="de73e-123">How to: Set the Tab Order on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-tab-order-on-windows-forms.md)  
 <span data-ttu-id="de73e-124">TAB キーを押したとき、コントロールのフォーカスが移動する順序を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-124">Gives directions for regulating the order in which controls will have focus when the user presses TAB.</span></span>  
  
 [<span data-ttu-id="de73e-125">方法 : コントロールを Windows フォームのスナップ線とグリッドを使用して配置する</span><span class="sxs-lookup"><span data-stu-id="de73e-125">How to: Arrange Controls with Snaplines and the Grid in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-arrange-controls-with-snaplines-and-the-grid-in-windows-forms.md)  
 <span data-ttu-id="de73e-126">フォーム上のグリッドにコントロールを貼る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-126">Gives directions for affixing controls to the grid on a form.</span></span>  
  
 [<span data-ttu-id="de73e-127">方法 : 既存のコントロールを別の親に再配置する</span><span class="sxs-lookup"><span data-stu-id="de73e-127">How to: Reassign Existing Controls to a Different Parent</span></span>](../../../../docs/framework/winforms/controls/how-to-reassign-existing-controls-to-a-different-parent.md)  
 <span data-ttu-id="de73e-128">新しい親コンテナーに既存のコントロールを割り当てる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-128">Gives directions for assigning existing controls to a new parent container.</span></span>  
  
 [<span data-ttu-id="de73e-129">チュートリアル: Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト</span><span class="sxs-lookup"><span data-stu-id="de73e-129">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 <span data-ttu-id="de73e-130">使用して、フォーム上のコントロールを配置する方法について説明します、 <xref:System.Windows.Forms.Control.Margin%2A>、 <xref:System.Windows.Forms.Control.Padding%2A>、および<xref:System.Windows.Forms.Control.AutoSize%2A>内のプロパティ、**フォーム デザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="de73e-130">Describes how you can place controls on your forms by using the <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, and <xref:System.Windows.Forms.Control.AutoSize%2A> properties within the **Forms Designer**.</span></span>  
  
 [<span data-ttu-id="de73e-131">チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="de73e-131">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 <span data-ttu-id="de73e-132">スナップ線で実行するさまざまなレイアウト ロールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-132">Demonstrates the various layout roles fulfilled by snaplines.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="de73e-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="de73e-133">Related Sections</span></span>  
 [<span data-ttu-id="de73e-134">方法 : デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="de73e-134">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 <span data-ttu-id="de73e-135">フォームを取り消すためのコントロールとしてボタンを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-135">Gives directions for establishing a button as the control to cancel the form.</span></span>  
  
 [<span data-ttu-id="de73e-136">方法 : デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="de73e-136">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 <span data-ttu-id="de73e-137">ダイアログ ボックス内のそのときのフォーカス位置に関係なく、ENTER キーを押したとき、"入力受付" ボタンとしてボタン (多くの場合、"OK" ボタン) を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-137">Gives directions for establishing a button (often an "OK" button) as the "accept input" button when ENTER is pressed regardless of where focus is at the time in the dialog box.</span></span>  
  
 [<span data-ttu-id="de73e-138">方法 : セットとして機能する Windows フォーム RadioButton コントロールをグループ化する</span><span class="sxs-lookup"><span data-stu-id="de73e-138">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)  
 <span data-ttu-id="de73e-139">互いに関連するものとして `RadioButton` コントロールのセットを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de73e-139">Gives directions for establishing a set of `RadioButton` controls as being related to one another.</span></span>  
  
 [<span data-ttu-id="de73e-140">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="de73e-140">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="de73e-141">コントロールに関する一般的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="de73e-141">Provides general information about controls.</span></span>
