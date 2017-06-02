---
title: "方法 : ペンを使用して四角形を描画する | Microsoft Docs"
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
  - "ペン, 描画 (四角形を)"
  - "四角形, 描画"
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : ペンを使用して四角形を描画する
四角形を描画するには、<xref:System.Drawing.Graphics> オブジェクトと <xref:System.Drawing.Pen> オブジェクトが必要です。  <xref:System.Drawing.Graphics> オブジェクトは <xref:System.Drawing.Graphics.DrawRectangle%2A> メソッドを提供し、<xref:System.Drawing.Pen> オブジェクトは線の色や幅などの特徴を格納します。  
  
## 使用例  
 上隅が \(10, 10\) の位置にある四角形を描画する例を次に示します。  この四角形の幅は 100 で、高さは 50 です。  <xref:System.Drawing.Pen.%23ctor%2A> コンストラクターに渡される 2 番目の引数は、ペン幅が 5 ピクセルであることを示しています。  
  
 四角形が描画されるときは、ペンは四角形の境界の中央に揃えて配置されます。  つまり、この場合はペン幅が 5 であるため、四角形の各辺は 5 ピクセルで描画されますが、そのうち 1 ピクセルは境界上に、2 ピクセルが内側に描画され、2 ピクセルが外側に描画されることになります。  ペンの配置の詳細については、「[方法 : ペンの幅と配置を設定する](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)」を参照してください。  
  
 結果として得られる四角形を次の図に示します。  点線は、ペン幅が 1 ピクセルの場合に四角形が描画される範囲を示しています。  四角形の左上隅の拡大図は、それらの点線の中央に揃えて黒い太線を配置した場合を示しています。  
  
 ![ペン](../../../../docs/framework/winforms/advanced/media/pens1.png "pens1")  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)