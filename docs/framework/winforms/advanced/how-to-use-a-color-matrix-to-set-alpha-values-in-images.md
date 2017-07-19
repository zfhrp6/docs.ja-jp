---
title: "方法 : カラー行列を使用してイメージのアルファ値を設定する | Microsoft Docs"
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
  - "ビットマップ [Windows フォーム], 使用 (半透明にするためにカラー行列を)"
  - "イメージ [Windows フォーム], 使用 (半透明にするためにカラー行列を)"
  - "行列, アルファ値"
  - "透明度, カラー行列"
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : カラー行列を使用してイメージのアルファ値を設定する
<xref:System.Drawing.Bitmap> クラス \(<xref:System.Drawing.Image> クラスから継承\) および <xref:System.Drawing.Imaging.ImageAttributes> クラスには、ピクセル値を取得したり設定したりするための機能が用意されています。  <xref:System.Drawing.Imaging.ImageAttributes> クラスを使用してイメージ全体のアルファ値を変更したり、<xref:System.Drawing.Bitmap> クラスの <xref:System.Drawing.Bitmap.SetPixel%2A> メソッドを呼び出して個々のピクセル値を変更したりできます。  
  
## 使用例  
 <xref:System.Drawing.Imaging.ImageAttributes> クラスには多数のプロパティがあり、これらのプロパティを使用して、描画中のイメージを修正できます。  <xref:System.Drawing.Imaging.ImageAttributes> オブジェクトを使用して、すべてのアルファ値を元の 80% の値に設定する例を次に示します。  このためには、カラー行列を初期化し、行列内のアルファ スケーリング値を 0.8 に設定します。  カラー行列のアドレスが<xref:System.Drawing.Imaging.ImageAttributes> オブジェクトの <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> メソッドに渡され、<xref:System.Drawing.Imaging.ImageAttributes> オブジェクトが <xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.DrawString%2A> メソッドに渡されます。  
  
 描画中に、ビットマップのアルファ値が、元の 80% の値に変換されます。  これにより、描画されるイメージが、背景とブレンドされるようになります。  次の図で示すように、ビットマップ イメージは透明に見えるため、そのイメージを透過して黒の実線を見ることができます。  
  
 ![行列を使用したアルファ ブレンド](../../../../docs/framework/winforms/advanced/media/image2.png "image2")  
  
 イメージが背景の白い部分の上にあるところでは、そのイメージ部分が白色とブレンドされています。  イメージが黒い線を横切るところでは、そのイメージ部分が黒色とブレンドされます。  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [アルファ ブレンドの直線と塗りつぶし](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)