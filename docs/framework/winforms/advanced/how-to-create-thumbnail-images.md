---
title: "方法 : サムネイル イメージを作成する | Microsoft Docs"
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
  - "イメージ [Windows フォーム], 作成 (サムネイル)"
  - "サムネイル イメージ, 作成"
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 方法 : サムネイル イメージを作成する
サムネイル イメージとは、イメージの縮小版のことです。  サムネイル イメージを作成するには、<xref:System.Drawing.Image> オブジェクトの <xref:System.Drawing.Image.GetThumbnailImage%2A> メソッドを呼び出します。  
  
## 使用例  
 JPG ファイルから <xref:System.Drawing.Image> オブジェクトを作成する例を次に示します。  元のイメージの幅は 640 ピクセルで、高さは 479 ピクセルです。  このコードは、幅および高さが共に 100 ピクセルのサムネイル イメージを作成します。  
  
 作成されたサムネイル イメージを次の図に示します。  
  
 ![サムネイル イメージ](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  この例では、コールバック メソッドが宣言されていますが、使用しません。  このメソッドは GDI\+ のすべてのバージョンをサポートします。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  この例を実行するには、次の手順に従います。  
  
1.  新しい Windows フォームアプリケーションを作成します。  
  
2.  プログラム例をフォームに追加します。  
  
3.  フォームの <xref:System.Windows.Forms.Control.Paint> イベントのハンドラーを作成します。  
  
4.  <xref:System.Windows.Forms.Control.Paint> ハンドラーで、`GetThumbnail` メソッドを呼び出し、<xref:System.Windows.Forms.PaintEventArgs> の `e` を渡します。  
  
5.  サムネイルを作成するイメージ ファイルを見つけます。  
  
6.  `GetThumbnail` メソッドで、イメージのパスとファイル名を指定します。  
  
7.  F5 キーを押して例を実行します。  
  
     100 × 100 のサムネイル イメージがフォーム上に表示されます。  
  
## 参照  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)