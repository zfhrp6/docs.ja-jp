---
title: "RichTextBox の概要 | Microsoft Docs"
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
  - "コントロール, RichTextBox"
  - "RichTextBox コントロール [WPF], RichTextBox コントロールの概要"
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# RichTextBox の概要
<xref:System.Windows.Controls.RichTextBox> コントロールを使用すると、段落、イメージ、テーブルなどのフロー コンテンツを表示または編集できます。  このトピックでは、<xref:System.Windows.Controls.TextBox> クラスについて説明し、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] と [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)] の両方で使用する例を示します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="textbox_or_richtextbox"></a>   
## TextBox と RichTextBox  
 <xref:System.Windows.Controls.RichTextBox> と <xref:System.Windows.Controls.TextBox> のどちらを使用してもテキストを編集できますが、2 つのコントロールは異なるシナリオで使用されます。  <xref:System.Windows.Controls.RichTextBox> は、書式設定されたテキスト、イメージ、テーブル、またはその他のリッチ コンテンツを編集する必要がある場合に適しています。  たとえば、書式設定やイメージなどが必要なドキュメント、記事、またはブログを編集する場合は、<xref:System.Windows.Controls.RichTextBox> を使用することをお勧めします。  <xref:System.Windows.Controls.TextBox> で必要なシステム リソースは <xref:System.Windows.Controls.RichTextBox> よりも少ないため、プレーンテキストのみを編集する必要がある場合 \(  フォームでの使用\) に適しています。  <xref:System.Windows.Controls.TextBox> の詳細については、「[TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)」を参照してください。  <xref:System.Windows.Controls.TextBox> および <xref:System.Windows.Controls.RichTextBox> の主要な機能を次の表にまとめます。  
  
|Control|リアルタイム スペル チェック|コンテキスト メニュー|<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctrl \+ B\) などの書式設定コマンド|イメージ、段落、テーブルなどの <xref:System.Windows.Documents.FlowDocument> コンテンツ|  
|-------------|---------------------|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|○|○|Ｘ|いいえ。|  
|<xref:System.Windows.Controls.RichTextBox>|○|○|○|○|  
  
 **メモ :** <xref:System.Windows.Controls.TextBox> では <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctrl \+ B\) などの書式設定関連のコマンドはサポートされませんが、<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> などのさまざまな基本コマンドが両方のコントロールでサポートされています。  
  
 上の表に示した機能については、後で詳しく説明します。  
  
<a name="creating_a_richtextbox"></a>   
## RichTextBox の作成  
 次のコードでは、ユーザーがリッチ コンテンツを編集できる <xref:System.Windows.Controls.RichTextBox> を作成する方法を示します。  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 具体的に言えば、<xref:System.Windows.Controls.RichTextBox> で編集されるコンテンツはフロー コンテンツです。  フロー コンテンツには、書式設定されたテキスト、イメージ、リスト、およびテーブルなどのさまざまな種類の要素を格納できます。  フロー ドキュメントの詳細については、「[フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)」を参照してください。  フロー コンテンツを格納するために、<xref:System.Windows.Controls.RichTextBox> が <xref:System.Windows.Documents.FlowDocument> オブジェクトをホストし、そのオブジェクトが編集可能コンテンツを格納します。  <xref:System.Windows.Controls.RichTextBox> のフロー コンテンツを示すために、次のコードで、段落と太字テキストのある <xref:System.Windows.Controls.RichTextBox> を作成する方法を示します。  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 このサンプルの表示結果を次の図に示します。  
  
 ![内容を含む RichTextBox](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-content.png "Editing\_RichTextBox\_with\_Content")  
  
 <xref:System.Windows.Documents.Paragraph> や <xref:System.Windows.Documents.Bold> などの要素は、<xref:System.Windows.Controls.RichTextBox> 内のコンテンツがどのように表示されるかを決定します。  ユーザーが <xref:System.Windows.Controls.RichTextBox> のコンテンツを編集すると、これらの要素がこのフロー コンテンツを変更します。  フロー コンテンツの機能、およびその使用方法の詳細については、「[フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)」を参照してください。  
  
 **メモ :** <xref:System.Windows.Controls.RichTextBox> 内のフロー コンテンツの動作は、他のコントロールに格納されたフロー コンテンツの動作とは異なる場合があります。  たとえば、<xref:System.Windows.Controls.RichTextBox> 内には列が存在しないため、自動サイズ変更動作もありません。  また、検索、表示モード、ページ ナビゲーション、およびズームなどの組み込み機能も、<xref:System.Windows.Controls.RichTextBox> 内では使用できません。  
  
