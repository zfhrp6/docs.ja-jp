---
title: "方法: 既存のビットマップを画面に描画する | Microsoft Docs"
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
  - "ビットマップ [Windows フォーム], 表示 (Windows フォームで)"
  - "ビットマップ [Windows フォーム], 読み込み (Windows フォーム アプリケーションに)"
  - "イメージ [Windows フォーム], 表示 (Windows フォームに)"
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法: 既存のビットマップを画面に描画する
既存のイメージを画面上に簡単に描画できます。  まず、ファイル名として <xref:System.Drawing.Bitmap.%23ctor%28System.String%29> を受け取るビットマップ コンストラクターを使用して、<xref:System.Drawing.Bitmap> オブジェクトを作成する必要があります。  このコンストラクターでは、BMP、GIF、JPEG、PNG、TIFF などのさまざまなファイル形式のイメージを使用できます。  <xref:System.Drawing.Bitmap> オブジェクトを作成した後に、その <xref:System.Drawing.Bitmap> オブジェクトを <xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.DrawImage%2A> メソッドに渡します。  
  
## 使用例  
 JPEG ファイルから <xref:System.Drawing.Bitmap> オブジェクトを作成し、左上隅が \(60, 10\) の位置にあるビットマップを描画する例を次に示します。  
  
 指定された位置に描画されたビットマップを次の図に示します。  
  
 ![イメージ ポジション](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)