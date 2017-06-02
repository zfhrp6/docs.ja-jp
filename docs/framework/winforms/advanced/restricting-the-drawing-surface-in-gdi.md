---
title: "GDI+ での描画サーフェイスの制限 | Microsoft Docs"
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
  - "クリップする, 使用 (GDI+ を)"
  - "GDI+, クリップする"
  - "GDI+, 限定 (描画サーフェイスを)"
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# GDI+ での描画サーフェイスの制限
クリッピングでは、特定の四角形または領域だけに描画を制限します。  文字列 "Hello" をハート形の領域に合わせてクリップした例を次の図に示します。  
  
 ![制限付き描画面](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.png "AboutGdip02\_Art30")  
  
## 領域のクリッピング  
 領域はパスから構築でき、パスは文字列のアウトラインを含むことができるため、テキストのアウトラインをクリッピングに使用できます。  複数の同心楕円をテキスト文字列の内部に合わせてクリップした例を次の図に示します。  
  
 ![制限付き描画面](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.png "AboutGdip02\_Art31")  
  
 クリッピングを使用して描画するには、<xref:System.Drawing.Graphics> オブジェクトを作成し、このオブジェクトの <xref:System.Drawing.Graphics.Clip%2A> プロパティを設定してから、同じ <xref:System.Drawing.Graphics> オブジェクトの描画メソッドを呼び出します。  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## 参照  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Region?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [領域の使用](../../../../docs/framework/winforms/advanced/using-regions.md)