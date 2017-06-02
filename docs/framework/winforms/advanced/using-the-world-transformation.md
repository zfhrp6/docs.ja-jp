---
title: "ワールド変換の使用 | Microsoft Docs"
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
  - "グラフィックス, ワールド変換"
  - "ワールド変換, 例"
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# ワールド変換の使用
ワールド変換は、<xref:System.Drawing.Graphics> クラスのプロパティです。  ワールド変換を指定する数値は、3 × 3 の行列を表す <xref:System.Drawing.Drawing2D.Matrix> オブジェクトに格納されます。  <xref:System.Drawing.Drawing2D.Matrix> クラスおよび <xref:System.Drawing.Graphics> クラスには、ワールド変換行列の数値を設定するためのメソッドがいくつかあります。  
  
## さまざまな変換  
 最初に 50 × 50 の四角形を作成し、その四角形を原点 \(0, 0\) に配置する例を次に示します。  原点は、クライアント領域の左上隅の位置です。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 スケーリング変換を適用し、四角形を x 方向に係数 1.75 で拡大し、y 方向に係数 0.5 で縮小するコードを次に示します。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 その結果、元の四角形よりも x 方向が長く、y 方向が短い四角形が作成されます。  
  
 この四角形をスケーリングせずに回転させる場合は、次のコードを使用します。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 この四角形を平行移動するには、次のコードを使用します。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## 参照  
 <xref:System.Drawing.Drawing2D.Matrix>   
 [座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [マネージ GDI\+ での変換の使用](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)