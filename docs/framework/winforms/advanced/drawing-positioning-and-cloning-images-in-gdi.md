---
title: GDI+ でのイメージの描画、配置、およびクローン作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
ms.openlocfilehash: 5ff502884874e21e8f34acb2f15db4c651a0a273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521652"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>GDI+ でのイメージの描画、配置、およびクローン作成
使用することができます、<xref:System.Drawing.Bitmap>を読み込んでラスター イメージを表示するクラスが使用することができます、<xref:System.Drawing.Imaging.Metafile>クラスをロードおよびベクター イメージを表示します。 <xref:System.Drawing.Bitmap>と<xref:System.Drawing.Imaging.Metafile>クラスの継承元、<xref:System.Drawing.Image>クラスです。 インスタンスを表示するには、ベクター イメージ必要、<xref:System.Drawing.Graphics>クラスおよび<xref:System.Drawing.Imaging.Metafile>です。 ラスター イメージを表示する必要がありますのインスタンス、<xref:System.Drawing.Graphics>クラスおよび<xref:System.Drawing.Bitmap>です。 インスタンス、<xref:System.Drawing.Graphics>クラスを提供、<xref:System.Drawing.Graphics.DrawImage%2A>を受信するメソッド、<xref:System.Drawing.Imaging.Metafile>または<xref:System.Drawing.Bitmap>を引数として。  
  
## <a name="file-types-and-cloning"></a>ファイルの種類と複製  
 次のコード例を作成する方法を示しています、 <xref:System.Drawing.Bitmap> Climber.jpg ファイルからビットマップを表示します。 イメージの左上隅の終点 (10, 10) は、2 番目と 3 番目のパラメーターで指定します。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 次の図は、イメージを示します。  
  
 ![サンプルをイメージ](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 構築できます<xref:System.Drawing.Bitmap>グラフィックスのさまざまなオブジェクト ファイル形式: BMP、GIF、JPEG、EXIF、PNG、TIFF、およびアイコン。  
  
 次のコード例は、作成する方法を示しています。<xref:System.Drawing.Bitmap>さまざまな種類のファイルからのオブジェクトとし、ビットマップを表示します。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap>クラスを提供する<xref:System.Drawing.Bitmap.Clone%2A>、既存のコピーを作成するを使用できるメソッド<xref:System.Drawing.Bitmap>です。 <xref:System.Drawing.Bitmap.Clone%2A>メソッドにソース四角形パラメーターがあり、使用することができますにコピーする元のビットマップの部分を指定します。 次のコード例を作成する方法を示しています、 <xref:System.Drawing.Bitmap> 、既存の上半分を複製して<xref:System.Drawing.Bitmap>です。 次に、両方のイメージが描画します。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 次の図は、2 つのイメージを示します。  
  
 ![トリミング](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>関連項目  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [方法: 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
