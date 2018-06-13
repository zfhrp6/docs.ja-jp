---
title: '方法 : パネルの OnRender メソッドをオーバーライドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: e591bc195d3b0ba58002bda42ddb3e9ed35d312e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554873"
---
# <a name="how-to-override-the-panel-onrender-method"></a>方法 : パネルの OnRender メソッドをオーバーライドする
この例は、オーバーライドする方法を示します、<xref:System.Windows.Controls.Panel.OnRender%2A>メソッドの<xref:System.Windows.Controls.Panel>レイアウト要素をカスタムのグラフィック効果を追加するためにします。  
  
## <a name="example"></a>例  
 使用して、<xref:System.Windows.Controls.Panel.OnRender%2A>レンダリングされたパネルの要素にグラフィック効果を追加するためにメソッドです。 たとえば、このメソッドを使用すると、カスタム枠線や背景の効果を追加します。 A<xref:System.Windows.Media.DrawingContext>オブジェクトは、図形、テキスト、画像、またはビデオを描画するためのメソッドを提供する引数として渡されます。 その結果、このメソッドは、パネル オブジェクトのカスタマイズの場合に便利です。  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Panel>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [カスタムの放射状パネルのサンプル](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [方法トピック](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
