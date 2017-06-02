---
title: "方法 : イメージをトリミングおよびスケーリングする | Microsoft Docs"
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
  - "イメージ [Windows フォーム], トリミング"
  - "イメージ [Windows フォーム], スケーリング"
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : イメージをトリミングおよびスケーリングする
<xref:System.Drawing.Graphics> クラスでは、<xref:System.Drawing.Graphics.DrawImage%2A> メソッドがいくつか用意されています。その中には、描画元の範囲を表す四角形パラメーターや、描画先の範囲を表す四角形パラメーターを受け取るメソッドもあり、これらはイメージをトリミングおよびスケーリングするために使用できます。  
  
## 使用例  
 ディスク ファイル Apple.gif から <xref:System.Drawing.Image> オブジェクトを作成する例を次に示します。  このコードは、リンゴのイメージ全体を元のサイズで描画します。  次に、<xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.DrawImage%2A> メソッドを呼び出して、リンゴのイメージの一部を、元のリンゴのイメージよりも大きな描画先の四角形に描画します。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> メソッドは、3 番目、4 番目、5 番目、6 番目の各引数によって指定されている、描画元の範囲を表す四角形を参照し、リンゴのどの部分を描画するかを決定します。  この場合は、リンゴの幅と高さがそれぞれの 75% になるようにトリミングされます。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> メソッドは、2 番目の引数によって指定されている、描画先の範囲を表す四角形を参照して、トリミングしたリンゴのイメージの描画位置と、そのイメージをどれくらいの大きさで描画するかを決定します。  この例では、描画先の範囲を表す四角形は、元のイメージよりも幅、高さ共に 30% 大きく指定されています。  
  
 元のリンゴと、スケーリングおよびトリミングしたリンゴを次の図に示します。  
  
 ![トリミング & スケール](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  `Apple.gif` は、必ずシステム上で有効なイメージ ファイルの名前とパスに置き換えてください。  
  
## 参照  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)