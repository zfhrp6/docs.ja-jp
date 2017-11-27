---
title: "方法 : カラー リマップ テーブルを使用する"
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
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1c4399e98504a675cfbf63462b8dc964c677488e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-remap-table"></a>方法 : カラー リマップ テーブルを使用する
再マップは、カラー リマップ テーブルに従ってイメージの色を変換するプロセスです。 カラー リマップ テーブルの配列は、<xref:System.Drawing.Imaging.ColorMap>オブジェクト。 各<xref:System.Drawing.Imaging.ColorMap>配列内のオブジェクトは、<xref:System.Drawing.Imaging.ColorMap.OldColor%2A>プロパティおよび<xref:System.Drawing.Imaging.ColorMap.NewColor%2A>プロパティです。  
  
 ときに[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]イメージを各ピクセルのイメージの描画が古い色の配列と比較します。 ピクセルの色には、既存の色が一致すると、その色が、対応する新しい色に変更されます。 レンダリングののみ、色が変更されて、イメージ自体のカラー値 (に格納されている、<xref:System.Drawing.Image>または<xref:System.Drawing.Bitmap>オブジェクト) は変更されません。  
  
 配列を初期化、再マップされたイメージを描画する<xref:System.Drawing.Imaging.ColorMap>オブジェクト。 その配列を渡す、<xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A>のメソッド、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクト、および、渡す、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクトを<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。  
  
## <a name="example"></a>例  
 次の例を作成、 <xref:System.Drawing.Image> RemapInput.bmp ファイルからオブジェクト。 コードが単一のカラー リマップ テーブルを作成<xref:System.Drawing.Imaging.ColorMap>オブジェクト。 <xref:System.Drawing.Imaging.ColorMap.OldColor%2A>のプロパティ、`ColorRemap`オブジェクトは、赤、および<xref:System.Drawing.Imaging.ColorMap.NewColor%2A>プロパティは青です。 イメージは、描画せず、再マップと再割り当てが 1 回です。 再マッピング プロセスでは、青に赤のすべてのピクセルを変更します。  
  
 次の図は、左側に元のイメージ、右側の再マップされたイメージを示しています。  
  
 ![カラー リマップ](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。  
  
## <a name="see-also"></a>関連項目  
 [イメージの色の変更](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
