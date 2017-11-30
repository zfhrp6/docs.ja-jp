---
title: "方法 : DataRepeater コントロールに項目ヘッダーを表示する (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da02f9374471a581a58131e26d618f91d7cbb7af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="d33a0-102">方法 : DataRepeater コントロールに項目ヘッダーを表示する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="d33a0-102">How to: Display Item Headers in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="d33a0-103">項目のヘッダー、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールに視覚インジケーターが用意されて ときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>が選択されています。</span><span class="sxs-lookup"><span data-stu-id="d33a0-103">The item header in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control provides a visual indicator when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> is selected.</span></span> <span data-ttu-id="d33a0-104">ときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>プロパティに設定されている<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical>(既定)、各項目の左側に項目ヘッダーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d33a0-104">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (the default), the item header is displayed to the left of each item.</span></span> <span data-ttu-id="d33a0-105">ときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>プロパティに設定されている<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>、各項目の上部にある項目ヘッダーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d33a0-105">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, the item header is displayed at the top of each item.</span></span>  
  
 <span data-ttu-id="d33a0-106">項目ヘッダーがで指定されている色で表示されますが最初にオンの場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>プロパティ、および、白の矢印のアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d33a0-106">When it is first selected, the item header is displayed in the color that is specified by the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property, and a white arrow icon is displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d33a0-107">設定した場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>に<xref:System.Drawing.Color.White%2A>アイテムが最初に選択したときに、選択記号は表示されません。</span><span class="sxs-lookup"><span data-stu-id="d33a0-107">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
 <span data-ttu-id="d33a0-108">ときに、フィールド、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>フォーカス、アイテム ヘッダーの変更の色、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>背景の色と、矢印アイコンの変更を黒にします。</span><span class="sxs-lookup"><span data-stu-id="d33a0-108">When a field in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> has focus, the color of the item header changes to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> background color and the arrow icon changes to black.</span></span> <span data-ttu-id="d33a0-109">データが変更された場合は、アイテム ヘッダーの鉛筆のアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d33a0-109">If data is changed, a pencil symbol is displayed in the item header.</span></span>  
  
 <span data-ttu-id="d33a0-110">既定の幅 (または高さときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>プロパティに設定されている<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) 項目のヘッダーが 15 ピクセルです。</span><span class="sxs-lookup"><span data-stu-id="d33a0-110">The default width (or height when the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) of the item header is 15 pixels.</span></span> <span data-ttu-id="d33a0-111">設定して、幅を変更することができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d33a0-111">You can change the width by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d33a0-112">場合、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 11 未満である値に設定されて、アイテム ヘッダーのマークは表示されません。</span><span class="sxs-lookup"><span data-stu-id="d33a0-112">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
 <span data-ttu-id="d33a0-113">項目ヘッダーを非表示を設定してできます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>プロパティを**False**です。</span><span class="sxs-lookup"><span data-stu-id="d33a0-113">You can hide the item headers by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span> <span data-ttu-id="d33a0-114">ときに<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>に設定されている**False**、項目が選択されていることだけが示されますが、点線の周囲、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>です。</span><span class="sxs-lookup"><span data-stu-id="d33a0-114">When <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> is set to **False**, the only indication that an item is selected is a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d33a0-115">監視することによって、独自の選択インジケーターを提供することも、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>のプロパティ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>で、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>のイベント、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d33a0-115">You can also provide your own selection indicator by monitoring the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> property of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="d33a0-116">詳細については、「<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d33a0-116">For more information, see <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</span></span>  
  
### <a name="to-change-the-appearance-of-item-headers"></a><span data-ttu-id="d33a0-117">項目ヘッダーの外観を変更するには</span><span class="sxs-lookup"><span data-stu-id="d33a0-117">To change the appearance of item headers</span></span>  
  
1.  <span data-ttu-id="d33a0-118">Windows フォーム デザイナーでの下部の領域を選択して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d33a0-118">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d33a0-119">コントロールの下の領域を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d33a0-119">You must select the lower region of the control.</span></span> <span data-ttu-id="d33a0-120">項目テンプレートのセクションを選択した場合、異なる一連のプロパティが [プロパティ] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d33a0-120">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="d33a0-121">[プロパティ] ウィンドウで使用して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>アイテム ヘッダーの色を変更するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d33a0-121">In the Properties window, use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property to change the color of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d33a0-122">設定した場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>に<xref:System.Drawing.Color.White%2A>アイテムが最初に選択したときに、選択記号は表示されません。</span><span class="sxs-lookup"><span data-stu-id="d33a0-122">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
3.  <span data-ttu-id="d33a0-123">使用して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>項目ヘッダーの幅 (または高さ) を変更するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d33a0-123">Use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property to change the width (or height) of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d33a0-124">場合、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 11 未満である値に設定されて、アイテム ヘッダーのマークは表示されません。</span><span class="sxs-lookup"><span data-stu-id="d33a0-124">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
### <a name="to-hide-item-headers"></a><span data-ttu-id="d33a0-125">項目ヘッダーを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="d33a0-125">To hide item headers</span></span>  
  
1.  <span data-ttu-id="d33a0-126">Windows フォーム デザイナーでの下部の領域を選択して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d33a0-126">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d33a0-127">コントロールの下の領域を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d33a0-127">You must select the lower region of the control.</span></span> <span data-ttu-id="d33a0-128">項目テンプレートのセクションを選択した場合、異なる一連のプロパティが [プロパティ] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d33a0-128">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="d33a0-129">[プロパティ] ウィンドウで、設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>プロパティを**False**です。</span><span class="sxs-lookup"><span data-stu-id="d33a0-129">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span>  
  
     <span data-ttu-id="d33a0-130">内のアイテムの場合に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>は選択すると、だけが示されますになります、点線の周囲、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>です。</span><span class="sxs-lookup"><span data-stu-id="d33a0-130">When an item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is selected, the only indication will be a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d33a0-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="d33a0-131">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="d33a0-132">DataRepeater コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="d33a0-132">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d33a0-133">方法: DataRepeater コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="d33a0-133">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d33a0-134">方法: DataRepeater コントロールのレイアウトを変更する</span><span class="sxs-lookup"><span data-stu-id="d33a0-134">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d33a0-135">DataRepeater コントロールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d33a0-135">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
