---
title: '方法 : RichTextBox からテキスト コンテンツを抽出する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
ms.openlocfilehash: 309fe15c76c17a79e11341f3a50c0bf5a7a2cc21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553937"
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a><span data-ttu-id="386cf-102">方法 : RichTextBox からテキスト コンテンツを抽出する</span><span class="sxs-lookup"><span data-stu-id="386cf-102">How to: Extract the Text Content from a RichTextBox</span></span>
<span data-ttu-id="386cf-103">この例の内容を抽出する方法を示しています、<xref:System.Windows.Controls.RichTextBox>プレーン テキストとして。</span><span class="sxs-lookup"><span data-stu-id="386cf-103">This example shows how to extract the contents of a <xref:System.Windows.Controls.RichTextBox> as plain text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="386cf-104">例</span><span class="sxs-lookup"><span data-stu-id="386cf-104">Example</span></span>  
 <span data-ttu-id="386cf-105">次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]コード説明、名前付き<xref:System.Windows.Controls.RichTextBox>単純コンテンツを持つコントロール。</span><span class="sxs-lookup"><span data-stu-id="386cf-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a><span data-ttu-id="386cf-106">例</span><span class="sxs-lookup"><span data-stu-id="386cf-106">Example</span></span>  
 <span data-ttu-id="386cf-107">次のコードを受け取るメソッドを実装する、<xref:System.Windows.Controls.RichTextBox>を引数としてのプレーン テキストの内容を表す文字列を返します、<xref:System.Windows.Controls.RichTextBox>です。</span><span class="sxs-lookup"><span data-stu-id="386cf-107">The following code implements a method that takes a <xref:System.Windows.Controls.RichTextBox> as an argument, and returns a string representing the plain text contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="386cf-108">メソッドが新たに作成<xref:System.Windows.Documents.TextRange>の内容から、<xref:System.Windows.Controls.RichTextBox>を使用して、<xref:System.Windows.Documents.FlowDocument.ContentStart%2A>と<xref:System.Windows.Documents.FlowDocument.ContentEnd%2A>を抽出する内容の範囲を示します。</span><span class="sxs-lookup"><span data-stu-id="386cf-108">The method creates a new <xref:System.Windows.Documents.TextRange> from the contents of the <xref:System.Windows.Controls.RichTextBox>, using the <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> to indicate the range of the contents to extract.</span></span>  <span data-ttu-id="386cf-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> および<xref:System.Windows.Documents.FlowDocument.ContentEnd%2A>各プロパティを返す、 <xref:System.Windows.Documents.TextPointer>、基になる FlowDocument の内容を表すにアクセスし、<xref:System.Windows.Controls.RichTextBox>です。</span><span class="sxs-lookup"><span data-stu-id="386cf-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> properties each return a <xref:System.Windows.Documents.TextPointer>, and are accessible on the underlying FlowDocument that represents the contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  <span data-ttu-id="386cf-110"><xref:System.Windows.Documents.TextRange> プレーン テキスト部分を返します、テキストのプロパティを提供、<xref:System.Windows.Documents.TextRange>を文字列として。</span><span class="sxs-lookup"><span data-stu-id="386cf-110"><xref:System.Windows.Documents.TextRange> provides a Text property, which returns the plain text portions of the <xref:System.Windows.Documents.TextRange> as a string.</span></span>  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a><span data-ttu-id="386cf-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="386cf-111">See Also</span></span>  
 [<span data-ttu-id="386cf-112">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="386cf-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="386cf-113">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="386cf-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
