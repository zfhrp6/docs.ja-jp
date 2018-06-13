---
title: グラデーション ブラシを使用した図形の塗りつぶし
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 857a9276a731ae5e69b3caa1a639d1315aba9901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525035"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>グラデーション ブラシを使用した図形の塗りつぶし
グラデーション ブラシを使用して、図形を塗りつぶす色が徐々 に変化させることができます。 たとえば、色、形状の左端から右端に移動する段階的に変化するように図形を塗りつぶすに水平方向のグラデーションを使用できます。 黒を左の端で四角形を想像してください (0, 0, 0 は、赤、緑、および青のコンポーネントによって表されます)、右端が赤 (255, 0, 0) とします。 四角形が 256 ピクセルである場合は、いずれかの左側にあるピクセルの赤の要素より大きい値を特定のピクセルの赤の要素になります。 行の左端のピクセルの色要素 (0, 0, 0)、2 番目のピクセルが (1, 0, 0)、3 番目のピクセルが (2, 0, 0)、し、右端のピクセルの色要素 (255, 0, 0) に達するまでします。 これらの色の補間値は、色のグラデーションを構成します。  
  
 線形グラデーションは、水平、垂直方向に移動または並列斜めの指定した行に色を変更します。 パス グラデーションは、内側およびパスの境界を移動すると、色を変更します。 さまざまな効果を実現するためにパス グラデーションをカスタマイズすることができます。  
  
 次の図は、四角形が線形グラデーション ブラシで塗りつぶされパス グラデーション ブラシで塗りつぶした楕円を示します。  
  
 ![グラデーション](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 線形グラデーションを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 線形グラデーションを使用して、作成する方法を示しています、<xref:System.Drawing.Drawing2D.LinearGradientBrush>クラスです。  
  
 [方法: パス グラデーションを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 パス グラデーションを使用して、作成する方法について説明します、<xref:System.Drawing.Drawing2D.PathGradientBrush>クラスです。  
  
 [方法: グラデーションに対してガンマ補正を適用する](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 グラデーション ブラシでガンマ補正を使用する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 このクラスの説明を表すし、そのすべてのメンバーへのリンクがあります。  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 このクラスの説明を表すし、そのすべてのメンバーへのリンクがあります。
