---
title: '方法 : Windows フォーム TextBox コントロールで複数行を表示する'
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: c826a519d8be05430eb6e2434209424514347b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538568"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>方法 : Windows フォーム TextBox コントロールで複数行を表示する
既定では、Windows フォーム<xref:System.Windows.Forms.TextBox>コントロールは、1 行のテキストを表示し、スクロール バーは表示されません。 テキストは、使用可能な領域よりも長くなりますが、テキストの一部のみが表示されます。 この既定の動作を変更するには設定して、 <xref:System.Windows.Forms.TextBox.Multiline%2A>、<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>と<xref:System.Windows.Forms.TextBox.ScrollBars%2A>プロパティを適切な値にします。  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>TextBox コントロールでの改行を表示するには  
  
-   複数の行に改行を表示する<xref:System.Windows.Forms.TextBox>を使用して、<xref:System.Environment.NewLine%2A>プロパティです。  
  
     注意してくださいをエスケープ文字の解釈 (\\) 言語に固有です。 Visual Basic で`Chr$(13) & Chr$(10)`のキャリッジ リターンとライン フィード文字の組み合わせ。  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>テキスト ボックス コントロールで複数の行を表示するには  
  
1.  <xref:System.Windows.Forms.TextBox.Multiline%2A> プロパティを `true` に設定します。 場合<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>は`true`(既定)、コントロール内のテキストが、1 つまたは複数の段落を表示する、以外の場合はそれ以外の場合でサポートされる一覧は、一部の行はコントロールの端に隠れてしまうことがあります。  
  
2.  <xref:System.Windows.Forms.TextBox.ScrollBars%2A> プロパティに適切な値を設定します。  
  
    |[値]|説明|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|段落テキストにする場合は、この値を使用するコントロールにほぼ常に適合します。 ユーザーは、一度にすべてを表示するには、テキストが長すぎる場合、コントロール内に移動する、マウス ポインターを使用できます。|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|線、これらのいくつかの幅を超える可能性がありますの一覧を表示する場合、この値を使用して、<xref:System.Windows.Forms.TextBox>コントロール。|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|一覧は、コントロールの高さより長くすることがある場合は、この値を使用します。|  
  
3.  <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> プロパティに適切な値を設定します。  
  
    |[値]|説明|  
    |-----------|-----------------|  
    |`false`|コントロール内のテキストが自動的に折り返される、ため、行の区切りに到達するまで右にスクロールされます。 選択した場合は、この値を使用して<xref:System.Windows.Forms.ScrollBars.Horizontal>スクロール バーまたは<xref:System.Windows.Forms.ScrollBars.Both>上、します。|  
    |`true` (既定値)|水平スクロール バーは表示されません。 選択した場合は、この値を使用して<xref:System.Windows.Forms.ScrollBars.Vertical>スクロール バーまたは<xref:System.Windows.Forms.ScrollBars.None>、上記の 1 つまたは複数の段落を表示します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [方法: 読み取り専用テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [方法: 文字列に引用符を挿入する](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [方法: Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
