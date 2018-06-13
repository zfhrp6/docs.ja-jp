---
title: GDI+ でのイメージのトリミングおよびスケーリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
ms.openlocfilehash: 84e2e74e71c13593cb013849c07a6e904a4d2c14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521555"
---
# <a name="cropping-and-scaling-images-in-gdi"></a>GDI+ でのイメージのトリミングおよびスケーリング
使用することができます、<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>を描画して、ベクター イメージとラスター イメージを配置するクラス。 <xref:System.Drawing.Graphics.DrawImage%2A> 引数を指定することがいくつかの方法があるため、オーバー ロードされたメソッドは、します。  
  
## <a name="drawimage-variations"></a>DrawImage のバリエーション  
 1 つのバリエーション、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドは受信、<xref:System.Drawing.Bitmap>と<xref:System.Drawing.Rectangle>です。 四角形を描画操作のシリアル化先を指定しますつまり、イメージを描画する四角形を指定します。 移行先の四角形のサイズが元のイメージのサイズと異なる場合は、イメージは移行先の四角形に合わせてスケーリングされます。 次のコード例は、3 回、同じイメージを描画する方法を示しています: スケーリングなしで、拡大、および、圧縮を使用します。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 次の図は、3 つの画像を示します。  
  
 ![スケーリング](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 いくつかのバリエーション、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドは、元の四角形のパラメーターだけでなく、移行先の四角形のパラメーターがあります。 元の四角形のパラメーターは、描画する元のイメージの一部を指定します。 先の四角形は、イメージの部分を描画する四角形を指定します。 先の四角形のサイズが元の四角形のサイズと異なる場合は、画像は移行先の四角形に合わせてスケーリングされます。  
  
 次のコード例を作成する方法を示しています、 <xref:System.Drawing.Bitmap> Runner.jpg ファイルからです。 位置にスケーリングなしで画像全体が描画された (0, 0) です。 イメージの一部が 2 回描画し、: 圧縮が 1 回 1 回、および拡大します。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 次の図は、スケールなしのイメージとイメージの圧縮および展開されている部分を示します。  
  
 ![トリミングとスケーリング](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>関連項目  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
