---
title: '方法 : カスタム パネル要素を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 2d1581ef1d0130a6952becf36d668e6a198e1ee9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-panel-element"></a>方法 : カスタム パネル要素を作成する
## <a name="example"></a>例  
 この例の既定のレイアウト動作をオーバーライドする方法を示しています、<xref:System.Windows.Controls.Panel>要素から派生したカスタム レイアウト要素を作成および<xref:System.Windows.Controls.Panel>です。  
  
 例では、定義の単純なカスタム<xref:System.Windows.Controls.Panel>と呼ばれる要素`PlotPanel`、子要素に従って 2 つハード コーディングされた x 座標と y 座標を配置します。 この例では`x`と`y`に設定されて`50`。 したがって、すべての子要素は、x と y でその場所に配置軸です。  
  
 ユーザー設定を実装する<xref:System.Windows.Controls.Panel>動作、この例では、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>と<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドです。 各メソッドを返します、<xref:System.Windows.Size>配置し、子要素をレンダリングするために必要なデータです。  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Panel>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [カスタム コンテンツの折り返しパネル サンプルを作成します。](http://go.microsoft.com/fwlink/?LinkID=159979)
