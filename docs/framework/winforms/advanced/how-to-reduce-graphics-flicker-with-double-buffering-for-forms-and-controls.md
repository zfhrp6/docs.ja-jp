---
title: '方法 : フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: 6e11e364af5dc361a24cdd88d72432d6ba4d4058
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522855"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>方法 : フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する
ダブル バッファリングでは、メモリ バッファーを使用して、複数の描画操作に関連するちらつきの問題に対処します。 ダブル バッファリングを有効にすると、すべての描画操作が画面上の描画サーフェイスではなく、最初にメモリ バッファーに描画されます。 描画操作がすべて完了すると、メモリ バッファーが、関連付けられている描画サーフェイスに直接コピーされます。 1 つだけのグラフィックス操作が実行されるため、画面に、複雑な描画操作に関連付けられているイメージのちらつきが排除されます。ほとんどのアプリケーションでの既定のダブル バッファリングによって提供される、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]最良の結果を提供します。 既定ではバッファー内の標準の Windows フォーム コントロールをダブルクリックします。 ダブル バッファリングをフォーム内での既定値を有効にすることができ、2 つの方法でコントロールを作成します。 設定するか、<xref:System.Windows.Forms.Control.DoubleBuffered%2A>プロパティを`true`、呼び出すか、または、<xref:System.Windows.Forms.Control.SetStyle%2A>を設定するメソッド、<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>フラグを`true`です。 両方のメソッドは既定のフォームまたはコントロールのダブル バッファリングを有効にして、グラフィックスのちらつきなしのレンダリングを提供します。 呼び出す、<xref:System.Windows.Forms.Control.SetStyle%2A>レンダリングのすべてのコードが記述されているカスタム コントロールに対してのみメソッドをお勧めします。  
  
 アニメーションまたは高度なメモリの管理より高度なダブル バッファリングのシナリオには、独自のダブル バッファリング ロジックを実装できます。 詳細については、次を参照してください。[する方法: バッファリングされたグラフィックス管理手動で](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)です。  
  
### <a name="to-reduce-flicker"></a>ちらつきを軽減するには  
  
-   <xref:System.Windows.Forms.Control.DoubleBuffered%2A> プロパティを `true` に設定します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- または -  
  
-   呼び出す、<xref:System.Windows.Forms.Control.SetStyle%2A>を設定するメソッド、<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>フラグを`true`です。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>  
 <xref:System.Windows.Forms.Control.SetStyle%2A>  
 [ダブル バッファリングされたグラフィックス](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
