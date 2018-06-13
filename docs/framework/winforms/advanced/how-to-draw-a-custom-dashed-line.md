---
title: '方法 : カスタム破線を描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 39dde3bb45165783171326b79e98744807350952
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521616"
---
# <a name="how-to-draw-a-custom-dashed-line"></a>方法 : カスタム破線を描画する
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 記載されているいくつかの破線スタイルを提供、<xref:System.Drawing.Drawing2D.DashStyle>列挙します。 これらの標準の破線スタイルがニーズに適合しないいない場合は、カスタムの破線のパターンを作成できます。  
  
## <a name="example"></a>例  
 カスタム破線を描画する、配列にダッシュと空白の長さを格納し、配列の値として割り当てます、<xref:System.Drawing.Pen.DashPattern%2A>のプロパティ、<xref:System.Drawing.Pen>オブジェクト。 次の例は、配列に基づくカスタム破線を描画`{5, 2, 15, 4}`です。 取得する場合は、配列の要素を 5 のペンの幅に乗算する`{25, 10, 75, 20}`です。 25 と 75 の長さの別の表示ダッシュと長が 10 ~ 20 の空白が交互です。  
  
 次の図は、結果として得られる点線を示します。 最終的な dash がで行が終了するようにに 25 よりも短くする必要がある注意 (405, 5)。  
  
 ![ペン](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 Windows フォームを作成し、処理、フォームの<xref:System.Windows.Forms.Control.Paint>イベント。 上記のコードを貼り付け、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。  
  
## <a name="see-also"></a>関連項目  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
