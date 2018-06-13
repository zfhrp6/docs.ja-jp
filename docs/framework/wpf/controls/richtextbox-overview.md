---
title: RichTextBox の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: 319dc43c0953b82da94eb6dd698f1a6afd582dbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557525"
---
# <a name="richtextbox-overview"></a>RichTextBox の概要
<xref:System.Windows.Controls.RichTextBox>コントロールでは、表示または段落、画像、テーブルなどのフロー コンテンツを編集することができます。 このトピックでは、<xref:System.Windows.Controls.TextBox>クラスし、両方で使用する方法の例を示します[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]と C# の場合。  
  
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox か RichTextBox か  
 両方<xref:System.Windows.Controls.RichTextBox>と<xref:System.Windows.Controls.TextBox>テキストを編集できるように、ただし、2 つのコントロールがさまざまなシナリオで使用します。 A<xref:System.Windows.Controls.RichTextBox>書式付きテキスト、画像、テーブル、またはその他の豊富なコンテンツを編集するユーザーの必要がある場合をお勧めします。 たとえば、画像、ドキュメント、アーティクル、または書式設定を必要とするブログを編集などの使用が最も適切な<xref:System.Windows.Controls.RichTextBox>します。 A<xref:System.Windows.Controls.TextBox>システム リソースが必要です、<xref:System.Windows.Controls.RichTextBox>のみプレーン テキストする必要があります (つまりフォームで使用) を編集する際に最適とします。 参照してください[TextBox 概要](../../../../docs/framework/wpf/controls/textbox-overview.md)について<xref:System.Windows.Controls.TextBox>です。 次の表の主な機能をまとめたもの<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.RichTextBox>です。  
  
|コントロール|リアルタイム スペル チェック|コンテキスト メニュー|ようなコマンドの書式設定<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(範囲 + B)|<xref:System.Windows.Documents.FlowDocument> イメージ、段落、テーブルなどのコンテンツ。|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|[はい]|はい|×|いいえ。|  
|<xref:System.Windows.Controls.RichTextBox>|[はい]|はい|はい|[はい]|  
  
 **注:** が<xref:System.Windows.Controls.TextBox>のように関連するコマンドの書式設定をサポートしていません<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(範囲 + B)、多くの基本的なコマンドがなどの両方のコントロールでサポートされて<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>です。  
  
 上の表の機能については、後で詳しく説明します。  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>RichTextBox の作成  
 次のコードを作成する方法を示しています、<xref:System.Windows.Controls.RichTextBox>ユーザーがの豊富なコンテンツを編集できます。  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 具体的には、コンテンツの編集、<xref:System.Windows.Controls.RichTextBox>フロー コンテンツを示します。 フロー コンテンツは、書式設定されたテキスト、イメージ、リスト、テーブルなどのさまざまな種類の要素を格納できます。 フロー ドキュメントの詳細については、[フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)を参照してください。 フロー コンテンツを格納するために、<xref:System.Windows.Controls.RichTextBox>ホスト、<xref:System.Windows.Documents.FlowDocument>オブジェクトが編集可能なコンテンツが含まれています。 フロー コンテンツを示すために、 <xref:System.Windows.Controls.RichTextBox>、次のコードを作成する方法を示しています、<xref:System.Windows.Controls.RichTextBox>段落といくつかの太字で表示されるテキストを使用します。  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 次の図は、このサンプルがレンダリングする方法を示しています。  
  
 ![RichTextBox with content](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 などの要素<xref:System.Windows.Documents.Paragraph>と<xref:System.Windows.Documents.Bold>を決定する方法の内部コンテンツ、<xref:System.Windows.Controls.RichTextBox>が表示されます。 ユーザーが編集と<xref:System.Windows.Controls.RichTextBox>コンテンツを変更することもこのフロー コンテンツ。 フロー コンテンツの機能およびその操作方法の詳細については、[フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)を参照してください。  
  
 **注:** 内のコンテンツをフローする<xref:System.Windows.Controls.RichTextBox>フロー コンテンツを他のコントロールに含まれているのと同じように動作しません。 たとえば、内の列がない、<xref:System.Windows.Controls.RichTextBox>のため自動サイズ変更なしの動作とします。 また、組み込み機能の検索、表示モード、ページ ナビゲーション、およびズームは、内で使用できるように、<xref:System.Windows.Controls.RichTextBox>です。  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>リアルタイム スペル チェック  
 リアルタイムでスペル チェックを有効にすることができます、<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>です。 スペル チェックをオンにすると、スペル ミスの語句の下に赤色の線が表示されます (下図を参照)。  
  
 ![スペル チェックを含む Textbox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 スペル チェックを有効にする方法については、「[テキスト編集コントロールでスペル チェックを有効にする](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)」を参照してください。  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>コンテキスト メニュー  
 既定では、両方とも<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.RichTextBox>コントロール内にユーザーを右クリックしたときに表示されるコンテキスト メニューが表示されます。 コンテキスト メニューでは、ユーザーは、切り取り、コピー、または貼り付けをできます (下図を参照)。  
  
 ![コンテキスト メニューを含む TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 独自のカスタム コンテキスト メニューを作成して、既定のコンテキスト メニューをオーバーライドできます。 詳細については、[カスタム コンテキスト メニューを RichTextBox に配置](../../../../docs/framework/wpf/controls/how-to-position-a-custom-context-menu-in-a-richtextbox.md)を参照してください。  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>コマンドの編集  
 コマンド内の編集可能なコンテンツを書式設定を有効にするユーザーの編集、<xref:System.Windows.Controls.RichTextBox>です。 Basic だけでなく編集コマンド、<xref:System.Windows.Controls.RichTextBox>を含むコマンドの書式設定<xref:System.Windows.Controls.TextBox>はサポートしていません。 例で編集するときの<xref:System.Windows.Controls.RichTextBox>ユーザーには、太字のテキストの書式設定を切り替えるには、範囲 B がキーを押して可能性があります。 参照してください<xref:System.Windows.Documents.EditingCommands>可能なコマンドの完全な一覧についてはします。 キーボード ショートカットを使用するだけでなく、ボタンのようにコマンドをフックしてその他のコントロールにすることができます。 次の例では、テキストの書式設定を変更するためにユーザーが使用できるボタンを含む簡単なツールバーを作成する方法を示します。  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 次の図は、このサンプルの表示方法を示しています。  
  
 ![ツールバーを含む RichTextBox](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>コンテンツがいつ変更されたかの検出  
 通常、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>を検出するたびにイベントを使用する必要があります内のテキスト、<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>変更ではなく<xref:System.Windows.UIElement.KeyDown>想定される場合があります。 例については、「[TextBox のテキストがいつ変更されたかを検出する](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md)」を参照してください。  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>RichTextBox コンテンツの保存、読み込み、および印刷  
 次の例の内容を保存する方法を示しています、<xref:System.Windows.Controls.RichTextBox>をファイルにそのコンテンツの状態に戻してを読み込み、 <xref:System.Windows.Controls.RichTextBox>、および内容を印刷します。 この例のマークアップを次に示します。  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 この例のコードを次に示します。  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 [方法トピック](../../../../docs/framework/wpf/controls/richtextbox-how-to-topics.md)  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)
