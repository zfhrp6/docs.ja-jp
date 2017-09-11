---
title: "軽減策: グリッド コントロールの *-column へのディスク領域の割り当て"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- Grid control retargeting changes
ms.assetid: 707c064d-85e9-4ea1-aefb-e42b60b88679
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 54391538ac0b2daf307cba2f7ceff1984d26b0ce
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-grid-control39s-space-allocation-to-star-columns"></a><span data-ttu-id="72e8d-102">軽減策: グリッド コントロールの *-column へのディスク領域の割り当て</span><span class="sxs-lookup"><span data-stu-id="72e8d-102">Mitigation: Grid Control&#39;s Space Allocation to Star-columns</span></span>

<span data-ttu-id="72e8d-103">.NET Framework 4.7 以降を対象とするアプリでは、WPF は <xref:System.Windows.Controls.Grid> コントロールが \*-column に領域を割り当てるために使用するアルゴリズムを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="72e8d-103">Starting with applications that the .NET Framework 4.7, WPF replaces the algorithm that the <xref:System.Windows.Controls.Grid> control uses to allocate space to \*-columns.</span></span> 

## <a name="whats-changed"></a><span data-ttu-id="72e8d-104">変更点</span><span class="sxs-lookup"><span data-stu-id="72e8d-104">What's changed</span></span>

<span data-ttu-id="72e8d-105">古いアルゴリズムには次のバグがありましたが、新しいアルゴリズムで修正されました。</span><span class="sxs-lookup"><span data-stu-id="72e8d-105">The new algorithm fixes several bugs present in the old algorithm:</span></span>

1. <span data-ttu-id="72e8d-106">列への割り当ての合計は、グリッドの幅を超える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-106">Total allocation to columns can exceed the Grid's width.</span></span> <span data-ttu-id="72e8d-107">この問題は、比例配分が最小サイズ未満の列に領域を割り当てると発生します。</span><span class="sxs-lookup"><span data-stu-id="72e8d-107">This can occur when allocating space to a column whose proportional share is less than its minimum size.</span></span> <span data-ttu-id="72e8d-108">このアルゴリズムでは最小サイズが割り当てられるため、他の列に使用できる領域が減ります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-108">The algorithm allocates the minimum size, which decreases the space available to other columns.</span></span> <span data-ttu-id="72e8d-109">割り当てる \*-column がなくなると、割り当ての合計は大きくなりすぎます。</span><span class="sxs-lookup"><span data-stu-id="72e8d-109">If there are no \*-columns left to allocate, the total allocation will be too large.</span></span>

1. <span data-ttu-id="72e8d-110">割り当ての合計が、グリッドの幅未満になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-110">Total allocation can fall short of the Grid's width.</span></span> <span data-ttu-id="72e8d-111">これは、問題 1 と重なる問題で、比例配分共有が最大サイズを超えている列に割り当て、不足を補う \*-column が残っていない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="72e8d-111">This is the dual problem to #1, arising when allocating to a column whose proportional share is greater than its maximum size, with no \*-columns left to take up the slack.</span></span>

1. <span data-ttu-id="72e8d-112">2 つの \*-column が、その -weight に比例していない割り当てを受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-112">Two \*-columns can receive allocations not proportional to their -weights.</span></span> <span data-ttu-id="72e8d-113">これは問題 1、2 よりも軽度な問題です。*-column A、B、C に (この順序で) 割り当てると、B の比例配分共有はその最小値 (または最大値) に違反します。</span><span class="sxs-lookup"><span data-stu-id="72e8d-113">This is a milder version of #1/#2, arising when allocating to *-columns A, B, and C (in that order), where B's proportional share violates its min (or max) constraint.</span></span> <span data-ttu-id="72e8d-114">前述のように、これによって列 C に使用できる領域が変わり、A よりも比例配分の割り当てが少なく (または多く) なります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-114">As above, this changes the space available to column C, who gets less (or more) proportional allocation than A did,</span></span>

1. <span data-ttu-id="72e8d-115">非常に大きな重みの列 (10^298 を超える場合) は、すべて 10^298 の重みとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="72e8d-115">Columns with extremely large weights (> 10^298) are all treated as if they had weight 10^298.</span></span> <span data-ttu-id="72e8d-116">そのような列 (およびやや小さな重みの列) の比例配分の差は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="72e8d-116">Proportional differences between them (and between columns with slightly smaller weights) are not honored.</span></span>

