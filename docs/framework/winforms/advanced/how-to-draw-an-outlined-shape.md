---
title: "方法 : 形状のアウトラインを描画する | Microsoft Docs"
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
  - "Graphics.DrawEllipse"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "円"
  - "円, 描画"
  - "円形"
  - "描画, 円形"
  - "描画, 形状"
  - "楕円, 描画"
  - "フォーム, 描画 (円形を)"
  - "アウトライン形状, 描画"
  - "アウトライン形状, 例"
  - "形状, 描画"
ms.assetid: f4f9214c-607e-407d-8cdd-6549f0278451
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : 形状のアウトラインを描画する
この例は、フォームに楕円と四角形のアウトラインを描画します。  
  
## 使用例  
 [!code-cpp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#6)]
 [!code-csharp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#6)]
 [!code-vb[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#6)]  
  
## コードのコンパイル  
 <xref:System.Windows.Forms.Form.Load> イベント ハンドラーでこのメソッドを呼び出すことはできません。  フォームがサイズ変更された場合、または別のフォームによって隠れている場合、描画済みのコンテンツは再描画されません。  コンテンツを自動的に再描画するには、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドする必要があります。  
  
## 信頼性の高いプログラミング  
 システム リソースを消費するオブジェクト \(<xref:System.Drawing.Pen> オブジェクトや <xref:System.Drawing.Graphics> オブジェクトなど\) では、必ず <xref:System.IDisposable.Dispose%2A> を呼び出す必要があります。  
  
## 参照  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 <xref:System.Drawing.Graphics.DrawRectangle%2A>   
 [グラフィックス プログラミングについて](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)