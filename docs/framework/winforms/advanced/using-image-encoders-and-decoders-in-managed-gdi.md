---
title: マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: b2e51587209cb4df41ea1fd18ce5c2088ee07a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524502"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用
<xref:System.Drawing>名前空間には、<xref:System.Drawing.Image>と<xref:System.Drawing.Bitmap>を格納して、画像を操作するためのクラスです。 イメージ エンコーダーを使用して、 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、メモリからディスク イメージを記述することができます。 イメージのデコーダーを使用して、 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、ディスクからイメージをメモリに読み込むことができます。 内のデータを変換するエンコーダー、<xref:System.Drawing.Image>または<xref:System.Drawing.Bitmap>オブジェクト、指定されたディスク ファイル形式に変換します。 必要な形式にディスク ファイル内のデータを変換するデコーダー、<xref:System.Drawing.Image>と<xref:System.Drawing.Bitmap>オブジェクト。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 組み込みエンコーダーとデコーダー ファイルの種類をサポートするにがあります。  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 次のファイルの種類をサポートする組み込みのデコーダーがあります。  
  
-   WMF  
  
-   EMF  
  
-   アイコン  
  
 次のトピックでは、エンコーダーとデコーダーの詳細について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: インストールされたエンコーダーの一覧](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 コンピューターで使用可能なエンコーダーの一覧を表示する方法について説明します。  
  
 [方法: インストールされたデコーダーの一覧](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 コンピューターで使用できるデコーダーの一覧を表示する方法について説明します。  
  
 [方法: エンコーダーがサポートするパラメーターの確認](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 一覧表示する方法について説明します、<xref:System.Drawing.Imaging.EncoderParameters>エンコーダーがサポートされます。  
  
 [方法: BMP イメージから PNG イメージへの変換](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 さまざまなイメージ形式で、イメージを保存する方法について説明します。  
  
 [方法: JPEG 圧縮レベルの設定](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 イメージの品質レベルを変更する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>関連項目  
 [GDI+ マネージ コードについて](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
