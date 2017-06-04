---
title: "方法 : メタファイルを読み込んで表示する | Microsoft Docs"
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
  - "例 [Windows フォーム], メタファイル"
  - "メタファイル, 表示"
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : メタファイルを読み込んで表示する
<xref:System.Drawing.Imaging.Metafile> クラスは、<xref:System.Drawing.Image> クラスから継承したクラスで、ベクター イメージを記録、表示、チェックするためのメソッドが用意されています。  
  
## 使用例  
 画面にベクター イメージ \(メタファイル\) を表示するには、<xref:System.Drawing.Imaging.Metafile> オブジェクトと <xref:System.Drawing.Graphics> オブジェクトが必要です。  ファイルまたはストリームの名前を <xref:System.Drawing.Imaging.Metafile> コンストラクターに渡します。  <xref:System.Drawing.Imaging.Metafile> オブジェクトを作成した後に、その <xref:System.Drawing.Imaging.Metafile> オブジェクトを <xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.DrawImage%2A> メソッドに渡します。  
  
 例では、EMF ファイル \(拡張メタファイル\) から <xref:System.Drawing.Imaging.Metafile> オブジェクトを作成し、左上隅が \(60, 10\) の位置にあるイメージを描画します。  
  
 指定された位置に描画されたメタファイルを次の図に示します。  
  
 ![イメージ ポジション](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)