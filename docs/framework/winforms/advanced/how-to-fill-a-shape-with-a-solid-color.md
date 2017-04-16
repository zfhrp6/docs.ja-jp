---
title: "方法 : 純色で図形を塗りつぶす | Microsoft Docs"
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
  - "色, 追加 (図形に)"
  - "形状, 塗りつぶし"
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 純色で図形を塗りつぶす
図形を純色で塗りつぶすには、<xref:System.Drawing.SolidBrush> オブジェクトを作成し、その <xref:System.Drawing.SolidBrush> オブジェクトを、<xref:System.Drawing.Graphics> クラスの塗りつぶしメソッドの 1 つに引数として渡します。  楕円を赤色で塗りつぶす方法を次の例に示します。  
  
## 使用例  
 次のコードでは、<xref:System.Drawing.SolidBrush.%23ctor%2A> コンストラクターの唯一の引数として <xref:System.Drawing.Color> オブジェクトが渡されています。  <xref:System.Drawing.Color.FromArgb%2A> メソッドで使用されている値は、それぞれ、アルファ、赤、緑、および青の色要素を表します。  これらの各値は、0 から 255 までの範囲内にする必要があります。  最初の 255 は、色の不透明度が最大であることを示し、2 番目の 255 は赤の要素の輝度が最大であることを示します。  残りの 2 つの 0 は、緑と青の要素の輝度が共に 0 であることを示します。  
  
 <xref:System.Drawing.Graphics.FillEllipse%2A> メソッドに渡される 4 つの数値 \(0, 0, 100, 60\) は、楕円に外接する四角形の位置とサイズを指定しています。  この四角形は、左上隅が \(0, 0\) の位置にあり、幅が 100、高さが 60 です。  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)