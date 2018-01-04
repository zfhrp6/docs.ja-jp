---
title: "方法: 既存のビットマップを画面に描画する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b3c8aef4aee74fbcdcc80301f5d5c1020883341
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a>方法: 既存のビットマップを画面に描画する
画面で、既存のイメージを簡単に描画できます。 最初に作成する必要があります、<xref:System.Drawing.Bitmap>オブジェクトは、ファイル名を受け取り、ビットマップ コンス トラクターを使用して<xref:System.Drawing.Bitmap.%23ctor%28System.String%29>です。 このコンス トラクターは、BMP、GIF、JPEG、PNG、TIFF を含め、いくつかの異なるファイル形式で画像を受け入れます。 作成した後、<xref:System.Drawing.Bitmap>オブジェクトを渡す<xref:System.Drawing.Bitmap>オブジェクトを<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。  
  
## <a name="example"></a>例  
 この例で作成、 <xref:System.Drawing.Bitmap> JPEG ファイルからオブジェクトで、左上隅のビットマップを描画と (60, 10)。  
  
 次の図は、指定した位置に描画されるビットマップを示します。  
  
 ![画像の位置](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>参照  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
