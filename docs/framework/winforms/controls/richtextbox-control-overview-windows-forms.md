---
title: RichTextBox コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 53c4cd41cf203886c93291debc7bca4f395f9698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542120"
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールを表示、入力すると、および書式設定を含むテキストを操作するために使用します。 <xref:System.Windows.Forms.RichTextBox>コントロールはすべて、<xref:System.Windows.Forms.TextBox>コントロールは、できますが、ことができますフォント、色、およびリンクの表示以外の場合は、ファイルからテキストと埋め込み画像を読み込む、指定した文字を検索します。 <xref:System.Windows.Forms.RichTextBox>通常、コントロールはテキストの操作を提供し、Microsoft Word などのワード プロセッシング アプリケーションと同様の機能の表示に使用します。 同様に、<xref:System.Windows.Forms.TextBox>コントロール、<xref:System.Windows.Forms.RichTextBox>コントロールがスクロール バーを表示できるとは異なり、<xref:System.Windows.Forms.TextBox>コントロール、その既定値は、必要に応じて、水平線と垂直スクロール バーを表示して、追加のスクロール バーの設定があります。  
  
## <a name="working-with-the-richtextbox-control"></a>RichTextBox コントロールの操作  
 同様、<xref:System.Windows.Forms.TextBox>コントロール表示されるテキストが設定されて、<xref:System.Windows.Forms.RichTextBox.Text%2A>プロパティです。 <xref:System.Windows.Forms.RichTextBox>コントロール テキストの書式設定を多数のプロパティがあります。 これらのプロパティの詳細については、「[How to: Set Font Attributes for the Windows Forms RichTextBox Control (方法: Windows フォームの RichTextBox コントロールのフォント属性を設定)](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)」と「[How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control (方法: Windows フォームの RichTextBox コントロールを使用したインデント、ぶら下げインデント、および箇条書き段落の設定)](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)」参照してください。 ファイルを操作するため、<xref:System.Windows.Forms.RichTextBox.LoadFile%2A>と<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>メソッドの表示し、プレーン テキスト、Unicode プレーン テキスト、およびリッチ テキスト形式 (RTF) を含む複数のファイル形式を書き込むことができます。 可能性のあるファイル形式が表示されます<xref:System.Windows.Forms.RichTextBoxStreamType>です。 使用することができます、<xref:System.Windows.Forms.RichTextBox.Find%2A>テキストまたは特定の文字の文字列を検索するメソッド。  
  
 使用することも、<xref:System.Windows.Forms.RichTextBox>を設定して Web スタイルのリンクの制御、<xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>プロパティを`true`を処理するコードを記述し、<xref:System.Windows.Forms.RichTextBox.LinkClicked>イベント。 詳細については、「[How to: Display Web-Style Links with the Windows Forms RichTextBox Control (方法: Windows フォームの RichTextBox コントロールを使用して Web スタイルのリンクを表示する)](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)」を参照してください。 コントロール内のテキストの一部またはすべての操作を設定してから、ユーザーを防ぐことができます、<xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A>プロパティを`true`です。  
  
 元に戻したりでのほとんどの編集操作をやり直すことができます、<xref:System.Windows.Forms.RichTextBox>コントロールを呼び出して、<xref:System.Windows.Forms.TextBoxBase.Undo%2A>と<xref:System.Windows.Forms.RichTextBox.Redo%2A>メソッドです。 <xref:System.Windows.Forms.RichTextBox.CanRedo%2A>メソッドでは、コントロールにユーザーを元に戻した最後の操作を再適用することができるかどうかを判断することができます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
