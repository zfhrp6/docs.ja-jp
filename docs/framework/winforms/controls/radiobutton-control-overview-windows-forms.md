---
title: RadioButton コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: 397808c055fd5ba5e8a73d47dfc7fee6c0cf2975
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540081"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.RadioButton>コントロールがユーザーに 2 つ以上の相互に排他的な選択肢を表示します。 重要な違いがあるオプション ボタンおよびチェック ボックスは、類似した機能に見える場合があります、にもかかわらず: ユーザーは、オプション ボタンを選択するときは、同じグループ内の他のオプション ボタンをも選択することはできません。 これに対し、任意の数のチェック ボックスを選択することができます。 ラジオ ボタン グループの定義は、「ここでは 1 つだけを選択できる選択肢のセットです」  
  
## <a name="using-the-control"></a>コントロールの使用  
 ときに、<xref:System.Windows.Forms.RadioButton>コントロールをクリックすると、その<xref:System.Windows.Forms.RadioButton.Checked%2A>プロパティに設定されている`true`と<xref:System.Windows.Forms.Control.Click>イベント ハンドラーが呼び出されます。 <xref:System.Windows.Forms.RadioButton.CheckedChanged>イベントが発生したときの値、<xref:System.Windows.Forms.RadioButton.Checked%2A>プロパティが変更されました。 場合、<xref:System.Windows.Forms.RadioButton.AutoCheck%2A>プロパティに設定されている`true`(既定) ラジオ ボタンを選択すると、グループの他のすべてが自動的に消去します。 通常、このプロパティにのみ設定`false`ラジオ ボタンを選択を確認する検証コードを使用する場合は、有効なオプションです。 コントロール内に表示されるテキストが設定されている、<xref:System.Windows.Forms.Control.Text%2A>プロパティで、アクセス キーのショートカットを含めることができます。 アクセス キーによりアクセス キーと ALT キーを押すとコントロールを「クリックして」をします。 詳細については、次を参照してください。[する方法: Windows のフォーム コントロールへのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)と[する方法: Windows フォーム コントロールによって表示されるテキストを設定](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)です。  
  
 <xref:System.Windows.Forms.RadioButton>がされている場合は選択すると、押されている場合に表示されるコマンド ボタンのように、コントロールの表示、<xref:System.Windows.Forms.RadioButton.Appearance%2A>プロパティに設定されている<xref:System.Windows.Forms.Appearance.Button>です。 オプション ボタンを使用してイメージを表示も、<xref:System.Windows.Forms.ButtonBase.Image%2A>と<xref:System.Windows.Forms.ButtonBase.ImageList%2A>プロパティです。 詳細については、次を参照してください。[する方法: Windows フォーム コントロールによってイメージの表示設定](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.RadioButton>  
 [Panel コントロールの概要](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [GroupBox コントロールの概要](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [CheckBox コントロールの概要](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [方法: Windows フォーム コントロールのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [方法: Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [方法: セットとして機能する Windows フォーム RadioButton コントロールをグループ化する](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)  
 [RadioButton コントロール](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
