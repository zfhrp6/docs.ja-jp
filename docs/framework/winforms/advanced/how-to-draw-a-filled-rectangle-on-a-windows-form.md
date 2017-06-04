---
title: "方法 : Windows フォームに塗りつぶした四角形を描画する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Graphics.FillRectangle"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "描画 (四角形を)"
  - "描画, 四角形"
  - "四角形, 描画"
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォームに塗りつぶした四角形を描画する
この例は、塗りつぶした四角形をフォームに描画します。  
  
## 使用例  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## コードのコンパイル  
 <xref:System.Windows.Forms.Form.Load> イベント ハンドラーでこのメソッドを呼び出すことはできません。  フォームがサイズ変更された場合、または別のフォームによって隠れている場合、描画済みのコンテンツは再描画されません。  コンテンツを自動的に再描画するには、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドする必要があります。  
  
## 信頼性の高いプログラミング  
 システム リソースを消費するオブジェクト \(<xref:System.Drawing.Brush> オブジェクトや <xref:System.Drawing.Graphics> オブジェクトなど\) では、必ず <xref:System.IDisposable.Dispose%2A> を呼び出す必要があります。  
  
## 参照  
 <xref:System.Drawing.Graphics.FillRectangle%2A>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [グラフィックス プログラミングについて](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [GDI\+ でのブラシと塗りつぶされた図形](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)