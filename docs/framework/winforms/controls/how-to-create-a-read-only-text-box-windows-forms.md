---
title: '方法 : 読み取り専用テキスト ボックスを作成する (Windows フォーム)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 06e03f67bd1f084b30bce85c3d81ad7b8c97a1b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530147"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>方法 : 読み取り専用テキスト ボックスを作成する (Windows フォーム)
編集可能な Windows フォームのテキスト ボックスは読み取り専用のコントロールに変換できます。 たとえば、テキスト ボックスでは、通常は編集されますが、できない場合があります現時点では、アプリケーションの状態のための値を表示可能性があります。  
  
### <a name="to-create-a-read-only-text-box"></a>読み取り専用テキスト ボックスを作成するには  
  
1.  設定、<xref:System.Windows.Forms.TextBox>コントロールの<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>プロパティを`true`です。 プロパティ設定された`true`ユーザーがまだスクロールして変更を許可せずにテキスト ボックス内のテキストを強調表示します。 A**コピー**コマンドがテキスト ボックスでは、機能が、**切り取り**と**貼り付け**のコマンドはできません。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>プロパティでは、実行時にユーザーとの対話のみに影響します。 まだ変更テキスト ボックスの内容プログラムで実行時に変更することによって、<xref:System.Windows.Forms.TextBox.Text%2A>テキスト ボックスのプロパティです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [方法: 文字列に引用符を挿入する](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [方法: Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [方法: Windows フォーム TextBox コントロールで複数行を表示する](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
