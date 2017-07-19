---
title: "方法 : イメージ テクスチャによって図形を塗りつぶす | Microsoft Docs"
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
  - "ビットマップ [Windows フォーム], 使用 (テクスチャを)"
  - "イメージ [Windows フォーム], 使用 (ブラシと共に)"
  - "形状, 塗りつぶし (イメージで)"
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : イメージ テクスチャによって図形を塗りつぶす
<xref:System.Drawing.Image> クラスおよび <xref:System.Drawing.TextureBrush> クラスを使用することによって、閉じている図形をテクスチャで塗りつぶすことができます。  
  
## 使用例  
 楕円をイメージで塗りつぶす例を次に示します。  このコードは、<xref:System.Drawing.Image> オブジェクトを作成し、その <xref:System.Drawing.Image> オブジェクトのアドレスを <xref:System.Drawing.TextureBrush.%23ctor%2A> コンストラクターに引数として渡します。  3 番目のステートメントでそのイメージを縮小し、4 番目のステートメントでは、縮小したイメージのコピーを繰り返したパターンによって楕円を塗りつぶしています。  
  
 次のコードでは、<xref:System.Drawing.TextureBrush.Transform%2A> プロパティに、イメージが描画される前にそのイメージに適用される変換方法が指定されています。  元のイメージの幅が 640 ピクセルで、高さが 480 ピクセルであることを前提とします。  この変換では、水平方向と垂直方向のスケーリング値を設定することによって、イメージを 75 × 75 に縮小します。  
  
> [!NOTE]
>  次の例では、イメージのサイズが 75 × 75 で、楕円のサイズが 150 × 250 です。  イメージの方が、そのイメージで塗りつぶす対象の楕円よりも小さいため、イメージを並べたパターンによって楕円が表示されます。  イメージを並べるとは、塗りつぶし対象の図形の境界に達するまで、イメージを水平方向と垂直方向に繰り返して表示することを意味します。  イメージを並べて表示する方法の詳細については、「[方法 : イメージを並べたパターンによって図形を塗りつぶす](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md)」を参照してください。  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)