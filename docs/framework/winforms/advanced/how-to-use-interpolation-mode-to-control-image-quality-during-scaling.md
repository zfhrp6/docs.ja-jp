---
title: '方法 : 補間モードを使用してスケーリング時の画質を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 72a9cb3a19f0d449dcb376a65f1734b79ed61ab9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522360"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>方法 : 補間モードを使用してスケーリング時の画質を制御する
補間モード、<xref:System.Drawing.Graphics>オブジェクト方法に影響を与えます[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]スケール (拡大および縮小) イメージ。 <xref:System.Drawing.Drawing2D.InterpolationMode>列挙体は、以下のうち一部を示しています、いくつかの補間モードを定義します。  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 イメージを拡大するには、大きいイメージのピクセルのグループに、元のイメージ内の各ピクセルをマップする必要があります。 イメージを縮小するより小さなイメージの単一のピクセルに元のイメージのピクセルのグループをマップする必要があります。 これらのマッピングを実行するアルゴリズムの有効性は、スケーリングされたイメージの品質を決定します。 高品質のスケーリングされたイメージを生成するアルゴリズムは、処理時間を必要とする傾向があります。 上記の一覧で<xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>が最も低い品質モードと<xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>最高品質のモードします。  
  
 補間モードを設定するには、メンバーのいずれかを割り当てる、<xref:System.Drawing.Drawing2D.InterpolationMode>列挙型を<xref:System.Drawing.Graphics.InterpolationMode%2A>のプロパティ、<xref:System.Drawing.Graphics>オブジェクト。  
  
## <a name="example"></a>例  
 次の例では、イメージを描画し、次の 3 つの異なる補間モードとイメージが圧縮されます。  
  
 次の図は、元のイメージと 3 つの小さいイメージを示します。  
  
 ![さまざまな補間設定でイメージ](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
