---
title: "方法 : ポップアップのカスタム位置を指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ab9baca1103adf8de96204bdb1b3353a5456b94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
