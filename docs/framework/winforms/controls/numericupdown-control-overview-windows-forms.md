---
title: NumericUpDown コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: b1f32a767d27ef2f4e5629947d67097272695d9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537162"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown コントロールの概要 (Windows フォーム)
<xref:System.Windows.Forms.NumericUpDown>コントロールはテキスト ボックスの組み合わせと、値を調整するユーザーがクリックする矢印のペアのようになります。 コントロールは、表示し、固定の数値の選択肢の一覧から 1 つの数値を設定します。 ユーザーは大きくなり、上下の矢印キーを押すか、テキスト ボックス コントロールの一部に数値を入力と下向きの矢印をクリックして、番号が低下します。 上矢印キーをクリックすると、数値が最大値です。 方向を移動します。数値、最小値の方向に移動、下方向キーをクリックします。  
  
 多用途の機能のためこのコントロールは、明らかな選択肢では、たとえば、ミュージック プレーヤー アプリケーションのボリューム コントロールを作成する場合です。 <xref:System.Windows.Forms.NumericUpDown>多くの Windows コントロール パネル アプリケーションでコントロールを使用します。  
  
## <a name="key-properties-and-methods"></a>キー プロパティとメソッド  
 コントロールのテキスト ボックスに表示する数値は 16 進数、さまざまな形式で指定できます。 詳細については、次を参照してください。[する方法: Windows フォームの NumericUpDown コントロールの書式を設定](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)です。 コントロールのプロパティは<xref:System.Windows.Forms.NumericUpDown.Value%2A>、 <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (既定値は 100)、 <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (既定値は 0)、および<xref:System.Windows.Forms.NumericUpDown.Increment%2A>(既定値は 1)。 <xref:System.Windows.Forms.NumericUpDown.Value%2A>プロパティは、コントロールで選択されている現在の数を設定します。 <xref:System.Windows.Forms.NumericUpDown.Increment%2A>プロパティを設定しますをクリックすると、矢印または下向き矢印数が調整されます。 コントロールからフォーカスが移動、ときに、最小値と最大の数値に対して任意の型指定された入力が検証されます。 上矢印を継続的に押す矢印または下向き矢印、数字、を通じてコントロールを移動する速度を上げることで、<xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>プロパティです。 コントロールの主要なメソッドは<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>と<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.NumericUpDown>  
 [NumericUpDown コントロール](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [方法: Windows フォームの NumericUpDown コントロールの書式を設定する](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)  
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
