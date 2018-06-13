---
title: '方法 : 自動スケーリングを解除してパフォーマンスを向上させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
ms.openlocfilehash: e1c46f805b7ba2e2f2a1eb52042cc2ca08e63e03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523043"
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>方法 : 自動スケーリングを解除してパフォーマンスを向上させる
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 描画すると、パフォーマンスが低下していましたが、イメージをスケーリング自動的に場合があります。 描画先の四角形の寸法を渡すことによって、イメージのスケーリングを制御する代わりに、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドです。  
  
 たとえば、次の呼び出し、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドの左上隅を指定します (50, 30) 先の四角形が指定されていません。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 これは最も簡単なバージョンが、<xref:System.Drawing.Graphics.DrawImage%2A>メソッド必須の引数の数、に関しては最も効率的とは限りません。 解決が使用する場合[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)](通常 96 ドット/インチ) に格納されている解像度とは異なる、<xref:System.Drawing.Image>オブジェクト、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドは、イメージを拡大縮小します。 たとえば、<xref:System.Drawing.Image>オブジェクト 216 ピクセル幅と 72 インチあたりのドットのストアドの水平方向の解像度の値があります。 216/72 が 3、ため<xref:System.Drawing.Graphics.DrawImage%2A>を 96 ドット/インチの解像度で 3 インチ、幅を持つようにイメージをスケーリングします。 つまり、 <xref:System.Drawing.Graphics.DrawImage%2A> 96 x 3 = 288 の幅があるイメージが表示されます (ピクセル)。  
  
 画面の解像度が 96 ドット/インチと異なる場合でも[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]はおそらくスケール イメージ画面の解像度が 96 ドット/インチ場合と同様です。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics>オブジェクトは、デバイス コンテキストに関連付けられて、いつ[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]結果画面の解像度のデバイス コンテキストは 96、実際の画面の解像度に関係なく、通常のクエリ。 移行先の四角形を指定することで自動スケーリングを避けることができます、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドです。  
  
## <a name="example"></a>例  
 次の例では、2 回、同じイメージを描画します。 最初のケースでは、先の四角形の高さと幅が指定されていないと、イメージが自動的にスケーリングします。 2 番目のケースの幅と高さ (ピクセル単位で測定) 先の四角形は、元の画像の高さと幅と同じにするのに指定します。 次の図は、2 回表示されるイメージを示します。  
  
 ![テクスチャのスケール](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。 Texture.jpg をイメージ名と、システムで有効なパスに置き換えます。  
  
## <a name="see-also"></a>関連項目  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
