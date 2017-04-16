---
title: "方法 : ハッチ パターンで図形を塗りつぶす | Microsoft Docs"
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
  - "ブラシ, 使用 (ハッチ ブラシを)"
  - "パターン, 追加 (図形に)"
  - "形状, 塗りつぶし (パターンで)"
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : ハッチ パターンで図形を塗りつぶす
ハッチ パターンは、背景色と、背景上にパターンを形成する直線の色という 2 つの色から構成されます。  閉じている図形をハッチ パターンで塗りつぶすには、<xref:System.Drawing.Drawing2D.HatchBrush> オブジェクトを使用します。  楕円をハッチ パターンで塗りつぶす方法を次の例に示します。  
  
## 使用例  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> コンストラクターは、ハッチ スタイル、ハッチ パターンを形成する直線の色、および背景色を 3 つの引数として受け取ります。  ハッチ スタイル引数には、<xref:System.Drawing.Drawing2D.HatchStyle> 列挙体から任意の値を指定できます。  <xref:System.Drawing.Drawing2D.HatchStyle> 列挙体は 50 を超える要素を保持しています。それらの要素のいくつかを次の一覧に示します。  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle>  
  
 塗りつぶされた楕円を次の図に示します。  
  
 ![ハッチ パターン](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)