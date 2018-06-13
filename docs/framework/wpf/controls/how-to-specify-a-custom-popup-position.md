---
title: '方法 : ポップアップのカスタム位置を指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: 8714cfa4f7e5bb0ca157ee9d551392571303f60e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551740"
---
# <a name="how-to-specify-a-custom-popup-position"></a>方法 : ポップアップのカスタム位置を指定する
この例のカスタム位置を指定する方法を示しています、<xref:System.Windows.Controls.Primitives.Popup>タイミングを制御、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティに設定されている<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>です。  
  
## <a name="example"></a>例  
 ときに、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティに設定されている<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>、<xref:System.Windows.Controls.Primitives.Popup>の定義済みのインスタンスを呼び出す、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>を委任します。 このデリゲートが対象となる領域の左上隅およびの左上隅に対して相対的な可能なポイントのセットを返す、<xref:System.Windows.Controls.Primitives.Popup>です。 <xref:System.Windows.Controls.Primitives.Popup>配置が、最適な可視性を提供するポイントで発生します。  
  
 次の例の位置を定義する方法を示しています、<xref:System.Windows.Controls.Primitives.Popup>を設定して、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>です。 作成して割り当てる方法も示しています、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>を配置するためにデリゲート、<xref:System.Windows.Controls.Primitives.Popup>です。  コールバック デリゲートでは、2 つを返します<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>オブジェクト。  場合、<xref:System.Windows.Controls.Primitives.Popup>最初の位置にある画面の端で非表示には、<xref:System.Windows.Controls.Primitives.Popup>は 2 番目の位置に置かれます。  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 サンプル全体については、次を参照してください。[ポップアップ配置サンプル](http://go.microsoft.com/fwlink/?LinkID=160032)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [ポップアップの概要](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
