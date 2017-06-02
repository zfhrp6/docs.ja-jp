---
title: "グラデーション ブラシを使用した図形の塗りつぶし | Microsoft Docs"
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
  - "ブラシ, グラデーション ブラシ"
  - "例 [Windows フォーム], グラデーション ブラシ"
  - "グラデーション ブラシ"
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# グラデーション ブラシを使用した図形の塗りつぶし
グラデーション ブラシを使用して、段階的に色を変化させて 1 つの図形を塗りつぶすことができます。  たとえば、水平方向のグラデーションを使用して、図形の左端から右端に移動するにつれて色が段階的に変化するように図形を塗りつぶすことができます。  左端が黒 \(赤、緑、青の各要素が \(0, 0, 0\) で表される\) で右端が赤 \(255, 0, 0\) の四角形があると想定します。  この四角形の幅が 256 ピクセルだとすると、あるピクセルの赤の要素は、その左側にあるピクセルの赤の要素よりも 1 大きい値になります。  一列に並んだピクセルの左端のピクセルの色要素は \(0, 0, 0\)、2 番目のピクセルは \(1, 0, 0\)、3 番目のピクセルは \(2, 0, 0\) となり、その後も同様に、色要素が \(255, 0, 0\) の右端のピクセルに達するまで続いていきます。  これらの補間色の値によって色のグラデーションが構成されます。  
  
 線形グラデーションでは、水平方向、垂直方向、または指定した斜線と並行方向に移動するにつれて色が変化します。  パス グラデーションでは、パスの内側および境界周辺を移動するにつれて色が変化します。  パス グラデーションをカスタマイズして、さまざまな効果を得ることができます。  
  
 線形グラデーション ブラシで塗りつぶした四角形と、パス グラデーション ブラシで塗りつぶした楕円を次の図に示します。  
  
 ![グラデーション](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")  
  
## このセクションの内容  
 [方法 : 線形グラデーションを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush> クラスを使用して線形グラデーションを作成する方法を示します。  
  
 [方法 : パス グラデーションを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 <xref:System.Drawing.Drawing2D.PathGradientBrush> クラスを使用してパス グラデーションを作成する方法を説明します。  
  
 [方法 : グラデーションに対してガンマ補正を適用する](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 グラデーション ブラシでガンマ補正を使用する方法を説明します。  
  
## 関連項目  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=fullName>  
 このクラスについて説明し、そのすべてのメンバーへのリンクを示します。  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=fullName>  
 このクラスについて説明し、そのすべてのメンバーへのリンクを示します。