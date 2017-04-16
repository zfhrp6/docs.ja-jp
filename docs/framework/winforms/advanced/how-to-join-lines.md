---
title: "方法 : 直線を接合する | Microsoft Docs"
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
  - "面取り (直線の接合スタイル)"
  - "描画, 接合 (直線を)"
  - "グラフィックス, 接合 (直線を)"
  - "GraphicsPath オブジェクト"
  - "直線の接合"
  - "線, 結合"
  - "鋭角 (直線の接合スタイル)"
  - "Pen クラス"
  - "角丸 (直線の接合スタイル)"
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 直線を接合する
直線の接合部とは、2 本の直線の端が交わることによって形成される共通領域のことです。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、直線の接合スタイルとして、鋭角、面取り、および角丸の 3 つのスタイルを提供しています。  直線の接合スタイルは、<xref:System.Drawing.Pen> クラスのプロパティです。  <xref:System.Drawing.Pen> オブジェクトに対して直線の接合スタイルを指定すると、そのペンで描画された <xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクト内の連結されたすべての直線に対して、その接合スタイルが適用されます。  
  
 直線の面取り接合の結果を次の図に示します。  
  
 ![ペン](../../../../docs/framework/winforms/advanced/media/pens5.png "pens5")  
  
## 使用例  
 直線の接合スタイルを指定するには、<xref:System.Drawing.Pen> クラスの <xref:System.Drawing.Pen.LineJoin%2A> プロパティを使用します。  水平方向の直線と垂直方向の直線の接合部に面取り接合スタイルを適用する例を次に示します。  次のコードで <xref:System.Drawing.Pen.LineJoin%2A> プロパティに割り当てられた値 <xref:System.Drawing.Drawing2D.LineJoin> は、<xref:System.Drawing.Drawing2D.LineJoin> 列挙体のメンバーです。  <xref:System.Drawing.Drawing2D.LineJoin> 列挙体のその他のメンバーには、<xref:System.Drawing.Drawing2D.LineJoin> および <xref:System.Drawing.Drawing2D.LineJoin> があります。  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)