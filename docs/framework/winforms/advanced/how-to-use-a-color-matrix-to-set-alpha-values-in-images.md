---
title: '方法 : カラー行列を使用してイメージのアルファ値を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: ed129cd9487ba1416cd69b2e13f59747856cb598
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522347"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>方法 : カラー行列を使用してイメージのアルファ値を設定する
<xref:System.Drawing.Bitmap>クラス (から継承される、<xref:System.Drawing.Image>クラス) と<xref:System.Drawing.Imaging.ImageAttributes>クラスが取得およびピクセル値を設定する機能を提供します。 使用することができます、<xref:System.Drawing.Imaging.ImageAttributes>アルファを変更するクラスは、イメージ全体の値または呼び出すことができます、<xref:System.Drawing.Bitmap.SetPixel%2A>のメソッド、<xref:System.Drawing.Bitmap>個々 のピクセル値を変更するクラス。  
  
## <a name="example"></a>例  
 <xref:System.Drawing.Imaging.ImageAttributes>クラス レンダリング中にイメージの変更に使用できる多くのプロパティがあります。 次の例で、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクトは、元の 80% にすべてのアルファ値を設定するために使用します。 これは、カラー行列を初期化し、アルファ スケーリング 0.8 をマトリックス内の値を設定します。 カラー行列のアドレスが渡される、<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>のメソッド、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクト、および<xref:System.Drawing.Imaging.ImageAttributes>にオブジェクトが渡される、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。  
  
 レンダリング中に、ビットマップのアルファ値は、元の 80% に変換されます。 これは、結果、イメージをバック グラウンドとブレンドされます。 次の図では、ビットマップ イメージ透明に見えるためです。純色の黒い線が引かを表示できます。  
  
 ![マトリックスを使用したアルファ ブレンド](../../../../docs/framework/winforms/advanced/media/image2.png "image2")  
  
 イメージは、バック グラウンドの白い部分には、イメージを白ブレンドされています。 イメージは、イメージと黒の線が交差黒い色とブレンドされます。  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> のパラメーターである `e`<xref:System.Windows.Forms.PaintEventHandler> を必要とします。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [アルファ ブレンドの直線と塗りつぶし](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
