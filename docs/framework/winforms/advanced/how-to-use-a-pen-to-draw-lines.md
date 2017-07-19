---
title: "方法 : ペンを使用して線を描画する | Microsoft Docs"
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
  - "線, 描画"
  - "ペン, 描画 (線を)"
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : ペンを使用して線を描画する
線を描画するには、<xref:System.Drawing.Graphics> オブジェクトと <xref:System.Drawing.Pen> オブジェクトが必要です。  <xref:System.Drawing.Graphics> オブジェクトは <xref:System.Drawing.Graphics.DrawLine%2A> メソッドを提供し、<xref:System.Drawing.Pen> オブジェクトは線の色や幅などの特徴を格納します。  
  
## 使用例  
 1 本の線を点 \(20, 10\) から点 \(300, 100\) に描画する例を次に示します。  最初のステートメントでは、<xref:System.Drawing.Pen.%23ctor%2A> クラス コンストラクターを使用して黒のペンを作成します。  <xref:System.Drawing.Pen.%23ctor%2A> コンストラクターに渡される 1 つの引数は、<xref:System.Drawing.Color.FromArgb%2A> メソッドで作成された <xref:System.Drawing.Color> オブジェクトです。  <xref:System.Drawing.Color> オブジェクトの作成に使用される値は \(255, 0, 0, 0\) であり、各値が色のアルファ、赤、緑、青の各要素に対応しています。  これらの値は、不透明な黒のペンを定義しています。  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 <xref:System.Drawing.Pen>   
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [GDI\+ でのペン、直線、および四角形](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)