---
title: "方法 : コンテキスト メニューでスペル チェックを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "有効化 (テキスト ボックスでスペル チェックを) [WPF]"
  - "再有効化 (テキスト ボックスでスペル チェックを) [WPF]"
  - "スペル チェック (コンテキスト メニューによる) [WPF]"
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : コンテキスト メニューでスペル チェックを使用する
既定では、<xref:System.Windows.Controls.TextBox> や <xref:System.Windows.Controls.RichTextBox> などの編集コントロールでスペル チェックを有効にすると、スペル チェック用の項目がコンテキスト メニューに表示されます。  たとえば、スペルが間違っている単語をユーザーが右クリックすると、スペル修正の候補や **\[すべて無視\]** のオプションが表示されます。  しかし、既定のコンテキスト メニューを独自のカスタム コンテキスト メニューでオーバーライドすると、この機能は失われ、コンテキスト メニューのスペル チェック機能を再度有効にするためのコードを記述する必要があります。  <xref:System.Windows.Controls.TextBox> でこれを行う方法を次の例に示します。  
  
## 使用例  
 コンテキスト メニューの実装に使用するイベントを持つ <xref:System.Windows.Controls.TextBox> を作成する [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を次の例に示します。  
  
 [!code-xml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## 使用例  
 コンテキスト メニューを実装するコードを次の例に示します。  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 <xref:System.Windows.Controls.RichTextBox> でこれを行う場合も、同様のコードを使用します。  大きな違いは、`GetSpellingError` メソッドに渡すパラメーターです。  <xref:System.Windows.Controls.TextBox> に対しては、キャレット位置のインデックスを表す整数を渡します。  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <xref:System.Windows.Controls.RichTextBox> に対しては、キャレット位置を表す <xref:System.Windows.Documents.TextPointer> を渡します。  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## 参照  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [テキスト編集コントロールでスペル チェックを有効にする](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)   
 [TextBox でカスタム コンテキスト メニューを使用する](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)