<a name="realtime_spellechecking"></a>   
## リアルタイム スペル チェック  
 <xref:System.Windows.Controls.TextBox> または <xref:System.Windows.Controls.RichTextBox> でリアルタイム スペル チェックを有効にすることができます。  スペル チェックを有効にすると、スペル ミスがある単語の下に赤い線が表示されます \(下図を参照\)。  
  
 ![スペル チェックを含む Textbox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing\_TextBox\_with\_Spellchecking")  
  
 スペル チェックを有効にする方法については、「[テキスト編集コントロールでスペル チェックを有効にする](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)」を参照してください。  
  
<a name="context_menu"></a>   
## コンテキスト メニュー  
 既定で、<xref:System.Windows.Controls.TextBox> と <xref:System.Windows.Controls.RichTextBox> の両方に、ユーザーがコントロール内を右クリックしたときに表示されるコンテキスト メニューが用意されています。  コンテキスト メニューを使用すると、ユーザーは切り取り、コピー、または貼り付けを実行できます \(下図を参照\)。  
  
 ![コンテキスト メニューを含む TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing\_TextBox\_with\_Context\_Menu")  
  
 独自のカスタム コンテキスト メニューを作成して、既定のメニューをオーバーライドできます。  詳細については、「[カスタム コンテキスト メニューを RichTextBox に配置する](../../../../docs/framework/wpf/controls/how-to-position-a-custom-context-menu-in-a-richtextbox.md)」を参照してください。  
  
<a name="detect_when_content_changes"></a>   
## 編集コマンド  
 編集コマンドを使用することで、ユーザーは <xref:System.Windows.Controls.RichTextBox> 内の編集可能コンテンツを書式設定できます。  <xref:System.Windows.Controls.RichTextBox> には、基本的な編集コマンドのほかに、<xref:System.Windows.Controls.TextBox> ではサポートされていない書式設定コマンドが含まれています。  たとえば、<xref:System.Windows.Controls.RichTextBox> 内で編集を行う場合、ユーザーは Ctrl \+ B キーを押すことで、テキストの太字設定を切り替えることができます。  使用可能なコマンドの全リストについては、<xref:System.Windows.Documents.EditingCommands> を参照してください。  キーボード ショートカットを使用するほかに、コマンドをボタンなどのその他のコントロールにフックすることができます。  次の例では、ユーザーがテキストの書式設定を変更するために使用できるボタンを格納した簡単なツール バーを作成する方法を示します。  
  
 [!code-xml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 このサンプルの表示結果を次の図に示します。  
  
 ![ツール バーを含む RichTextBox](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-toobar.png "Editing\_RichTextBox\_with\_TooBar")  
  
<a name="editing_commands"></a>   
## コンテンツの変更の検出  
 <xref:System.Windows.Controls.TextBox> または <xref:System.Windows.Controls.RichTextBox> のテキストの変更を検出するには、<xref:System.Windows.UIElement.KeyDown> イベントを使用するのではなく、通常は <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> イベントを使用する必要があります。  例については、「[TextBox のテキストがいつ変更されたかを検出する](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md)」を参照してください。  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## RichTextBox コンテンツの保存、読み込み、および印刷  
 <xref:System.Windows.Controls.RichTextBox> のコンテンツをファイルに保存し、そのコンテンツを再び <xref:System.Windows.Controls.RichTextBox> に読み込み、そのコンテンツを印刷する方法を次の例に示します。  以下は、この例のマークアップです。  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 以下は、この例の分離コードです。  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## 参照  
 [方法のトピック](../../../../docs/framework/wpf/controls/richtextbox-how-to-topics.md)   
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)