---
title: "方法 : 成型された Windows フォームを作成する | Microsoft Docs"
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
  - "フォーム, 変更 (形を)"
  - "フォーム, 円形"
  - "フォーム, カスタムの形"
  - "フォーム, 四角形以外"
  - "フォーム, 角の丸い"
  - "成型されたフォーム"
  - "Windows フォーム, 円形"
  - "Windows フォーム, カスタムの形"
  - "Windows フォーム, 四角形以外の形状"
  - "Windows フォーム, 角の丸い"
  - "Windows フォーム, 成型された"
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 成型された Windows フォームを作成する
この例は、フォームと共にサイズ変更する楕円形をフォームに設定します。  
  
## 使用例  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   <xref:System.Windows.Forms> 名前空間および <xref:System.Drawing> 名前空間への参照。  
  
 次のコード例では、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドし、フォームの形状を変更します。  このコードを使用するには、メソッド宣言と共にメソッド内の描画コードをコピーします。  
  
## 参照  
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 <xref:System.Drawing.Region>   
 <xref:System.Drawing>   
 <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>   
 <xref:System.Windows.Forms.Control.Region%2A>   
 [グラフィックス プログラミングについて](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)