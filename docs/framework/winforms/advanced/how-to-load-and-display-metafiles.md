---
title: "方法 : メタファイルを読み込んで表示する"
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
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 722b6d36801c69e500535a32e952ef8f45634d03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-load-and-display-metafiles"></a>方法 : メタファイルを読み込んで表示する
<xref:System.Drawing.Imaging.Metafile>から継承されるクラスが、<xref:System.Drawing.Image>クラス、記録、表示、およびベクター イメージを検証するメソッドを提供します。  
  
## <a name="example"></a>例  
 画面にベクター イメージ (メタファイル) を表示する必要があります、<xref:System.Drawing.Imaging.Metafile>オブジェクトおよび<xref:System.Drawing.Graphics>オブジェクト。 名前のファイル (またはストリーム) に渡す、<xref:System.Drawing.Imaging.Metafile>コンス トラクターです。 作成した後、<xref:System.Drawing.Imaging.Metafile>オブジェクトを渡す<xref:System.Drawing.Imaging.Metafile>オブジェクトを<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。  
  
 例は、作成、 <xref:System.Drawing.Imaging.Metafile> EMF (メタファイル) ファイルからオブジェクトで、左上隅にイメージを描画と (60, 10)。  
  
 次の図は、指定した位置に描画するメタファイルを示します。  
  
 ![画像の位置](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
