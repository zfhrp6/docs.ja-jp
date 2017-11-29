---
title: "組み込みのオーナー描画サポートを備えたコントロール"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8fb699a93effcdf0b5f88606419479d51754125b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="da085-102">組み込みのオーナー描画サポートを備えたコントロール</span><span class="sxs-lookup"><span data-stu-id="da085-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="da085-103">Windows フォームのオーナー描画 (カスタム描画とも呼ばれます) は、特定のコントロールの外観を変更するための手法です。</span><span class="sxs-lookup"><span data-stu-id="da085-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da085-104">このトピックでは、「コントロール」という単語がいずれかから派生したクラスのことを意味する使用<xref:System.Windows.Forms.Control>または<xref:System.ComponentModel.Component>です。</span><span class="sxs-lookup"><span data-stu-id="da085-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="da085-105">通常、Windows の描画を自動的に処理などのプロパティ設定を使用して<xref:System.Windows.Forms.Control.BackColor%2A>をコントロールの外観を決定します。</span><span class="sxs-lookup"><span data-stu-id="da085-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="da085-106">オーナー描画では、描画プロセスを引き継いで、プロパティでは設定できない外観の要素を変更できます。</span><span class="sxs-lookup"><span data-stu-id="da085-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="da085-107">たとえば、多くのコントロールでは表示されるテキストの色を設定できますが、1 つの色に制限されます。</span><span class="sxs-lookup"><span data-stu-id="da085-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="da085-108">オーナー描画では、テキストの一部分を黒で表示し、別の部分を赤で表示する、といったことができます。</span><span class="sxs-lookup"><span data-stu-id="da085-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="da085-109">実際には、オーナー描画はフォームでのグラフィックスの描画に似ています。</span><span class="sxs-lookup"><span data-stu-id="da085-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="da085-110">フォームのなどのハンドラーでグラフィックス メソッドを使用する可能性があります<xref:System.Windows.Forms.Control.Paint>をエミュレートするイベント、`ListBox`コントロールですはすべてのユーザー操作を処理するコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da085-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="da085-111">オーナー描画では、コントロールは独自のコードを使って内容を描画しますが、それ以外については組み込み機能がすべて保持されます。</span><span class="sxs-lookup"><span data-stu-id="da085-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="da085-112">グラフィックス メソッドを使うと、コントロール内の各項目を描画したり、各項目の一部だけカスタマイズして他の部分は既定の外観を使ったりすることができます。</span><span class="sxs-lookup"><span data-stu-id="da085-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="da085-113">Windows フォーム コントロールでのオーナー描画</span><span class="sxs-lookup"><span data-stu-id="da085-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="da085-114">オーナー描画をサポートしているコントロールでオーナー描画を実行するには、通常、1 つのプロパティを設定し、1 つまたは複数のイベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="da085-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="da085-115">オーナー描画をサポートしているほとんどのコントロールには、コントロールの描画時に描画関連のイベントが発生するかどうかを示す `OwnerDraw` または `DrawMode` プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="da085-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="da085-116">`OwnerDraw` または `DrawMode` プロパティを持たないコントロールには、自動的に発生する描画イベントを提供する `DataGridView` コントロールと、独自の描画関連イベントを持つ外部レンダリング クラスを使って描画される `ToolStrip` コントロールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="da085-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="da085-117">さまざまな種類の描画イベントがありますが、標準的な描画イベントはコントロール内の 1 つの項目を描画するために発生します。</span><span class="sxs-lookup"><span data-stu-id="da085-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="da085-118">イベント ハンドラーは、描画される項目に関する情報と、その描画に使用できるツールを含む、`EventArgs` オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="da085-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="da085-119">このオブジェクトが通常、その親コレクション内の項目のインデックス番号を含むなど、<xref:System.Drawing.Rectangle>アイテムの表示の境界を示す、<xref:System.Drawing.Graphics>ペイント メソッドを呼び出すためのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="da085-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="da085-120">一部のイベントの `EventArgs` オブジェクトでは、項目に関する追加情報と、背景やフォーカス四角形などの項目の一部分を既定で描画するために呼び出すことができるメソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="da085-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="da085-121">オーナー描画のカスタマイズを含む再利用可能なコントロールを作成するには、オーナー描画をサポートするコントロール クラスから派生する新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="da085-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="da085-122">描画イベントを処理するのではなく、新しいクラスの適切な `On`<*イベント名*> メソッドのオーバーライドにオーナー描画のコードを組み込みます。</span><span class="sxs-lookup"><span data-stu-id="da085-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="da085-123">この場合、コントロールのユーザーがオーナー描画イベントを処理して追加のカスタマイズを提供できるように、基底クラスの `On`<*イベント名*> メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="da085-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="da085-124">次の Windows フォーム コントロールは、すべてのバージョンの .NET Framework でオーナー描画をサポートします。</span><span class="sxs-lookup"><span data-stu-id="da085-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <span data-ttu-id="da085-125"><xref:System.Windows.Forms.MenuItem>(で使用される<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="da085-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="da085-126">次のコントロールは、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] でのみオーナー描画をサポートします。</span><span class="sxs-lookup"><span data-stu-id="da085-126">The following controls support owner drawing only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="da085-127">次のコントロールはオーナー描画をサポートし、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] での新機能です。</span><span class="sxs-lookup"><span data-stu-id="da085-127">The following controls support owner drawing and are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="da085-128">以下のセクションでは、これらの各コントロールについてさらに詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="da085-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="da085-129">ListBox コントロールと ComboBox コントロール</span><span class="sxs-lookup"><span data-stu-id="da085-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="da085-130"><xref:System.Windows.Forms.ListBox>と<xref:System.Windows.Forms.ComboBox>コントロールを使用すると、すべて 1 つのサイズまたはさまざまなサイズで、コントロール内の個々 の項目を描画します。</span><span class="sxs-lookup"><span data-stu-id="da085-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da085-131">ただし、<xref:System.Windows.Forms.CheckedListBox>から派生したコントロールが、<xref:System.Windows.Forms.ListBox>コントロールをサポートしていませんオーナー描画します。</span><span class="sxs-lookup"><span data-stu-id="da085-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="da085-132">同じサイズの各項目を描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.DrawMode.OwnerDrawFixed>を処理し、`DrawItem`イベント。</span><span class="sxs-lookup"><span data-stu-id="da085-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="da085-133">さまざまなサイズを使用して各項目を描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>両方を処理し、`MeasureItem`と`DrawItem`イベント。</span><span class="sxs-lookup"><span data-stu-id="da085-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="da085-134">`MeasureItem` イベントを使うと、項目の `DrawItem` イベントが発生する前に、その項目のサイズを指定できます。</span><span class="sxs-lookup"><span data-stu-id="da085-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="da085-135">サンプル コードなど詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="da085-135">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [<span data-ttu-id="da085-136">方法: ComboBox コントロールにサイズ変更可能なテキストを作成する</span><span class="sxs-lookup"><span data-stu-id="da085-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="da085-137">MenuItem コンポーネント</span><span class="sxs-lookup"><span data-stu-id="da085-137">MenuItem Component</span></span>  
 <span data-ttu-id="da085-138"><xref:System.Windows.Forms.MenuItem>コンポーネントが 1 つのメニュー項目を表す、<xref:System.Windows.Forms.MainMenu>または<xref:System.Windows.Forms.ContextMenu>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="da085-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="da085-139">描画する、<xref:System.Windows.Forms.MenuItem>設定、その`OwnerDraw`プロパティを`true`処理とその`DrawItem`イベント。</span><span class="sxs-lookup"><span data-stu-id="da085-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="da085-140">`DrawItem` イベントが発生する前にメニュー項目のサイズをカスタマイズするには、項目の`MeasureItem` イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="da085-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="da085-141">サンプル コードなど詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="da085-141">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="da085-142">TabControl コントロール</span><span class="sxs-lookup"><span data-stu-id="da085-142">TabControl Control</span></span>  
 <span data-ttu-id="da085-143"><xref:System.Windows.Forms.TabControl>コントロールでは、コントロール内の個々 のタブを描画することができます。</span><span class="sxs-lookup"><span data-stu-id="da085-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="da085-144">オーナー描画タブのみに影響を与える<xref:System.Windows.Forms.TabPage>内容が影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="da085-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="da085-145">各タブを描画する、 <xref:System.Windows.Forms.TabControl>、設定、`DrawMode`プロパティを<xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>を処理し、`DrawItem`イベント。</span><span class="sxs-lookup"><span data-stu-id="da085-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="da085-146">このイベントは、コントロールにタブが表示されている場合にのみ、タブごとに 1 回発生します。</span><span class="sxs-lookup"><span data-stu-id="da085-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="da085-147">サンプル コードなど詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="da085-147">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="da085-148">ToolTip コンポーネント</span><span class="sxs-lookup"><span data-stu-id="da085-148">ToolTip Component</span></span>  
 <span data-ttu-id="da085-149"><xref:System.Windows.Forms.ToolTip>コンポーネントでは、表示される場合、全体のツールヒントを描画することができます。</span><span class="sxs-lookup"><span data-stu-id="da085-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="da085-150">描画する、<xref:System.Windows.Forms.ToolTip>設定、その`OwnerDraw`プロパティを`true`処理とその`Draw`イベント。</span><span class="sxs-lookup"><span data-stu-id="da085-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="da085-151">サイズをカスタマイズする、<xref:System.Windows.Forms.ToolTip>する前に、`Draw`処理イベントが発生する、`Popup`イベントとセット、<xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A>イベント ハンドラーのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="da085-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="da085-152">サンプル コードなど詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="da085-152">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="da085-153">ListView コントロール</span><span class="sxs-lookup"><span data-stu-id="da085-153">ListView Control</span></span>  
 <span data-ttu-id="da085-154"><xref:System.Windows.Forms.ListView>コントロールでは、コントロール内の個々 の項目、サブ項目、および列ヘッダーを描画することができます。</span><span class="sxs-lookup"><span data-stu-id="da085-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="da085-155">コントロールのオーナー描画を有効にするには、`OwnerDraw` プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="da085-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="da085-156">コントロール内の各項目を描画するには、`DrawItem` イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="da085-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="da085-157">コントロール内の各サブ項目または列ヘッダーを描画するときに、<xref:System.Windows.Forms.ListView.View%2A>プロパティに設定されている<xref:System.Windows.Forms.View.Details>、処理、`DrawSubItem`と`DrawColumnHeader`イベント。</span><span class="sxs-lookup"><span data-stu-id="da085-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="da085-158">サンプル コードなど詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="da085-158">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="da085-159">TreeView コントロール</span><span class="sxs-lookup"><span data-stu-id="da085-159">TreeView Control</span></span>  
 <span data-ttu-id="da085-160"><xref:System.Windows.Forms.TreeView>コントロールでは、コントロール内の個々 のノードを描画することができます。</span><span class="sxs-lookup"><span data-stu-id="da085-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="da085-161">各ノードに表示されるテキストのみを描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText>を処理し、`DrawNode`テキストを描画するイベントです。</span><span class="sxs-lookup"><span data-stu-id="da085-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="da085-162">各ノードのすべての要素を描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll>を処理し、`DrawNode`方に必要な要素、テキスト、アイコン、チェック ボックス、プラスとマイナス記号などと、ノードを結ぶ直線を描画するイベントです。</span><span class="sxs-lookup"><span data-stu-id="da085-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="da085-163">サンプル コードなど詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="da085-163">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="da085-164">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="da085-164">DataGridView Control</span></span>  
 <span data-ttu-id="da085-165"><xref:System.Windows.Forms.DataGridView>コントロールでは、コントロール内の個々 のセルと行を描画することができます。</span><span class="sxs-lookup"><span data-stu-id="da085-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="da085-166">個別のセルを描画するには、`CellPainting` イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="da085-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="da085-167">個別の行または行の要素を描画するには、`RowPrePaint` イベントと `RowPostPaint` イベントの一方または両方を処理します。</span><span class="sxs-lookup"><span data-stu-id="da085-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="da085-168">`RowPrePaint` イベントは行内のセルが描画される前に発生し、`RowPostPaint` イベントはセルが描画された後で発生します。</span><span class="sxs-lookup"><span data-stu-id="da085-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="da085-169">両方のイベントと `CellPainting` イベントを処理して、行の背景、個々のセル、行の前景を個別に描画できます。または、必要な部分については個別にカスタマイズを提供し、行の他の要素には既定の表示を使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="da085-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="da085-170">サンプル コードなど詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="da085-170">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [<span data-ttu-id="da085-171">方法: Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="da085-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [<span data-ttu-id="da085-172">方法 : Windows フォームの DataGridView コントロールの行の外観をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="da085-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="da085-173">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="da085-173">ToolStrip Control</span></span>  
 <span data-ttu-id="da085-174"><xref:System.Windows.Forms.ToolStrip>派生したコントロールの外観のすべての側面をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="da085-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="da085-175">カスタムの表示を提供する<xref:System.Windows.Forms.ToolStrip>、コントロールの設定、`Renderer`のプロパティ、 <xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.ToolStripManager>、 <xref:System.Windows.Forms.ToolStripPanel>、または<xref:System.Windows.Forms.ToolStripContentPanel>を`ToolStripRenderer`オブジェクトし、によって提供される多くの描画イベントの 1 つ以上の処理、`ToolStripRenderer`クラスです。</span><span class="sxs-lookup"><span data-stu-id="da085-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="da085-176">または、設定、`Renderer`から派生した独自のクラスのインスタンスにプロパティ`ToolStripRenderer`、 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>、または<xref:System.Windows.Forms.ToolStripSystemRenderer>を実装またはオーバーライド特定`On` *EventName*メソッドです。</span><span class="sxs-lookup"><span data-stu-id="da085-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="da085-177">サンプル コードなど詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="da085-177">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [<span data-ttu-id="da085-178">方法: Windows フォームに ToolStrip コントロールのカスタム レンダラーを作成して設定する</span><span class="sxs-lookup"><span data-stu-id="da085-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [<span data-ttu-id="da085-179">方法 : ToolStrip コントロールをカスタム描画する</span><span class="sxs-lookup"><span data-stu-id="da085-179">How to: Custom Draw a ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="da085-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="da085-180">See Also</span></span>  
 [<span data-ttu-id="da085-181">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="da085-181">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
