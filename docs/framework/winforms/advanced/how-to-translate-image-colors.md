---
title: "方法 : イメージの色を変換する | Microsoft Docs"
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
  - "ビットマップ [Windows フォーム], 変更 (色を)"
  - "イメージの色 [Windows フォーム]"
  - "イメージ [Windows フォーム], 変更 (色を)"
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : イメージの色を変換する
変換では、4 つの色要素のうちの 1 つ以上の要素に値が追加されます。  変換を表すカラー行列エントリを次の表に示します。  
  
|変換対象の要素|行列エントリ|  
|-------------|------------|  
|赤|\[4\]\[0\]|  
|緑|\[4\]\[1\]|  
|青|\[4\]\[2\]|  
|アルファ|\[4\]\[3\]|  
  
## 使用例  
 ファイル ColorBars.bmp から <xref:System.Drawing.Image> オブジェクトを作成する例を次に示します。  このコードは、次に、イメージ内の各ピクセルの赤の要素に 0.75 を追加します。  元のイメージと変換後のイメージが並んで描画されます。  
  
 次の図は、左側に元のイメージ、右側に変換後のイメージを示しています。  
  
 ![色の変換](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 赤の変換を実行する前後の 4 つのバーのカラー ベクターを次の表に示します。  色要素の最大値が 1 であるため、2 番目の行にある赤の要素は変化しません。  同様に、色要素の最小値は 0 です。  
  
|元|変換後|  
|-------|---------|  
|黒 \(0, 0, 0, 1\)|\(0.75, 0, 0, 1\)|  
|赤 \(1, 0, 0, 1\)|\(1, 0, 0, 1\)|  
|緑 \(0, 1, 0, 1\)|\(0.75, 1, 0, 1\)|  
|青 \(0, 0, 1, 1\)|\(0.75, 0, 1, 1\)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  `ColorBars.bmp`  は、システム上で有効なイメージ ファイルの名前とパスに置き換えてください。  
  
## 参照  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [イメージの色の変更](../../../../docs/framework/winforms/advanced/recoloring-images.md)