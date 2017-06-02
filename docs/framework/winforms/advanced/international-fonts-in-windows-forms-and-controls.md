---
title: "Windows フォームおよびコントロールの国際対応フォント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "フォント フォールバック (Windows フォームでの)"
  - "フォント, グローバリゼーションの考慮事項"
  - "フォント, 国際対応"
  - "グローバリゼーション [Windows フォーム], 文字セット"
  - "国際対応のアプリケーション [Windows フォーム], 文字表示"
  - "ローカリゼーション [Windows フォーム], フォント"
  - "Windows フォーム コントロール, ラベル"
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Windows フォームおよびコントロールの国際対応フォント
国際対応のアプリケーションでフォントを選択する方法としては、できるだけフォント フォールバックを使用することをお勧めします。  フォント フォールバックとは、文字が属する言語をシステムが判断することを指します。  
  
## フォント フォールバックの使用  
 この機能を利用するには、フォームまたはその他の要素の <xref:System.Drawing.Font> プロパティは設定しないようにしてください。  アプリケーションが、オペレーティング システムのローカライズ言語ごとに異なる既定のシステム フォントを自動的に使用します。  アプリケーションの実行時、システムにより、オペレーティング システムで選択された地域に適したフォントが自動的に設定されます。  
  
 フォント設定をしないという規則には、フォント スタイルの変更を考慮した例外があります。  このことは、ユーザーがテキスト ボックスのテキストを太字で表示させるためにボタンをクリックするアプリケーションで重要になります。  これを行うには、フォームのフォントに関係なく、テキスト ボックスのスタイルを太字に変更する関数を作成します。  この関数は <xref:System.Windows.Forms.Control.Click> イベント ハンドラーおよび <xref:System.Windows.Forms.Control.FontChanged> イベント ハンドラーの 2 か所で呼び出す必要があります。  <xref:System.Windows.Forms.Control.Click> イベント ハンドラーでだけこの関数を呼び出した場合、コードの他の部分によってフォーム全体のフォント ファミリが変更されると、テキスト ボックスは、このフォームの残りの要素と同じフォント ファミリに変更されません。  
  
```  
' Visual Basic  
Private Sub MakeBold()  
   ' Change the TextBox to a bold version of the form font  
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
   ' Clicking this button makes the TextBox bold  
   MakeBold()  
End Sub  
  
Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged  
   ' If the TextBox is already bold and the form's font changes,  
   ' change the TextBox to a bold version of the new form font  
   If (TextBox1.Font.Style = FontStyle.Bold) Then  
      MakeBold()  
   End If  
End Sub  
  
// C#  
private void button1_Click(object sender, System.EventArgs e)  
{  
   // Clicking this button makes the TextBox bold  
   MakeBold();  
}  
  
private void MakeBold()   
{  
   // Change the TextBox to a bold version of the form's font  
   textBox1.Font = new Font(this.Font, FontStyle.Bold);  
}  
  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
   // If the TextBox is already bold and the form's font changes,  
   // change the TextBox to a bold version of the new form font  
   if (textBox1.Font.Style == FontStyle.Bold)   
   {  
      MakeBold();  
   }  
}  
```  
  
 ただし、言語によっては、アプリケーションのローカライズにより、太字フォントの表示が乱れることがあります。  このことが問題になる場合は、ローカライズで、フォント切り替えオプションを太字ではなく通常のテキストに指定します。  一般に、ローカリゼーション担当者は、開発者とは異なりソース コードに手を加えることはせず、リソース ファイルだけを処理します。したがって、このオプションの設定はリソース ファイルで行う必要があります。  これを行うには、<xref:System.Drawing.Font.Bold%2A> プロパティを `true` に設定します。  これにより、フォント設定がリソース ファイルに書き出され、ローカリゼーション担当者が編集できるようになります。  `InitializeComponent`  メソッドの後に、フォームのフォントに関係なくフォントをリセットし、リソース ファイルで指定されたフォント スタイルを使用するためのコードを記述します。  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## 参照  
 [Windows フォームのグローバル化](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)   
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)