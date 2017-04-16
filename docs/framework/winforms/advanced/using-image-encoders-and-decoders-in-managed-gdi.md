---
title: "マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用 | Microsoft Docs"
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
  - "イメージ デコーダー, 使用"
  - "イメージ エンコーダー, 使用"
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用
<xref:System.Drawing> 名前空間は、イメージの格納および操作のための <xref:System.Drawing.Image> クラスおよび <xref:System.Drawing.Bitmap> クラスを提供します。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] でイメージ エンコーダーを使用すると、メモリからディスクにイメージを書き込むことができます。[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] でイメージ デコーダーを使用すると、ディスクからメモリにイメージを読み込むことができます。  エンコーダーは、<xref:System.Drawing.Image> オブジェクトまたは <xref:System.Drawing.Bitmap> オブジェクトのデータを指定のディスク ファイル形式に変換します。  デコーダーは、ディスク ファイルのデータを <xref:System.Drawing.Image> オブジェクトおよび <xref:System.Drawing.Bitmap> オブジェクトで必要とされる形式に変換します。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] には、次のファイルの種類をサポートするエンコーダーおよびデコーダーが組み込まれています。  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] には、次のファイルの種類をサポートするデコーダーも組み込まれています。  
  
-   WMF  
  
-   EMF  
  
-   ICON  
  
 以下のトピックでは、エンコーダーとデコーダーについて詳細に説明します。  
  
## このセクションの内容  
 [方法 : インストールされたエンコーダーの一覧](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 コンピューター上で使用できるエンコーダーを一覧表示する方法について説明します。  
  
 [方法 : インストールされたデコーダーの一覧](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 コンピューター上で使用できるデコーダーを一覧表示する方法について説明します。  
  
 [方法 : エンコーダーがサポートするパラメーターの確認](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 エンコーダーがサポートする <xref:System.Drawing.Imaging.EncoderParameters> を一覧表示する方法について説明します。  
  
 [方法 : BMP イメージから PNG イメージへの変換](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 さまざまなイメージ形式でイメージを保存する方法について説明します。  
  
 [方法 : JPEG 圧縮レベルの設定](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 イメージの品質レベルを変更する方法について説明します。  
  
## 関連項目  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## 関連項目  
 [GDI\+ マネージ コードについて](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)