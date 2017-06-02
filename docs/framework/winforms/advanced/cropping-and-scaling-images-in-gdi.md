---
title: "GDI+ でのイメージのトリミングおよびスケーリング | Microsoft Docs"
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
  - "圧縮 (データを), イメージ"
  - "GDI+, トリミング (イメージを)"
  - "GDI+, スケーリング (イメージの)"
  - "イメージ [Windows フォーム], 圧縮"
  - "イメージ [Windows フォーム], トリミング"
  - "イメージ [Windows フォーム], 展開"
  - "イメージ [Windows フォーム], スケーリング"
  - "四角形, 描画先"
  - "四角形, source"
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# GDI+ でのイメージのトリミングおよびスケーリング
<xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawImage%2A> メソッドを使用して、ベクター イメージとラスター イメージを描画および配置できます。  <xref:System.Drawing.Graphics.DrawImage%2A> はオーバーロードされたメソッドであるため、いくつかの方法でこのメソッドの引数を指定できます。  
  
## DrawImage のバリエーション  
 ある <xref:System.Drawing.Graphics.DrawImage%2A> メソッドは、<xref:System.Drawing.Bitmap> と <xref:System.Drawing.Rectangle> を受け取ります。  四角形は、描画操作の範囲を指定します。つまり、イメージが描画される先の四角形を指定します。  描画先の四角形のサイズと元のイメージのサイズが異なる場合、イメージは、描画先の四角形と一致するようにスケーリングされます。  スケーリングなし、拡大、および縮小の操作をそれぞれ適用して、同じイメージを 3 回描画するコード例を次に示します。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 3 つのピクチャを次の図に示します。  
  
 ![スケーリング](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.png "AboutGdip03\_Art06")  
  
 描画元の四角形パラメーターと描画先の四角形パラメーターを使用する <xref:System.Drawing.Graphics.DrawImage%2A> メソッドもあります。  描画元の四角形パラメーターは、描画する元のイメージの部分を指定します。  描画先の四角形は、イメージのその部分が描画される先の四角形を指定します。  描画先の四角形のサイズと描画元の四角形のサイズが異なる場合、ピクチャは、描画先の四角形と一致するようにスケーリングされます。  
  
 Runner.jpg ファイルから <xref:System.Drawing.Bitmap> オブジェクトを構築するコード例を次に示します。  イメージ全体が \(0, 0\) の位置にスケーリングなしで描画されます。  次に、縮小と拡大の操作をそれぞれ適用して、イメージの小さい部分が 2 回描画されます。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 スケーリングなしのイメージ、縮小されたイメージ部分、および拡大されたイメージ部分を次の図に示します。  
  
 ![トリミングとスケーリング](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.png "AboutGdip03\_Art07")  
  
## 参照  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)