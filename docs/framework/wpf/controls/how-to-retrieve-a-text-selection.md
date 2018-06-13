---
title: '方法 : テキスト選択を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: 6b25c555d5e6cac93b2e1518b25e7880ab77c866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552013"
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="f94b0-102">方法 : テキスト選択を取得する</span><span class="sxs-lookup"><span data-stu-id="f94b0-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="f94b0-103">この例を使用する方法を示しています、<xref:System.Windows.Controls.TextBox.SelectedText%2A>で、ユーザーが選択したテキストを取得するプロパティを<xref:System.Windows.Controls.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="f94b0-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f94b0-104">例</span><span class="sxs-lookup"><span data-stu-id="f94b0-104">Example</span></span>  
 <span data-ttu-id="f94b0-105">次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の定義の例、<xref:System.Windows.Controls.TextBox>を選択するにはいくつかのテキストを含むコントロールと<xref:System.Windows.Controls.Button>と指定したコントロール<xref:System.Windows.Controls.Button.OnClick%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f94b0-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="f94b0-106">この例では、ボタンに関連付けられている<xref:System.Windows.Controls.Primitives.ButtonBase.Click>テキスト選択範囲を取得するイベント ハンドラーを使用します。</span><span class="sxs-lookup"><span data-stu-id="f94b0-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="f94b0-107">ユーザーは、ボタンをクリックしたときに、<xref:System.Windows.Controls.Button.OnClick%2A>メソッドは、文字列に、テキスト ボックスで、選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="f94b0-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="f94b0-108">特定の状況で選択されているテキストを取得 (ボタンをクリックすると、) も (テキストの選択を文字列にコピー)、選択範囲で実行されるアクションは、さまざまなシナリオに合わせて簡単に変更できます。</span><span class="sxs-lookup"><span data-stu-id="f94b0-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="f94b0-109">例</span><span class="sxs-lookup"><span data-stu-id="f94b0-109">Example</span></span>  
 <span data-ttu-id="f94b0-110">次の c# の例は、<xref:System.Windows.Controls.Button.OnClick%2A>で定義されているボタンのイベント ハンドラー、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]この例です。</span><span class="sxs-lookup"><span data-stu-id="f94b0-110">The following C# example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="f94b0-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f94b0-111">See Also</span></span>  
 [<span data-ttu-id="f94b0-112">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="f94b0-112">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="f94b0-113">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="f94b0-113">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
