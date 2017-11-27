---
title: "GDI+ での描画サーフェイスの制限"
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
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 213f0afefa1f8635d2b70d2e3626b7fbe748b42c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
