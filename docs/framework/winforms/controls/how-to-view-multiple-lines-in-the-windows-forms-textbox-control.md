---
title: "方法 : Windows フォーム TextBox コントロールで複数行を表示する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "復帰"
  - "CRLF"
  - "行末"
  - "ライン フィード"
  - "MultiLine プロパティ (TextBox コントロールの)"
  - "改行"
  - "ScrollBars プロパティ, TextBox コントロールで"
  - "TextBox コントロール [Windows フォーム], 表示 (複数行を)"
  - "WordWrap プロパティ"
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : Windows フォーム TextBox コントロールで複数行を表示する
既定の Windows フォーム <xref:System.Windows.Forms.TextBox> コントロールでは、単一行のテキストが表示され、スクロール バーは表示されません。  使用できる領域よりもテキストが長い場合は、テキストの一部だけが表示されます。  この既定の動作は、<xref:System.Windows.Forms.TextBox.Multiline%2A>、<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>、および <xref:System.Windows.Forms.TextBox.ScrollBars%2A> の各プロパティを適切な値に設定することにより変更できます。  
  
### TextBox コントロールに復帰を表示するには  
  
-   複数行 <xref:System.Windows.Forms.TextBox> に復帰を表示するには、<xref:System.Environment.NewLine%2A> プロパティを使用します。  
  
     エスケープ文字 \(\\\) の解釈は言語に固有であることに注意してください。  Visual Basic では、復帰とライン フィード文字の組み合わせを表すために `Chr$(13) & Chr$(10)` を使用します。  
  
### TextBox コントロールに複数行を表示するには  
  
1.  <xref:System.Windows.Forms.TextBox.Multiline%2A> プロパティを `true` に設定します。  <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> を既定値である真 \(`true`\) に設定している場合、コントロールのテキストは 1 つ以上の段落として表示されます。真 \(true\) に設定していない場合、テキストはリストとして表示され、一部の行はコントロールの端で隠れてしまうことがあります。  
  
2.  <xref:System.Windows.Forms.TextBox.ScrollBars%2A> プロパティに適切な値を設定します。  
  
    |値|Description|  
    |-------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars>|テキストの段落が、ほぼ常にコントロールに適合する場合に使用します。  テキストが長すぎて一度にすべてを表示できない場合は、マウス ポインターを使用して、コントロールの内部を移動できます。|  
    |<xref:System.Windows.Forms.ScrollBars>|<xref:System.Windows.Forms.TextBox> コントロールの幅よりも長い行のリストを表示する場合に使用します。|  
    |<xref:System.Windows.Forms.ScrollBars>|リストがコントロールの高さよりも長い場合に使用します。|  
  
3.  <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> プロパティに適切な値を設定します。  
  
    |値|Description|  
    |-------|-----------------|  
    |`false`|コントロールのテキストは、自動的に折り返されないため、改行に到達するまで右方向にスクロールされます。  この値は、上記の <xref:System.Windows.Forms.ScrollBars> スクロール バーまたは <xref:System.Windows.Forms.ScrollBars> を選択した場合に使用します。|  
    |`true` \(既定値\)|水平スクロール バーは表示されません。  この値は、上記の <xref:System.Windows.Forms.ScrollBars> スクロール バーまたは <xref:System.Windows.Forms.ScrollBars> を選択した場合に使用して、1 つ以上の段落を表示します。|  
  
## 参照  
 <xref:System.Windows.Forms.TextBox>   
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [方法 : Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [方法 : 読み取り専用テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [方法 : 文字列に引用符を挿入する](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)