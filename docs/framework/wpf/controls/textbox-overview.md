---
title: "TextBox の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コントロール, TextBox"
  - "TextBox コントロール, TextBox コントロールの概要"
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# TextBox の概要
<xref:System.Windows.Controls.TextBox> クラスを使用すると、書式なしテキストを表示または編集できます。  <xref:System.Windows.Controls.TextBox> は一般的に、フォームで書式なしテキストを編集するために使用されます。  たとえば、ユーザーの氏名や電話番号などの入力を求めるフォームで、テキスト入力のために <xref:System.Windows.Controls.TextBox> コントロールを使用します。  このトピックでは、<xref:System.Windows.Controls.TextBox> クラスについて説明し、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] と [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)] の両方で使用する例を示します。  
  
   
  
<a name="textbox_or_richtextbox"></a>   
## TextBox と RichTextBox  
 <xref:System.Windows.Controls.TextBox> と <xref:System.Windows.Controls.RichTextBox> のどちらを使用してもテキストを入力できますが、2 つのコントロールは異なるシナリオで使用されます。  <xref:System.Windows.Controls.TextBox> で必要なシステム リソースは <xref:System.Windows.Controls.RichTextBox> よりも少ないため、プレーン テキストのみを編集する必要がある場合 \(フォームでの使用\) に適しています。  <xref:System.Windows.Controls.RichTextBox> は、書式設定されたテキスト、イメージ、テーブル、またはその他のサポートされているコンテンツを編集する必要がある場合に適しています。  たとえば、書式設定やイメージなどが必要なドキュメント、記事、またはブログを編集する場合は、<xref:System.Windows.Controls.RichTextBox> を使用することをお勧めします。  <xref:System.Windows.Controls.TextBox> および <xref:System.Windows.Controls.TextBox> の主要な機能を次の表にまとめます。  
  
|Control|リアルタイム スペル チェック|コンテキスト メニュー|<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctrl \+ B\) などの書式設定コマンド|イメージ、段落、テーブルなどの <xref:System.Windows.Documents.FlowDocument> コンテンツ|  
|-------------|---------------------|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|○|○|Ｘ|いいえ。|  
|<xref:System.Windows.Controls.RichTextBox>|○|○|○ \([RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md) を参照\)|○ \([RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md) を参照\)|  
  
> [!NOTE]
>  <xref:System.Windows.Controls.TextBox> では <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctrl \+ B\) などの書式設定関連の編集コマンドはサポートされませんが、<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> などのさまざまな基本コマンドが両方のコントロールでサポートされています。  詳細については、<xref:System.Windows.Documents.EditingCommands> のトピックを参照してください。  
  
 <xref:System.Windows.Controls.TextBox> でサポートされる機能については、以降のセクションで説明します。  <xref:System.Windows.Controls.RichTextBox> の詳細については、「[RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)」を参照してください。  
  
### リアルタイム スペル チェック  
 <xref:System.Windows.Controls.TextBox> または <xref:System.Windows.Controls.RichTextBox> では、リアルタイム スペルチェックを有効にすることができます。  スペル チェックを有効にすると、スペル ミスがある単語の下に赤い線が表示されます \(下図を参照\)。  
  
 ![スペル チェックを含む Textbox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing\_TextBox\_with\_Spellchecking")  
  
 スペル チェックを有効にする方法については、「[テキスト編集コントロールでスペル チェックを有効にする](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)」を参照してください。  
  
### コンテキスト メニュー  
 既定で、<xref:System.Windows.Controls.TextBox> と <xref:System.Windows.Controls.RichTextBox> の両方に、ユーザーがコントロール内を右クリックしたときに表示されるコンテキスト メニューが用意されています。  コンテキスト メニューを使用すると、ユーザーは切り取り、コピー、または貼り付けを実行できます \(下図を参照\)。  
  
 ![コンテキスト メニューを含む TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing\_TextBox\_with\_Context\_Menu")  
  
 独自のカスタム コンテキスト メニューを作成して、既定の動作をオーバーライドできます。  詳細については、「[TextBox でカスタム コンテキスト メニューを使用する](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)」を参照してください。  
  
<a name="creating_textboxes"></a>   
## TextBox の作成  
 <xref:System.Windows.Controls.TextBox> は、高さを単一行にすることも、複数行から構成することもできます。  単一行の <xref:System.Windows.Controls.TextBox> は、少量のプレーンテキスト \(フォームの "  氏名" や "電話番号"  など\) の入力に適しています。  単一行の <xref:System.Windows.Controls.TextBox> を作成する方法を次の例に示します。  
  
 [!code-xml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 複数行のテキストを入力できる <xref:System.Windows.Controls.TextBox> を作成することもできます。  たとえば、フォームでユーザーの簡単な経歴の入力を求める場合は、複数行のテキストをサポートする <xref:System.Windows.Controls.TextBox> を使用します。  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して複数行のテキストが収まるように自動的に拡大する <xref:System.Windows.Controls.TextBox> コントロールを定義する方法を次の例に示します。  
  
 [!code-xml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 <xref:System.Windows.Controls.TextBox.TextWrapping%2A> 属性を `Wrap` に設定した場合、テキストは <xref:System.Windows.Controls.TextBox> コントロールの端に達すると次の行に折り返されます。<xref:System.Windows.Controls.TextBox> コントロールは、新しい行が収まるように必要に応じて自動的に調整されます。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> 属性を `true` に設定した場合は、Enter キーを押すたびに新しい行が挿入されます。このときも、<xref:System.Windows.Controls.TextBox> は新しい行が収まるように必要に応じて自動的に調整されます。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> 属性を設定すると <xref:System.Windows.Controls.TextBox> にスクロール バーが追加され、<xref:System.Windows.Controls.TextBox> がそれを囲むフレームまたはウィンドウのサイズよりも大きくなった場合は、<xref:System.Windows.Controls.TextBox> の内容をスクロールすることができます。  
  
 <xref:System.Windows.Controls.TextBox> の使用に関連するさまざまなタスクの詳細については、「[方法のトピック](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)」を参照してください。  
  
<a name="editing_commands"></a>   
## コンテンツの変更の検出  
 <xref:System.Windows.Controls.TextBox> または <xref:System.Windows.Controls.RichTextBox> 内のテキストが変わったことを検出するには、<xref:System.Windows.UIElement.KeyDown> イベントを使用すると思われがちですが、通常は <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> イベントを使用する必要があります。  例については、「[TextBox のテキストがいつ変更されたかを検出する](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md)」を参照してください。  
  
## 参照  
 [方法のトピック](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)