1. <span data-ttu-id="72e8d-117">無限の重みを持つ列が正しく処理されません。</span><span class="sxs-lookup"><span data-stu-id="72e8d-117">Columns with infinite weights are not handled correctly.</span></span> <span data-ttu-id="72e8d-118">[実際には重みを無限大に設定することはできませんが、これは人為的な制限です。</span><span class="sxs-lookup"><span data-stu-id="72e8d-118">[Actually you can't set a weight to Infinity, but this is an artificial restriction.</span></span> <span data-ttu-id="72e8d-119">割り当てコードは制限を処理しようとしますが、無効なジョブになります。]</span><span class="sxs-lookup"><span data-stu-id="72e8d-119">The allocation code was trying to handle it, but doing a bad job.]</span></span>

1. <span data-ttu-id="72e8d-120">オーバーフロー、アンダーフロー、精度の低下などの浮動小数点精度の問題を回避していますが、いくつかの軽微な問題があります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-120">Several minor problems while avoiding overflow, underflow, loss of precision and similar floating-point issues.</span></span>

1. <span data-ttu-id="72e8d-121">十分に高い DPI でレイアウトの丸めの調整が不適切です。</span><span class="sxs-lookup"><span data-stu-id="72e8d-121">Adjustments for layout rounding are incorrect at sufficiently high DPI.</span></span>

<span data-ttu-id="72e8d-122">新しいアルゴリズムでは、次の条件を満たす結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="72e8d-122">The new algorithm produces results that meet the following criteria:</span></span>

<span data-ttu-id="72e8d-123">A: </span><span class="sxs-lookup"><span data-stu-id="72e8d-123">A.</span></span> <span data-ttu-id="72e8d-124">*-column に割り当てられる実際の幅が、幅の最小値未満にならない、また幅の最大値を超えないようにします。</span><span class="sxs-lookup"><span data-stu-id="72e8d-124">The actual width assigned to a *-column is never less than its minimum width nor greater than its maximum width.</span></span>

<span data-ttu-id="72e8d-125">B: </span><span class="sxs-lookup"><span data-stu-id="72e8d-125">B.</span></span> <span data-ttu-id="72e8d-126">最小値または最大値の幅が割り当てられていない各 -column に、その -weight に比例した幅を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="72e8d-126">Each -column that is not assigned its minimum or maximum width is assigned a width proportional to its -weight.</span></span> <span data-ttu-id="72e8d-127">正確には、2 つの列がそれぞれ x、y と宣言され、いずれの列も最小値の幅または最大値の幅が割り当てられていない場合、各列に割り当てられる実際の幅 v と w は同じ比率の v / w == x / y になります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-127">To be precise, if two columns are declared with width x and y respectively, and if neither column receives its minimum or maximum width, the actual widths v and w assigned to the columns are in the same proportion: v / w == x / y.</span></span>

<span data-ttu-id="72e8d-128">C: </span><span class="sxs-lookup"><span data-stu-id="72e8d-128">C.</span></span> <span data-ttu-id="72e8d-129">"比例配分" の \*-column に割り当てられる幅の合計は、制限された列 (固定、自動、および最小値または最大値の幅が割り当てられた \*-column) に割り当てられた後に使用できる領域と同じなります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-129">The total width allocated to "proportional" \*-columns is equal to the space available after allocating to the constrained columns (fixed, auto, and \*-columns that are allocated their min or max width).</span></span> <span data-ttu-id="72e8d-130">たとえば、最小値の幅の合計がグリッドに使用できる幅を超える場合は、ゼロになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-130">This might be zero, for instance if the sum of the minimum widths exceeds the Grid's availbable width.</span></span>

<span data-ttu-id="72e8d-131">D:</span><span class="sxs-lookup"><span data-stu-id="72e8d-131">D.</span></span> <span data-ttu-id="72e8d-132">これらすべてのステートメントは "理想的な" レイアウトを基準に解釈されます。</span><span class="sxs-lookup"><span data-stu-id="72e8d-132">All these statements are to be interpreted with respect to the "ideal" layout.</span></span> <span data-ttu-id="72e8d-133">レイアウトの丸めが有効な場合、実際の幅は理想的な幅と最大 1 ピクセル異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-133">When layout rounding is in effect, the actual widths can differ from the ideal widths by as much as one pixel.</span></span>

<span data-ttu-id="72e8d-134">古いアルゴリズムでは (A) を考慮していましたが、上記の他の条件は考慮されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="72e8d-134">The old algorithm honored (A) but failed to honor the other criteria in the cases outlined above.</span></span>

<span data-ttu-id="72e8d-135">このトピックで取り上げた列と幅のすべての情報は、行と高さにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="72e8d-135">Everything said about columns and widths in this topic applies as well to rows and heights.</span></span>

## <a name="impact"></a><span data-ttu-id="72e8d-136">影響</span><span class="sxs-lookup"><span data-stu-id="72e8d-136">Impact</span></span>

<span data-ttu-id="72e8d-137">新しいアルゴリズムで \*-column に割り当てられる実際の幅は、次のようにさまざまな場合で変わります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-137">The new algorithm changes the actual width assigned to \*-columns in a number of cases:</span></span>

- <span data-ttu-id="72e8d-138">1 つまたは複数の \*-column に、その列の比例割り当てを無視する最小値または最大値の幅もある場合</span><span class="sxs-lookup"><span data-stu-id="72e8d-138">When one or more \*-columns also have a minimum or maximum width that overrides the proportional allocation for that column.</span></span> <span data-ttu-id="72e8d-139">(最小値の幅は、明示的な <xref:System.Windows.FrameworkElement.MinWidth%2A> 宣言、または列の内容から取得した暗黙的な最小値に由来する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72e8d-139">(The minimum width can derive from an explicit <xref:System.Windows.FrameworkElement.MinWidth%2A> declaration, or from an implicit minimum obtained from the column's content.</span></span> <span data-ttu-id="72e8d-140">最大値の幅は、明示的な <xref:System.Windows.FrameworkElement.MaxWidth%2A> 宣言にのみ由来します)。</span><span class="sxs-lookup"><span data-stu-id="72e8d-140">The maximum width can only be defined explicitly, from a <xref:System.Windows.FrameworkElement.MaxWidth%2A> declaration.)</span></span>

- <span data-ttu-id="72e8d-141">1 つまたは複数の \*-column で 10^298 を超える非常に大きな \*-weight を宣言した場合。</span><span class="sxs-lookup"><span data-stu-id="72e8d-141">When one or more \*-columns declare an extremely large \*-weight, greater than 10^298.</span></span>

- <span data-ttu-id="72e8d-142">\*-weight が大幅に異なるため、浮動小数点が不安定になる場合 (オーバーフロー、アンダーフロー、精度の低下)。</span><span class="sxs-lookup"><span data-stu-id="72e8d-142">When the \*-weights are sufficiently different to encounter floating-point instability (overflow, underflow, loss of precision).</span></span>

- <span data-ttu-id="72e8d-143">レイアウトの丸めが有効で、ディスプレイの実効 DPI が十分に高い場合。</span><span class="sxs-lookup"><span data-stu-id="72e8d-143">When layout rounding is enabled, and the effective display DPI is sufficiently high.</span></span>

<span data-ttu-id="72e8d-144">最初の 2 つの場合、新しいアルゴリズムで生成される幅は、古いアルゴリズムで生成される幅と大幅に異なる可能性があります。最後の場合、違いは最大で 1 から 2 ピクセルです。</span><span class="sxs-lookup"><span data-stu-id="72e8d-144">In the first two cases, the widths produced by the new algorithm can be significantly different from those produced by the old algorithm; in the last case, the difference will be at most one or two pixels.</span></span>

## <a name="mitigation"></a><span data-ttu-id="72e8d-145">軽減策</span><span class="sxs-lookup"><span data-stu-id="72e8d-145">Mitigation</span></span>

<span data-ttu-id="72e8d-146">.NET Framework 4.7 以降の .NET Framework をターゲットとするアプリの場合、既定で新しいアルゴリズムが使用されますが、.NET Framework 4.6.2 以前をターゲットとするアプリは古いアルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="72e8d-146">By default, apps that target versions of the .NET Framework starting with the .NET Framework 4.7 will use the new algorithm, while apps that target the .NET Framework 4.6.2 or earlier versions will use the old algorithm.</span></span>

<span data-ttu-id="72e8d-147">この既定を無視するには、次の構成設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="72e8d-147">To override the default, use the following configuration setting:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true" /> 
</runtime>
```

<span data-ttu-id="72e8d-148">値 'true' を設定すると古いアルゴリズムが選択され、'false' を設定すると新しいアルゴリズムが選択されます。</span><span class="sxs-lookup"><span data-stu-id="72e8d-148">The value 'true' selects the old algorithm, and 'false' selects the new algorithm.</span></span>

## <a name="see-also"></a><span data-ttu-id="72e8d-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="72e8d-149">See also</span></span>
[<span data-ttu-id="72e8d-150">.NET Framework 4.7 における再ターゲットの変更点</span><span class="sxs-lookup"><span data-stu-id="72e8d-150">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

