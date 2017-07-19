---
title: "変換を使用した色のスケーリング | Microsoft Docs"
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
  - "色, スケーリング"
  - "変換, スケーリング (色の)"
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 変換を使用した色のスケーリング
スケーリング変換では、4 つの色要素のうちの 1 つ以上の要素に数値を掛け合わせます。  スケーリングを表すカラー行列エントリを次の表に示します。  
  
|スケーリング対象の要素|行列エントリ|  
|-----------------|------------|  
|赤|\[0\]\[0\]|  
|緑|\[1\]\[1\]|  
|青|\[2\]\[2\]|  
|アルファ|\[3\]\[3\]|  
  
## 単一色のスケーリング  
 ファイル ColorBars2.bmp から <xref:System.Drawing.Image> オブジェクトを構築する例を次に示します。  このコードは、次に、イメージ内の各ピクセルの青の要素を係数 2 でスケーリングします。  元のイメージと変換後のイメージが並んで描画されます。  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 次の図は、左側に元のイメージ、右側にスケーリングされたイメージを示しています。  
  
 ![スケールの色](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")  
  
 青のスケーリングを実行する前後の 4 つのバーのカラー ベクターを次の表に示します。  4 番目のカラー バーの青の要素は、0.8 から 0.6 になっています。  その理由は、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] が結果値の小数部だけを保持するためです。  たとえば、\(2\)\(0.8\) \= 1.6 の場合、1.6 の小数部は 0.6 になります。  小数部だけを保持することによって、結果値が必ず \[0, 1\] の間隔内に収まるようにしています。  
  
|元|変換後|  
|-------|---------|  
|\(0.4, 0.4, 0.4, 1\)|\(0.4, 0.4, 0.8, 1\)|  
|\(0.4, 0.2, 0.2, 1\)|\(0.4, 0.2, 0.4, 1\)|  
|\(0.2, 0.4, 0.2, 1\)|\(0.2, 0.4, 0.4, 1\)|  
|\(0.4, 0.4, 0.8, 1\)|\(0.4, 0.4, 0.6, 1\)|  
  
## 複数の色のスケーリング  
 ファイル ColorBars2.bmp から <xref:System.Drawing.Image> オブジェクトを構築する例を次に示します。  このコードは、次に、イメージ内の各ピクセルの赤、緑、青の各要素をスケーリングします。  赤の要素は 25%、緑の要素は 35%、青の要素は 50% 縮小されます。  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 次の図は、左側に元のイメージ、右側にスケーリングされたイメージを示しています。  
  
 ![スケールの色](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")  
  
 赤、緑、および青のスケーリングを実行する前後の 4 つのバーのカラー ベクターを次の表に示します。  
  
|元|変換後|  
|-------|---------|  
|\(0.6, 0.6, 0.6, 1\)|\(0.45, 0.39, 0.3, 1\)|  
|\(0, 1, 1, 1\)|\(0, 0.65, 0.5, 1\)|  
|\(1, 1, 0, 1\)|\(0.75, 0.65, 0, 1\)|  
|\(1, 0, 1, 1\)|\(0.75, 0, 0.5, 1\)|  
  
## 参照  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [イメージの色の変更](../../../../docs/framework/winforms/advanced/recoloring-images.md)