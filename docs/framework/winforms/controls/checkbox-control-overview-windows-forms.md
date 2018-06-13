---
title: CheckBox コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: 54a0bba3923626398fb4d1b0af753177dfaa09a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524145"
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox コントロールの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.CheckBox> コントロールは、特定の条件がオンかオフかを示します。 一般的に、はい/いいえ、または True/False の選択肢をユーザーに提示するために使用されます。 ユーザーが 1 つ以上選択可能な複数の選択肢を表示するために、チェック ボックス コントロールをグループの中で使用できます。  
  
 各を選択したユーザーを示すために使用することで、チェック ボックス コントロールがラジオ ボタン コントロールに似ています。 そのグループ内の 1 つだけのラジオ ボタンを一度に選択できますが異なります。 チェック ボックス コントロールで、ただし、任意の数のチェック ボックスを選択できます。  
  
 チェック ボックスは、単純データ バインディングを使用して、データベース内の要素に接続されている可能性があります。 使用して複数のチェック ボックスをグループ化することがあります、<xref:System.Windows.Forms.GroupBox>コントロール。 コントロールをグループ化できます一緒に移動するフォーム デザイナーでこれは、外観もユーザー インターフェイスのデザインに便利です。 詳細については、次を参照してください。 [Windows フォーム データ バインディング](../../../../docs/framework/winforms/windows-forms-data-binding.md)と[GroupBox コントロール](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)です。  
  
 <xref:System.Windows.Forms.CheckBox>コントロールは、2 つの重要なプロパティを持つ<xref:System.Windows.Forms.CheckBox.Checked%2A>と<xref:System.Windows.Forms.CheckBox.CheckState%2A>です。 <xref:System.Windows.Forms.CheckBox.Checked%2A>プロパティには、どちらかを返します`true`または`false`です。 <xref:System.Windows.Forms.CheckBox.CheckState%2A>プロパティには、どちらかを返します<xref:System.Windows.Forms.CheckState.Checked>または<xref:System.Windows.Forms.CheckState.Unchecked>; またはの場合、<xref:System.Windows.Forms.CheckBox.ThreeState%2A>プロパティに設定されている`true`、<xref:System.Windows.Forms.CheckBox.CheckState%2A>を返すことも<xref:System.Windows.Forms.CheckState.Indeterminate>します。 不確定な状態で淡色表示オプションは使用を示すために、ボックスが表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.CheckBox>  
 [方法: Windows フォームの CheckBox コントロールでオプションを設定する](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [方法: Windows フォームの CheckBox のクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [CheckBox コントロール](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
