---
title: "方法 : ペンの色を設定する | Microsoft Docs"
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
  - "色付きのペン"
  - "ペン, 設定 (色を)"
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : ペンの色を設定する
この例は、既存の <xref:System.Drawing.Pen> オブジェクトの色を変更します。  
  
## 使用例  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `myPen` という名前の <xref:System.Drawing.Pen> オブジェクト  
  
## 信頼性の高いプログラミング  
 システム リソースを消費するオブジェクト \(<xref:System.Drawing.Pen> オブジェクトなど\) を使用した後は、必ず <xref:System.Drawing.Pen.Dispose%2A> を呼び出す必要があります。  
  
## 参照  
 <xref:System.Drawing.Pen>   
 [グラフィックス プログラミングについて](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [方法 : ペンを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)   
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [GDI\+ でのペン、直線、および四角形](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)