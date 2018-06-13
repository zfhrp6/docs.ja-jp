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
# <a name="how-to-use-spell-checking-with-a-context-menu"></a><span data-ttu-id="0099d-102">方法 : コンテキスト メニューでスペル チェックを使用する</span><span class="sxs-lookup"><span data-stu-id="0099d-102">How to: Use Spell Checking with a Context Menu</span></span>
<span data-ttu-id="0099d-103">既定では、編集コントロールでスペル チェックを有効にする場合と同様に<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.RichTextBox>、コンテキスト メニューでスペル チェックの選択肢を取得します。</span><span class="sxs-lookup"><span data-stu-id="0099d-103">By default, when you enable spell checking in an editing control like <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>, you get spell-checking choices in the context menu.</span></span> <span data-ttu-id="0099d-104">たとえば、ユーザーは、スペル ミスの単語を右クリックし、ときに取得した一連のスペル修正候補またはオプション**すべて無視**です。</span><span class="sxs-lookup"><span data-stu-id="0099d-104">For example, when users right-click a misspelled word, they get a set of spelling suggestions or the option to **Ignore All**.</span></span> <span data-ttu-id="0099d-105">ただし、独自のカスタムのコンテキスト メニューで、既定のコンテキスト メニューをオーバーライドするときにこの機能は失われ、コンテキスト メニューの スペル チェック機能を再度有効にするコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0099d-105">However, when you override the default context menu with your own custom context menu, this functionality is lost, and you need to write code to reenable the spell-checking feature in the context menu.</span></span> <span data-ttu-id="0099d-106">次の例で有効にする方法を示しています、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="0099d-106">The following example shows how to enable this on a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0099d-107">例</span><span class="sxs-lookup"><span data-stu-id="0099d-107">Example</span></span>  
 <span data-ttu-id="0099d-108">次の例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を作成する、<xref:System.Windows.Controls.TextBox>コンテキスト メニューの実装に使用される一部のイベントにします。</span><span class="sxs-lookup"><span data-stu-id="0099d-108">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that creates a <xref:System.Windows.Controls.TextBox> with some events that are used to implement the context menu.</span></span>  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="0099d-109">例</span><span class="sxs-lookup"><span data-stu-id="0099d-109">Example</span></span>  
 <span data-ttu-id="0099d-110">次の例では、コンテキスト メニューを実装するコードを示します。</span><span class="sxs-lookup"><span data-stu-id="0099d-110">The following example shows the code that implements the context menu.</span></span>  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 <span data-ttu-id="0099d-111">これを行うために使用するコード、<xref:System.Windows.Controls.RichTextBox>と似ています。</span><span class="sxs-lookup"><span data-stu-id="0099d-111">The code used for doing this with a <xref:System.Windows.Controls.RichTextBox> is similar.</span></span> <span data-ttu-id="0099d-112">主な違いは、パラメーターに渡される、`GetSpellingError`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0099d-112">The main difference is in the parameter passed to the `GetSpellingError` method.</span></span> <span data-ttu-id="0099d-113"><xref:System.Windows.Controls.TextBox>、キャレット位置の整数のインデックスを渡します。</span><span class="sxs-lookup"><span data-stu-id="0099d-113">For a <xref:System.Windows.Controls.TextBox>, pass the integer index of the caret position:</span></span>  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <span data-ttu-id="0099d-114"><xref:System.Windows.Controls.RichTextBox>、渡す、<xref:System.Windows.Documents.TextPointer>キャレット位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="0099d-114">For a <xref:System.Windows.Controls.RichTextBox>, pass the <xref:System.Windows.Documents.TextPointer> that specifies the caret position:</span></span>  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a><span data-ttu-id="0099d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0099d-115">See Also</span></span>  
 [<span data-ttu-id="0099d-116">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="0099d-116">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="0099d-117">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="0099d-117">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="0099d-118">テキスト編集コントロールでスペル チェックを有効にする</span><span class="sxs-lookup"><span data-stu-id="0099d-118">Enable Spell Checking in a Text Editing Control</span></span>](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)  
 [<span data-ttu-id="0099d-119">TextBox でカスタム コンテキスト メニューを使用する</span><span class="sxs-lookup"><span data-stu-id="0099d-119">Use a Custom Context Menu with a TextBox</span></span>](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
