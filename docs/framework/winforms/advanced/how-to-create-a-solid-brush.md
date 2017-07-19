---
title: "方法 : ソリッド ブラシを作成する | Microsoft Docs"
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
  - "ブラシ, 作成 (ソリッド)"
  - "ブラシ, 例"
  - "純色のブラシ"
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : ソリッド ブラシを作成する
<xref:System.Drawing.Graphics> オブジェクトが図形の塗りつぶしに使用できる <xref:System.Drawing.SolidBrush> オブジェクトを作成する例を次に示します。  
  
## 使用例  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## 信頼性の高いプログラミング  
 ブラシ オブジェクトなど、システム リソースを消費するオブジェクトについては、使用後に <xref:System.IDisposable.Dispose%2A> を呼び出す必要があります。  
  
## 参照  
 <xref:System.Drawing.SolidBrush>   
 <xref:System.Drawing.Brush>   
 [グラフィックス プログラミングについて](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [GDI\+ でのブラシと塗りつぶされた図形](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)   
 [ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)