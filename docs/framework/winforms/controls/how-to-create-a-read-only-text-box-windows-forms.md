---
title: "方法 : 読み取り専用テキスト ボックスを作成する (Windows フォーム) | Microsoft Docs"
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
  - "読み取り専用テキスト ボックス"
  - "テキスト ボックス, 読み取り専用"
  - "TextBox コントロール [Windows フォーム], 読み取り専用"
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 読み取り専用テキスト ボックスを作成する (Windows フォーム)
編集可能な Windows フォーム テキスト ボックスを読み取り専用コントロールに変換できます。  たとえば、アプリケーションの状態によって、テキスト ボックスに、通常は編集されるが現在は編集しない値が表示される場合があります。  
  
### 読み取り専用テキスト ボックスを作成するには  
  
1.  <xref:System.Windows.Forms.TextBox> コントロールの <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> プロパティを `true` に設定します。  このプロパティを `true` に設定した場合、テキスト ボックスのテキストは変更できませんが、スクロールおよび強調表示はできます。  テキスト ボックスでは、**\[コピー\]** は使用できますが、**\[切り取り\]** および **\[貼り付け\]** は使用できません。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> プロパティは、実行時のユーザーとの対話だけに影響します。  <xref:System.Windows.Forms.TextBox.Text%2A> プロパティを変更すると、実行時にプログラムによってテキスト ボックスの内容を変更できます。  
  
## 参照  
 <xref:System.Windows.Forms.TextBox>   
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [方法 : Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [方法 : 文字列に引用符を挿入する](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [方法 : Windows フォーム TextBox コントロールで複数行を表示する](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)