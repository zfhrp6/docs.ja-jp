---
title: "方法 : ペンの幅と配置を設定する | Microsoft Docs"
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
  - "ペン, 設定 (配置を)"
  - "ペン, 設定 (幅を)"
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : ペンの幅と配置を設定する
<xref:System.Drawing.Pen> オブジェクトを作成するときに、そのコンストラクターへの引数の 1 つとしてペン幅を渡すことができます。  また、<xref:System.Drawing.Pen> クラスの <xref:System.Drawing.Pen.Width%2A> プロパティを使用して、ペン幅を変更することもできます。  
  
 理論上は、線の幅は 0 です。  幅が 1 ピクセルの線を描画する場合、そのピクセルは理論上の線の中央に配置されます。  幅が 2 ピクセル以上の直線を描画する場合は、ピクセルは理論上の線の中央か、その線の片側に揃えて配置されます。  <xref:System.Drawing.Pen> のペン配置プロパティを設定して、そのペンで描画されるピクセルを理論上の線に対してどのように配置するかを指定できます。  
  
 次のコード例の <xref:System.Drawing.Drawing2D.PenAlignment>、<xref:System.Drawing.Drawing2D.PenAlignment>、および <xref:System.Drawing.Drawing2D.PenAlignment> の各値は、<xref:System.Drawing.Drawing2D.PenAlignment> 列挙体のメンバーです。  
  
 1 本の直線を 2 回描画する例を次に示します。1 回目は幅が 1 の黒いペンで描画し、2 回目は幅が 10 の緑のペンで描画します。  
  
### ペンの幅を変更するには  
  
-   <xref:System.Drawing.Pen.Alignment%2A> プロパティの値を <xref:System.Drawing.Drawing2D.PenAlignment> \(既定値\) に設定して、緑のペンで描画されるピクセルが理論上の直線の中央に揃えて配置されるように指定します。  結果として得られる直線を次の図に示します。  
  
     ![ペン](../../../../docs/framework/winforms/advanced/media/pens1a.png "pens1A")  
  
     四角形を 2 回描画する例を次に示します。1 回目は幅が 1 の黒いペンで描画し、2 回目は幅が 10 の緑のペンで描画します。  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### ペンの配置を変更するには  
  
-   <xref:System.Drawing.Pen.Alignment%2A> プロパティの値を <xref:System.Drawing.Drawing2D.PenAlignment> に設定して、緑のペンで描画されるピクセルが四角形の境界の中央に揃えて配置されるように指定します。  
  
     結果として得られる四角形を次の図に示します。  
  
     ![ペン](../../../../docs/framework/winforms/advanced/media/pens2.png "pens2")  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### くぼみ表示のペンを作成するには  
  
-   上のコードの 3 番目のステートメントを次のように変更して、緑のペンの配置を変更します。  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     この場合、緑の太い直線を表すピクセルは、次の図で示すように四角形の内側に表示されます。  
  
     ![ペン](../../../../docs/framework/winforms/advanced/media/pens3.png "pens3")  
  
## 参照  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)