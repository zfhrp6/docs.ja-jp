---
title: '方法 : DataRepeater コントロールの外観を変更する (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: 9863d9343ffcecc1e4aae7f6bc16dae39ef76385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="bd6c1-102">方法 : DataRepeater コントロールの外観を変更する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="bd6c1-102">How to: Change the Appearance of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="bd6c1-103">外観を変更することができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール プロパティの設定によっては、デザイン時または実行時に処理して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>イベント。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-103">You can change the appearance of a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time by setting properties or at run time by handling the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event.</span></span>  
  
 <span data-ttu-id="bd6c1-104">コントロールの項目テンプレートのセクションを選択すると、デザイン時に設定したプロパティはごとに繰り返されます<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>実行時にします。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-104">Properties that you set at design time when the item template section of the control is selected will be repeated for each <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> at run time.</span></span> <span data-ttu-id="bd6c1-105">外観に関連するプロパティ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール自体は明らかになった場合にのみ、コンテナーのパーツが左の実行時に表示されます (たとえば場合、<xref:System.Windows.Forms.Control.Padding%2A>を大きな値に設定されます)。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-105">Appearance-related properties of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control itself will be visible at run time only if a part of the container is left uncovered (for example, if the <xref:System.Windows.Forms.Control.Padding%2A> property is set to a large value).</span></span>  
  
 <span data-ttu-id="bd6c1-106">実行時に、プロパティの外観に関連することができますに基づいて設定条件。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-106">At run time, appearance-related properties can be set based on conditions.</span></span> <span data-ttu-id="bd6c1-107">たとえば、スケジューリングのアプリケーションでは、期日の項目がユーザーに警告する項目の背景色を変更する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-107">For example, in a scheduling application, you might change the background color of an item to warn users when an item is past due.</span></span> <span data-ttu-id="bd6c1-108"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>など、条件付きステートメントでプロパティを設定した場合、イベント ハンドラー `If…Then`、使用することも必要があります、`Else`句を条件が満たされないときに、外観を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-108">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, if you set a property in a conditional statement such as `If…Then`, you must also use an `Else` clause to specify the appearance when the condition is not met.</span></span>  
  
### <a name="to-change-the-appearance-at-design-time"></a><span data-ttu-id="bd6c1-109">デザイン時の外観を変更するには</span><span class="sxs-lookup"><span data-stu-id="bd6c1-109">To change the appearance at design time</span></span>  
  
1.  <span data-ttu-id="bd6c1-110">Windows フォーム デザイナーで、項目テンプレート (上部) の領域を選択、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-110">In the Windows Forms Designer, select the item template (upper) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="bd6c1-111">[プロパティ] ウィンドウでプロパティを選択し、値を変更します。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-111">In the Properties window, select a property and change the value.</span></span> <span data-ttu-id="bd6c1-112">外観に影響する共通のプロパティを含める<xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.BackgroundImage%2A>、 <xref:System.Windows.Forms.Panel.BorderStyle%2A>、および<xref:System.Windows.Forms.Control.ForeColor%2A>です。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-112">Common properties that affect appearance include <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, and <xref:System.Windows.Forms.Control.ForeColor%2A>.</span></span>  
  
### <a name="to-change-the-appearance-at-run-time"></a><span data-ttu-id="bd6c1-113">実行時に外観を変更するには</span><span class="sxs-lookup"><span data-stu-id="bd6c1-113">To change the appearance at run time</span></span>  
  
1.  <span data-ttu-id="bd6c1-114">コード エディターで、[イベント] ボックスの一覧の **[DrawItem]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-114">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
2.  <span data-ttu-id="bd6c1-115"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 、イベント ハンドラーのプロパティを設定するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-115">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add code to set the properties:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="bd6c1-116">例</span><span class="sxs-lookup"><span data-stu-id="bd6c1-116">Example</span></span>  
 <span data-ttu-id="bd6c1-117">一般的なカスタマイズをいくらか、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールには、表示色を交互を条件に基づくフィールドの色を変更することで、行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-117">Some common customizations for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control include displaying the rows in alternating colors and changing the color of a field based on a condition.</span></span> <span data-ttu-id="bd6c1-118">次の例では、これらのカスタマイズを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-118">The following example shows how to perform these customizations.</span></span> <span data-ttu-id="bd6c1-119">この例があるか、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Northwind データベースの Products テーブルにバインドされているコントロール。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-119">This example assumes that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that is bound to the Products table in the Northwind database.</span></span>  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 <span data-ttu-id="bd6c1-120">これらのカスタマイズの両方、条件の両方の側のプロパティを設定するコードを提供する必要がありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-120">Note that for both of these customizations, you must provide code to set the properties for both sides of the condition.</span></span> <span data-ttu-id="bd6c1-121">指定しない場合、`Else`条件、実行時に予期しない結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bd6c1-121">If you do not specify the `Else` condition, you will see unexpected results at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd6c1-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd6c1-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [<span data-ttu-id="bd6c1-123">DataRepeater コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="bd6c1-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="bd6c1-124">DataRepeater コントロールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="bd6c1-124">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="bd6c1-125">方法: DataRepeater コントロールに、バインドされたデータを表示する</span><span class="sxs-lookup"><span data-stu-id="bd6c1-125">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="bd6c1-126">方法: DataRepeater コントロールに非バインド コントロールを表示する</span><span class="sxs-lookup"><span data-stu-id="bd6c1-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="bd6c1-127">方法: DataRepeater コントロールに項目ヘッダーを表示する</span><span class="sxs-lookup"><span data-stu-id="bd6c1-127">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
