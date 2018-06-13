---
title: '方法 : ペンの幅と配置を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: 8ac125978405f39cd26680338cdabb661ad92d16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522283"
---
# <a name="how-to-set-pen-width-and-alignment"></a>方法 : ペンの幅と配置を設定する
作成するときに、 <xref:System.Drawing.Pen>、コンス トラクターに引数の 1 つとして、ペンの幅を指定することができます。 ペンの幅を変更することも、<xref:System.Drawing.Pen.Width%2A>のプロパティ、<xref:System.Drawing.Pen>クラスです。  
  
 理論上の線が 0 の幅を持ちます。 1 ピクセル幅の広い線を描画するときは、理論上の線のピクセルが中央揃えされます。 1 つ以上のピクセル幅の広い線を描画する場合ピクセルは理論上の線の中央揃えで配置するか、または、理論上の線の片側に表示されます。 ペンの配置プロパティを設定することができます、<xref:System.Drawing.Pen>理論上の行に対する相対をペンで描画されるピクセルを配置する方法を決定します。  
  
 値<xref:System.Drawing.Drawing2D.PenAlignment.Center>、 <xref:System.Drawing.Drawing2D.PenAlignment.Outset>、および<xref:System.Drawing.Drawing2D.PenAlignment.Inset>次に表示されるコードの例のメンバーである、<xref:System.Drawing.Drawing2D.PenAlignment>列挙します。  
  
 次のコード例では直線を 2 回を描画します。 黒のペンの幅が 1 のが 1 回と緑のペンの幅が 10 のです。  
  
### <a name="to-vary-the-width-of-a-pen"></a>ペンの幅を変更するには  
  
-   値を設定、<xref:System.Drawing.Pen.Alignment%2A>プロパティを<xref:System.Drawing.Drawing2D.PenAlignment.Center>(既定値) を緑のペンで描画されるピクセルの中央を理論的な行に指定します。 次の図は、結果として得られる行を示しています。  
  
     ![ペン](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")  
  
     次のコード例は 2 回四角形を描画します。 黒のペンの幅が 1 のが 1 回と緑のペンの幅が 10 のです。  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>ペンのアラインメントを変更するには  
  
-   値を設定、<xref:System.Drawing.Pen.Alignment%2A>プロパティを<xref:System.Drawing.Drawing2D.PenAlignment.Center>緑のペンで描画されるピクセルの中央を四角形の境界を指定します。  
  
     次の図は、結果として得られる四角形を示します。  
  
     ![ペン](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>ペンを作成するには  
  
-   前のコード例では、3 番目のステートメントを次のように変更することによって、緑のペンの配置を変更します。  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     これで、次の図に示すようには、四角形の内側のワイド緑の線のピクセルが表示されます。  
  
     ![ペン](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")  
  
## <a name="see-also"></a>関連項目  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
