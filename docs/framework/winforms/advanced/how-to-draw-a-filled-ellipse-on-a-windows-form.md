---
title: "方法 : Windows フォームに塗りつぶした楕円を描画する | Microsoft Docs"
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
  - "Graphics.FillEllipse"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "円, 描画"
  - "円形"
  - "描画, 楕円"
  - "楕円, 描画"
  - "フォーム, 描画 (楕円を)"
  - "形状, 描画"
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : Windows フォームに塗りつぶした楕円を描画する
この例は、塗りつぶした楕円をフォームに描画します。  
  
## 使用例  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## コードのコンパイル  
 <xref:System.Windows.Forms.Form.Load> イベント ハンドラーでこのメソッドを呼び出すことはできません。  フォームがサイズ変更された場合、または別のフォームによって隠れている場合、描画済みのコンテンツは再描画されません。  コンテンツを自動的に再描画するには、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドする必要があります。  
  
## 信頼性の高いプログラミング  
 システム リソースを消費するオブジェクト \(<xref:System.Drawing.Brush> オブジェクトや <xref:System.Drawing.Graphics> オブジェクトなど\) では、必ず <xref:System.IDisposable.Dispose%2A> を呼び出す必要があります。  
  
## 参照  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [グラフィックス プログラミングについて](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [アルファ ブレンドの直線と塗りつぶし](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)   
 [ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)