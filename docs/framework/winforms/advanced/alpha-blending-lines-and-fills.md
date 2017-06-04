---
title: "アルファ ブレンドの直線と塗りつぶし | Microsoft Docs"
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
  - "アルファ ブレンド"
  - "アルファ ブレンド, 使用 (塗りつぶしで)"
  - "アルファ ブレンド, 使用 (直線で)"
  - "例 [Windows フォーム], アルファ ブレンド"
  - "塗りつぶし, アルファ ブレンド"
  - "線, 追加 (透明度を)"
  - "線, アルファ ブレンド"
  - "形状, 追加 (透明度を)"
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# アルファ ブレンドの直線と塗りつぶし
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、アルファ、赤、緑、青の各要素に 8 ビットずつ割り当てた 32 ビット値で色を表します。  アルファ値は、色の透明度、つまり、色を背景色とブレンドする度合いを示します。  アルファ値の範囲は 0 から 255 までです。0 は色の透明度が最大であることを表し、255 は色の不透明度が最大であることを表します。  
  
 アルファ ブレンドでは、ソース カラーのデータと背景色のデータをピクセルごとにブレンドします。  ソース カラーの 3 つの各要素 \(赤、緑、青\) は、次の数式に基づいて、背景色の対応する要素とブレンドされます。  
  
 displayColor \= sourceColor × alpha \/ 255 \+ backgroundColor × \(255 – alpha\) \/ 255  
  
 たとえば、ソース カラーの赤の要素が 150、背景色の赤の要素が 100 だとします。  アルファ値が 200 の場合、生成される色の赤の要素は、次のように計算されます。  
  
 150 × 200 \/ 255 \+ 100 × \(255 – 200\) \/ 255 \= 139  
  
## このセクションの内容  
 [方法 : 不透明な直線および半透明な直線を描画する](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 アルファ ブレンドされた線を描画する方法を示します。  
  
 [方法 : 不透明ブラシおよび半透明ブラシを使用して描画する](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 ブラシでアルファ ブレンドする方法を説明します。  
  
 [方法 : 複合モードを使用してアルファ ブレンドを制御する](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 <xref:System.Drawing.Drawing2D.CompositingMode> を使用してアルファ ブレンドを制御する方法を説明します。  
  
 [方法 : カラー行列を使用してイメージのアルファ値を設定する](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 <xref:System.Drawing.Imaging.ColorMatrix> オブジェクトを使用してアルファ ブレンドを制御する方法を説明します。