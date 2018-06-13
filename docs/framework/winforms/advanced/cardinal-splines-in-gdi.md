---
title: GDI+ でのカーディナル スプライン
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
ms.openlocfilehash: 93ae09c72415fa489e62f753e51e5a3ffcfb2425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517966"
---
# <a name="cardinal-splines-in-gdi"></a>GDI+ でのカーディナル スプライン
カーディナル スプラインは、大規模な曲線を形成に参加している個々 の曲線のシーケンスです。 スプラインは、ポイントおよびテンション パラメーターの配列を指定します。 配列内の各ポイントを通過するカーディナル スプラインがスムーズに通過します。ありませんとがった角と曲線のテンションの急激な変化があります。 次の図は、一連のポイントと、セット内の各ポイントを通過するカーディナル スプラインを示します。  
  
 ![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>物理および数学スプライン  
 シン木材やその他の柔軟な資料の物理的なスプラインです。 数学的なスプラインの出現により、前に、デザイナーは、物理的なスプラインを曲線の描画に使用されます。 デザイナーはスプライン枚の用紙に置き、特定の点のセットに固定します。 デザイナーは、曲線をペンや鉛筆とスプラインに沿って描画で作成し、でした。 指定された一連のポイントは、さまざまな物理スプラインのプロパティによって、曲線を起動できませんでした。 たとえば、曲げに対する抵抗力が強いスプラインでは、非常に柔軟なスプラインよりも異なる曲線と生成されます。  
  
 数学的なスプラインによって生成される、曲線、物理的なスプラインによって生成された 1 回、曲線に似ていますので、数学的なスプライン数式は柔軟な棒プロパティに基づきます。 異なるテンションの物理的なスプライン ポイントの指定されたセットを別の曲線が生成されます、同様テンション パラメーターの値が異なる数学スプラインによって別の曲線ポイントの指定されたセットを通じてが生成されます。 次の図は、同じ点のセットに渡される 4 つのカーディナル スプラインを示します。 各スプラインのテンションが表示されます。 曲線のポイントの間の最短方法 (直線) を実行するように強制無限の物理的テンション テンション 0 の値が対応しています。 1 のテンションは曲げの合計が最低のパスを取得するスプラインをできるように、物理ありませんテンションに対応します。 張力値が 1 より大きい、曲線のように動作圧縮のスプリングより長いパスを取得するプッシュします。  
  
 ![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 前の図に 4 つのスプラインは、開始位置に同じ正接回線を共有します。 タンジェントとは、開始点と曲線に沿って次の点を結ぶ線です。 同様に、終了位置で共有正接とは、曲線の終点から過去の時点に描画される直線。  
  
 インスタンスを通過するカーディナル スプラインを描画する必要、<xref:System.Drawing.Graphics>クラス、 <xref:System.Drawing.Pen>、および配列の<xref:System.Drawing.Point>オブジェクトのインスタンス、<xref:System.Drawing.Graphics>クラスを提供、<xref:System.Drawing.Graphics.DrawCurve%2A>スプラインを描画するメソッドと<xref:System.Drawing.Pen>スプライン、線の幅、色などの属性を格納します。 配列<xref:System.Drawing.Point>曲線を通じて渡されるポイントがオブジェクトに格納します。 次のコード例は、内のポイントを通過するカーディナル スプラインを描画する方法を示しています。`myPointArray`です。 3 番目のパラメーターは、テンションです。  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>関連項目  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [曲線の作成と描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
