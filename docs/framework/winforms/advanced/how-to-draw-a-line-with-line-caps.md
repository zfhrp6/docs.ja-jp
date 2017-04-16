---
title: "方法 : ライン キャップを使用した直線を描画する | Microsoft Docs"
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
  - "描画 (線を), ライン キャップ"
  - "描画, 線"
  - "線, 描画"
  - "ペン, 描画 (線を)"
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : ライン キャップを使用した直線を描画する
ライン キャップと呼ばれるいくつかの形状のいずれかを使用して、直線の開始点または終了点を描画できます。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、円形、正方形、菱形、矢じり形などの複数のライン キャップをサポートしています。  
  
## 使用例  
 ライン キャップは、直線の開始点 \(開始キャップ\)、終了点 \(端点キャップ\)、または破線のダッシュ \(ダッシュ キャップ\) に対して指定できます。  
  
 一方の端には矢じり形のキャップ、もう一方の端には円形のキャップを使用した直線を描画する例を次に示します。  結果として得られる直線を次の図に示します。  
  
 ![ペン](../../../../docs/framework/winforms/advanced/media/pens4.png "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## コードのコンパイル  
  
-   Windows フォームを作成し、フォームの <xref:System.Windows.Forms.Control.Paint> イベントを処理します。  プログラム例を <xref:System.Windows.Forms.Control.Paint> イベント ハンドラーに貼り付け、`e` を <xref:System.Windows.Forms.PaintEventArgs> として渡します。  
  
## 参照  
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=fullName>   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)