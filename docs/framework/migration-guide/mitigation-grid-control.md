---
title: "軽減策: グリッド コントロールの *-column へのディスク領域の割り当て | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: 9460c8b6ca8db927af4064e3567eca34c1bf5c91
ms.openlocfilehash: c7acce9d41af7e72b04b89751a7b186c9581dfea
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-grid-control39s-space-allocation-to-star-columns"></a>軽減策: グリッド コントロールの *-column へのディスク領域の割り当て

.NET Framework 4.7 以降をターゲットとするアプリでは、WPF は <xref:System.Windows.Controls.Grid> コントロールが \*-column に領域を割り当てるために使用するアルゴリズムを置き換えます。 

## <a name="whats-changed"></a>変更点

古いアルゴリズムには次のバグがありましたが、新しいアルゴリズムで修正されました。

1. 列への割り当ての合計は、グリッドの幅を超える可能性があります。 この問題は、比例配分が最小サイズ未満の列に領域を割り当てると発生します。 このアルゴリズムでは最小サイズが割り当てられるため、他の列に使用できる領域が減ります。 割り当てる \*-column がなくなると、割り当ての合計は大きくなりすぎます。

1. 割り当ての合計が、グリッドの幅未満になる可能性があります。 これは、問題 1 と重なる問題で、比例配分共有が最大サイズを超えている列に割り当て、不足を補う \*-column が残っていない場合に発生します。

1. 2 つの \*-column が、その -weight に比例していない割り当てを受ける可能性があります。 これは問題 1、2 よりも軽度な問題です。*-column A、B、C に (この順序で) 割り当てると、B の比例配分共有はその最小値 (または最大値) に違反します。 前述のように、これによって列 C に使用できる領域が変わり、A よりも比例配分の割り当てが少なく (または多く) なります。

1. 非常に大きな重みの列 (10^298 を超える場合) は、すべて 10^298 の重みとして処理されます。 そのような列 (およびやや小さな重みの列) の比例配分の差は考慮されません。

1. 無限の重みを持つ列が正しく処理されません。 [実際には重みを無限大に設定することはできませんが、これは人為的な制限です。 割り当てコードは制限を処理しようとしますが、無効なジョブになります。]

1. オーバーフロー、アンダーフロー、精度の低下などの浮動小数点精度の問題を回避していますが、いくつかの軽微な問題があります。

1. 十分に高い DPI でレイアウトの丸めの調整が不適切です。

新しいアルゴリズムでは、次の条件を満たす結果が生成されます。

A:  *-column に割り当てられる実際の幅が、幅の最小値未満にならない、また幅の最大値を超えないようにします。

B:  最小値または最大値の幅が割り当てられていない各 -column に、その -weight に比例した幅を割り当てます。 正確には、2 つの列がそれぞれ x、y と宣言され、いずれの列も最小値の幅または最大値の幅が割り当てられていない場合、各列に割り当てられる実際の幅 v と w は同じ比率の v / w == x / y になります。

C:  "比例配分" の \*-column に割り当てられる幅の合計は、制限された列 (固定、自動、および最小値または最大値の幅が割り当てられた \*-column) に割り当てられた後に使用できる領域と同じなります。 たとえば、最小値の幅の合計がグリッドに使用できる幅を超える場合は、ゼロになる可能性があります。

D: これらすべてのステートメントは "理想的な" レイアウトを基準に解釈されます。 レイアウトの丸めが有効な場合、実際の幅は理想的な幅と最大 1 ピクセル異なる可能性があります。

古いアルゴリズムでは (A) を考慮していましたが、上記の他の条件は考慮されていませんでした。

このトピックで取り上げた列と幅のすべての情報は、行と高さにも適用されます。

## <a name="impact"></a>影響

新しいアルゴリズムで \*-column に割り当てられる実際の幅は、次のようにさまざまな場合で変わります。

- 1 つまたは複数の \*-column に、その列の比例割り当てを無視する最小値または最大値の幅もある場合 (最小値の幅は、明示的な <xref:System.Windows.FrameworkElement.MinWidth%2A> 宣言、または列の内容から取得した暗黙的な最小値に由来する可能性があります。 最大値の幅は、明示的な <xref:System.Windows.FrameworkElement.MaxWidth%2A> 宣言にのみ由来します)。

- 1 つまたは複数の \*-column で 10^298 を超える非常に大きな \*-weight を宣言した場合。

- \*-weight が大幅に異なるため、浮動小数点が不安定になる場合 (オーバーフロー、アンダーフロー、精度の低下)。

- レイアウトの丸めが有効で、ディスプレイの実効 DPI が十分に高い場合。

最初の 2 つの場合、新しいアルゴリズムで生成される幅は、古いアルゴリズムで生成される幅と大幅に異なる可能性があります。最後の場合、違いは最大で 1 から 2 ピクセルです。

## <a name="mitigation"></a>軽減策

.NET Framework 4.7 以降の .NET Framework をターゲットとするアプリの場合、既定で新しいアルゴリズムが使用されますが、.NET Framework 4.6.2 以前をターゲットとするアプリは古いアルゴリズムが使用されます。

この既定を無視するには、次の構成設定を使用します。

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true" /> 
</runtime>
```

値 'true' を設定すると古いアルゴリズムが選択され、'false' を設定すると新しいアルゴリズムが選択されます。

## <a name="see-also"></a>関連項目
[.NET Framework 4.7 における再ターゲットの変更点](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

