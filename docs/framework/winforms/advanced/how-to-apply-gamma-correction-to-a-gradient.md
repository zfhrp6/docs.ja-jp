---
title: "方法 : グラデーションに対してガンマ補正を適用する"
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
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2721a45381f2d0befe82d6d0db2630f3eae08d51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>方法 : グラデーションに対してガンマ補正を適用する
ブラシの設定を線形グラデーション ブラシのガンマ補正を有効にする<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>プロパティを`true`です。 ガンマ補正を無効に設定できます、<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>プロパティを`false`です。 既定では、ガンマ補正が無効です。  
  
## <a name="example"></a>例  
 この例では、線形グラデーション ブラシを作成し、そのブラシを使用して 2 つの四角形を入力します。 最初の四角形はガンマ補正を適用せず、ガンマ補正と 2 つ目の四角形が格納されます。  
  
 次の図は、次の 2 つの塗りつぶされた四角形を示します。 ガンマ補正を持たない場合、最上位の四角形は、中央で淡色表示します。 複数の uniform 濃度ガンマ補正は、下の四角形が表示されます。  
  
 ![グラデーション](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [グラデーション ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
