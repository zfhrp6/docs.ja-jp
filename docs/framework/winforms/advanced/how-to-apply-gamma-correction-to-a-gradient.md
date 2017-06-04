---
title: "方法 : グラデーションに対してガンマ補正を適用する | Microsoft Docs"
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
  - "グラデーション ブラシ, ガンマ補正"
  - "グラデーション, ガンマ補正"
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : グラデーションに対してガンマ補正を適用する
線形グラデーション ブラシの <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> プロパティを `true` に設定することによって、そのブラシに対するガンマ補正を有効化できます。  <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> プロパティを `false` に設定すると、ガンマ補正は無効化されます。  既定では、ガンマ補正は無効になっています。  
  
## 使用例  
 線形グラデーション ブラシを作成し、そのブラシを使用して 2 つの四角形を塗りつぶす例を示します。  最初の四角形はガンマ補正を適用せずに塗りつぶされ、2 番目の四角形はガンマ補正を適用して塗りつぶされます。  
  
 2 つの塗りつぶされた四角形を次の図に示します。  ガンマ補正が適用されていない上の四角形は、中央の部分が暗くなっています。  ガンマ補正が適用されている下の四角形は、輝度がより均等化されているように見えます。  
  
 ![グラデーション](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>   
 [グラデーション ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)