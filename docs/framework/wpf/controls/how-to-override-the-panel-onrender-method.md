---
title: "方法 : パネルの OnRender メソッドをオーバーライドする"
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 774c612b09d5cb0ffdf36024a7e6a543f407cf67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
