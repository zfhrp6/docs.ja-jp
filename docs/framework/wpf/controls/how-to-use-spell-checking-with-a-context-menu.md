---
title: '方法 : コンテキスト メニューでスペル チェックを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
ms.openlocfilehash: 966e3adbcb57c30a55d606f6d6b8b51523ee30ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553768"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>方法 : コンテキスト メニューでスペル チェックを使用する
既定では、編集コントロールでスペル チェックを有効にする場合と同様に<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>、コンテキスト メニューでスペル チェックの選択肢を取得します。 たとえば、ユーザーは、スペル ミスの単語を右クリックし、ときに取得した一連のスペル修正候補またはオプション**すべて無視**です。 ただし、独自のカスタムのコンテキスト メニューで、既定のコンテキスト メニューをオーバーライドするときにこの機能は失われ、コンテキスト メニューの スペル チェック機能を再度有効にするコードを記述する必要があります。 次の例で有効にする方法を示しています、<xref:System.Windows.Controls.TextBox>です。  
  
## <a name="example"></a>例  
 次の例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を作成する、<xref:System.Windows.Controls.TextBox>コンテキスト メニューの実装に使用される一部のイベントにします。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>例  
 次の例では、コンテキスト メニューを実装するコードを示します。  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 これを行うために使用するコード、<xref:System.Windows.Controls.RichTextBox>と似ています。 主な違いは、パラメーターに渡される、`GetSpellingError`メソッドです。 <xref:System.Windows.Controls.TextBox>、キャレット位置の整数のインデックスを渡します。  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <xref:System.Windows.Controls.RichTextBox>、渡す、<xref:System.Windows.Documents.TextPointer>キャレット位置を指定します。  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>関連項目  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [テキスト編集コントロールでスペル チェックを有効にする](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)  
 [TextBox でカスタム コンテキスト メニューを使用する](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
