---
title: "方法 : カラー行列を使用して単一色を変換する | Microsoft Docs"
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
  - "カラー行列, 使用"
  - "イメージ カラー, 変換"
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : カラー行列を使用して単一色を変換する
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、イメージの格納および操作のために、<xref:System.Drawing.Image> クラスおよび <xref:System.Drawing.Bitmap> クラスを提供しています。  <xref:System.Drawing.Image> オブジェクトおよび <xref:System.Drawing.Bitmap> オブジェクトは、各ピクセルの色として、赤、緑、青、およびアルファそれぞれに 8 ビットずつ割り当てた 32 ビットの数値を格納します。  4 つの各要素は、0 から 255 までの数値で表され、0 は輝度がないことを表し、255 は最大の輝度を表します。  アルファ要素は、色の透明度を指定します。0 は完全な透明を表し、255 は完全な不透明を表します。  
  
 カラー ベクターは、4 つの要素 \(赤、緑、青、アルファ\) から成る集合です。  たとえば、カラー ベクター \(0, 255, 0, 255\) は、赤と青に輝度がなく、緑の輝度が最大である不透明な色を表します。  
  
 色を表すための別の規則では、数値 1 を使用して最大の輝度を表します。  その規則を使用すると、上の段落で説明した色はベクター \(0, 1, 0, 1\) で表されます。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、色の変換を行うときに、最大の輝度を 1 で表す規則を使用します。  
  
 カラー ベクターに 4 × 4 の行列を掛け合わせることによって、そのカラー ベクターに線形変換 \(回転、スケーリングなど\) を適用できます。  しかし、線形変換ではない平行移動を行うために、4 × 4 の行列は使用できません。  ダミーとして 5 番目の座標 \(たとえば、数字 1\) を各カラー ベクターに追加すると、5 × 5 の行列を使用して、線形変換と平行移動を任意に組み合わせて適用できます。  線形変換に続いて平行移動を実行する変換をアフィン変換と呼びます。  
  
 たとえば、色 \(0.2, 0.0, 0.4, 1.0\) から開始して、次の変換を適用するとします。  
  
1.  赤の要素を 2 倍にします。  
  
2.  赤、緑、青の各要素に 0.2 を追加します。  
  
 次の行列の掛け合わせによって、ペアになっている変換が、リストに示されている順序で実行されます。  
  
 ![色変更](../../../../docs/framework/winforms/advanced/media/recoloring01.png "recoloring01")  
  
 カラー行列の要素には、行そして列ごとに 0 から始まるインデックスが付けられます。  たとえば、行列 M の 5 行目および 3 列目のエントリは、M \[4\]\[2\] と表記されます。  
  
 次の図に示す 5 × 5 の単位行列には、対角線上に 1、それ以外のすべての位置に 0 が格納されています。  カラー ベクターとこの単位行列を掛け合わせても、そのカラー ベクターは変化しません。  カラー変換の行列を形成する簡単な方法として、単位行列から着手し、必要な変換を生成できるように微調整していく方法があります。  
  
 ![色変更](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")  
  
 行列と変換の詳細については、「[座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)」を参照してください。  
  
## 使用例  
 全体が 1 つの色 \(0.2, 0.0, 0.4, 1.0\) であるイメージに、上の段落で説明した変換を適用する例を次に示します。  
  
 次の図は、左側に元のイメージ、右側に変換後のイメージを示しています。  
  
 ![色](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")  
  
 次のコード例では、以下の手順で色の変更が行われます。  
  
1.  <xref:System.Drawing.Imaging.ColorMatrix> オブジェクトを初期化します。  
  
2.  <xref:System.Drawing.Imaging.ImageAttributes> オブジェクトを作成し、<xref:System.Drawing.Imaging.ImageAttributes> オブジェクトの <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> メソッドに <xref:System.Drawing.Imaging.ColorMatrix> オブジェクトを渡します。  
  
3.  <xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.DrawImage%2A> メソッドに <xref:System.Drawing.Imaging.ImageAttributes> オブジェクトを渡します。  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [イメージの色の変更](../../../../docs/framework/winforms/advanced/recoloring-images.md)   
 [座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)