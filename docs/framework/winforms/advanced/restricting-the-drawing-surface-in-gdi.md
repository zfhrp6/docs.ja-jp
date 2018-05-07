---
title: GDI+ での描画サーフェイスの制限
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: b457e94acb334dc012f017090c63189de372592d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>GDI+ での描画サーフェイスの制限
クリッピングでは、特定の四角形または領域に描画を制限します。 次の図、文字列「こんにちは」ハート形の領域にクリップします。  
  
 ![制限付き描画面](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>クリッピング領域を持つ  
 パスからの領域を作成し、領域のアウトラインが表示されたテキストを使用できるように、パスは、文字列のアウトラインを含めることができます。 次の図は、テキストの文字列の内側にクリップ同心構造の省略記号のセットを示します。  
  
 ![制限付き描画面](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 クリッピングを使用して描画、作成、<xref:System.Drawing.Graphics>オブジェクト、設定、<xref:System.Drawing.Graphics.Clip%2A>プロパティ、描画の呼び出しメソッドを同じ<xref:System.Drawing.Graphics>オブジェクト。  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [領域の使用](../../../../docs/framework/winforms/advanced/using-regions.md)
