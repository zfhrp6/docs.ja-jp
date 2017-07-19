---
title: "方法 : 直線、曲線、および形状から図形を作成する | Microsoft Docs"
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
  - "図形, 作成 (直線から)"
  - "図形, 作成 (形状から)"
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 直線、曲線、および形状から図形を作成する
図形を作成するには、<xref:System.Drawing.Drawing2D.GraphicsPath> を作成し、<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> や <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> などのメソッドを呼び出して、パスにプリミティブを追加します。  
  
## 使用例  
 次のコード例では、図形を含むパスを作成します。  
  
-   1 番目の例では、1 つの図形から成るパスを作成します。  この図形は、1 つの円弧から成ります。  この円弧のスイープ角度は \-180°であり、既定の座標系では、これは反時計回りに計測された角度です。  
  
-   2 番目の例では、2 つの図形から成るパスを作成します。  最初の図形では、円弧の後に直線が続いています。  2 番目の図形では、直線の後に曲線が続き、さらにその後に直線が続いています。  最初の図形は開いたままで、2 番目の図形は閉じています。  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## コードのコンパイル  
 前の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 <xref:System.Drawing.Drawing2D.GraphicsPath>   
 [パスの作成および描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)   
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)