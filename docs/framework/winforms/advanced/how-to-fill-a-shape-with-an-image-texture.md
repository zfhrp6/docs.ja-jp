---
title: "方法 : イメージ テクスチャによって図形を塗りつぶす"
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
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b5ef87762b08daa973237e7b3da1068640e08bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>方法 : イメージ テクスチャによって図形を塗りつぶす
使用してテクスチャを使用して、閉じた図形を塗りつぶすことができます、<xref:System.Drawing.Image>クラスおよび<xref:System.Drawing.TextureBrush>クラスです。  
  
## <a name="example"></a>例  
 次の例では、イメージと楕円を塗りつぶします。 コードを構築、<xref:System.Drawing.Image>オブジェクト、し、そのアドレスを渡します<xref:System.Drawing.Image>オブジェクトに渡す引数として、<xref:System.Drawing.TextureBrush.%23ctor%2A>コンス トラクターです。 3 番目のステートメントは、イメージを縮小し、4 番目のステートメントがスケーリングされたイメージの繰り返しコピー楕円を塗りつぶします。  
  
 次のコードで、<xref:System.Drawing.TextureBrush.Transform%2A>プロパティが描画される前に、イメージに適用される変換が含まれています。 元のイメージが 640 ピクセル幅と高さが 480 ピクセルがあると仮定します。 トランス フォームは、水平および垂直方向のスケーリング値を設定して、75 × 75 にイメージを縮小します。  
  
> [!NOTE]
>  次の例では、イメージ サイズは 75 × 75、および楕円のサイズは 150 × 250 です。 イメージが楕円よりも小さいため、楕円は、イメージを並べて表示されます。 イメージが繰り返されること水平方向および垂直方向、形状の境界まで手段をタイルに到達します。 タイルの詳細については、次を参照してください。[する方法: イメージで図形をタイル](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md)です。  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>参照  
 [ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
