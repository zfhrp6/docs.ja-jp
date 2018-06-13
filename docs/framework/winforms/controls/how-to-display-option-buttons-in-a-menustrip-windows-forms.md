---
title: '方法 : MenuStrip にオプション ボタンを表示する (Windows フォーム)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: da2bb7edceaf83aa5178618fd4098631d65a7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538029"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>方法 : MenuStrip にオプション ボタンを表示する (Windows フォーム)
オプション ボタン、オプション ボタンとも呼ばれるは、ユーザーが一度に 1 つだけを選択する点を除いて、チェック ボックスに似ています。 既定では、<xref:System.Windows.Forms.ToolStripMenuItem>クラスは、オプション ボタンの動作を提供していない、このクラスのメニュー項目にオプション ボタンの動作を実装するカスタマイズ可能なチェック ボックスの動作を提供する<xref:System.Windows.Forms.MenuStrip>コントロール。  
  
 ときに、<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>メニュー項目のプロパティは`true`ユーザーがアイテムをクリックしてチェック マークの表示を切り替えます。 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>プロパティは、項目の現在の状態を示します。 動作を実装する基本のオプション ボタン、項目が選択されているときに設定することを確認する必要があります、<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>に以前に選択した項目のプロパティを`false`です。  
  
 次の手順がこれを実装する方法を説明し、継承するクラスの追加機能、<xref:System.Windows.Forms.ToolStripMenuItem>クラスです。 `ToolStripRadioButtonMenuItem`などの上書きをメンバー クラス<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>と<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>選択の動作およびオプション ボタンの外観を提供します。 さらに、このクラスは、オーバーライド、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>親項目が選択されていないプロパティを [オプション] サブメニューでは無効になります。  
  
### <a name="to-implement-option-button-selection-behavior"></a>オプション ボタンの選択の動作を実装するには  
  
1.  初期化、<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>プロパティを`true`項目の選択を有効にします。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  上書き、<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>新しい項目が選択されているときに、以前に選択した項目の選択をクリアします。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  上書き、<xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>は既に選択されている項目をクリックすることを確認するメソッドは、選択範囲をクリアされません。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a>オプション ボタンの項目の外観を変更するには  
  
1.  上書き、<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>を使用して、オプション ボタンの既定のチェック マークするメソッド、<xref:System.Windows.Forms.RadioButtonRenderer>クラスです。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  上書き、 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>、 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>、 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>、および<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A>マウスの状態を追跡していることを確認する方法、<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>メソッドは、正しいオプション ボタンの状態を描画します。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>親項目が選択されていないときに、サブメニューのオプションを無効にするには  
  
1.  上書き、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティ両方を含む親項目にある場合に、項目が無効にできるように、<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>の値`true`と<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>の値`false`です。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  上書き、<xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>をサブスクライブするメソッド、<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>親アイテムのイベントです。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  親項目のハンドラーで<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>イベント、新しい有効な状態で画面を更新する項目が無効にします。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a>例  
 次のコード例は、完全な`ToolStripRadioButtonMenuItem`クラス、および<xref:System.Windows.Forms.Form>クラスと`Program`オプション ボタンの動作を確認するクラス。  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [MenuStrip コントロール](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [方法: カスタムの ToolStripRenderer を実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
