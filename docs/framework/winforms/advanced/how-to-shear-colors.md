---
title: "方法 : 色を傾斜する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "色, 傾斜"
  - "色, 変換 (カラー行列を使用して)"
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 色を傾斜する
傾斜は、1 つの色要素を別の色要素との比率分だけ増加または減少させます。  たとえば、赤の要素を青の要素の値の半分だけ増加する変換を考えます。  このような変換では、色 \(0.2, 0.5, 1\) は \(0.7, 0.5, 1\) になります。  新しい赤の要素は、0.2 \+ \(1\/2\)\(1\) \= 0.7 となります。  
  
## 使用例  
 ファイル ColorBars4.bmp から <xref:System.Drawing.Image> オブジェクトを作成する例を次に示します。  このコードは、次に、イメージ内の各ピクセルに上のパラグラフで説明した傾斜変換を適用します。  
  
 次の図は、左側に元のイメージ、右側に傾斜されたイメージを示しています。  
  
 ![色の傾斜](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")  
  
 傾斜変換を実行する前後の 4 つのバーのカラー ベクターを次の表に示します。  
  
|元|変換後|  
|-------|---------|  
|\(0, 0, 1, 1\)|\(0.5, 0, 1, 1\)|  
|\(0.5, 1, 0.5, 1\)|\(0.75, 1, 0.5, 1\)|  
|\(1, 1, 0, 1\)|\(1, 1, 0, 1\)|  
|\(0.4, 0.4, 0.4, 1\)|\(0.6, 0.4, 0.4, 1\)|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  `ColorBars.bmp` を、システムで有効なイメージ名とパスで置き換えます。  
  
## 参照  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [イメージの色の変更](../../../../docs/framework/winforms/advanced/recoloring-images.md)