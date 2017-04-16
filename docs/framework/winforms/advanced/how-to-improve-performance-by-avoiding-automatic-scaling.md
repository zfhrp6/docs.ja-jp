---
title: "方法 : 自動スケーリングを解除してパフォーマンスを向上させる | Microsoft Docs"
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
  - "自動スケーリング"
  - "イメージ [Windows フォーム], 向上 (パフォーマンスを)"
  - "イメージ [Windows フォーム], 使用 (自動スケーリングなしで)"
  - "パフォーマンス, 向上 (イメージ)"
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 自動スケーリングを解除してパフォーマンスを向上させる
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、イメージを描画すると自動的にそのイメージがスケーリングされ、これによりパフォーマンスが低下する場合があります。  別の方法として、描画先の四角形の寸法を <xref:System.Drawing.Graphics.DrawImage%2A> メソッドに渡すと、イメージのスケーリングを制御できます。  
  
 たとえば、次の <xref:System.Drawing.Graphics.DrawImage%2A> メソッドの呼び出しでは、左上隅の値 \(50, 30\) を指定していますが、描画先の四角形は指定していません。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 これは、指定する引数の数が少なくて済むという点では一番簡単な形式の <xref:System.Drawing.Graphics.DrawImage%2A> メソッドですが、必ずしも効率的な形式ではありません。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] によって使用される解像度 \(通常は 96 dpi\) が <xref:System.Drawing.Image> オブジェクトに格納されている解像度と異なる場合、イメージは <xref:System.Drawing.Graphics.DrawImage%2A> メソッドによってスケーリングされます。  たとえば、<xref:System.Drawing.Image> オブジェクトの幅が 216 ピクセルで、格納されている水平方向の解像度の値が 72 dpi であるとします。  216\/72 は 3 なので、<xref:System.Drawing.Graphics.DrawImage%2A> は、96 dpi の解像度で幅が 3 インチになるようにイメージをスケーリングします。  つまり、<xref:System.Drawing.Graphics.DrawImage%2A> は、96 × 3 \= 288 ピクセルの幅でイメージを表示します。  
  
 画面解像度が 96 dpi ではない場合でも、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は解像度が 96 dpi であるものとしてイメージをスケーリングします。  これは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> オブジェクトがデバイス コンテキストに関連付けられているためです。一般的に、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] がデバイス コンテキストに画面解像度を照会すると、実際の画面解像度がどうなっているかにかかわらず、結果は 96 になります。  <xref:System.Drawing.Graphics.DrawImage%2A> メソッドで描画先の四角形を指定すると、自動スケーリングを解除できます。  
  
## 使用例  
 同じイメージを 2 回描画する例を次に示します。  1 回目は、描画先の四角形の幅と高さを指定していないため、イメージが自動的にスケーリングされます。  2 回目には、描画先の四角形の幅と高さ \(ピクセル単位\) が、元のイメージの幅と高さと同じになるように指定されています。  2 回描画された結果のイメージを次の図に示します。  
  
 ![スケール テクスチャ](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  Texture.jpg は、システム上で有効なイメージの名前とパスに置き換えてください。  
  
## 参照  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)