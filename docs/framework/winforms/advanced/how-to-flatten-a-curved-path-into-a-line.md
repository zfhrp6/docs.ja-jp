---
title: '方法 : 曲線のパスを直線に平坦化する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a3a8467dc5906a88911672316bb0f2ed3607d3a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521204"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>方法 : 曲線のパスを直線に平坦化する
A<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトは、一連の行とベジエ スプラインを格納します。 パスをいくつかの種類の曲線 (省略記号ボタン、円弧をカーディナル スプライン) を追加できますが、パスに保存する前に、各曲線がベジエ スプラインに変換されます。 パスのフラット化は、パス内の各ベジエ スプラインを一連の直線に変換するので構成されます。 次の図は前に、と後のフラット化されたパスを示します。  
  
 ![直線と曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>パスを平坦化します。  
  
-   呼び出す、<xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>のメソッド、<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクト。 <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>メソッドは、フラット化されたパスと、元のパスの間で最大距離を指定する、平坦度引数を受け取ります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [パスの作成および描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
