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
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a>方法 : RichTextBox からテキスト コンテンツを抽出する
この例の内容を抽出する方法を示しています、<xref:System.Windows.Controls.RichTextBox>プレーン テキストとして。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]コード説明、名前付き<xref:System.Windows.Controls.RichTextBox>単純コンテンツを持つコントロール。  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a>例  
 次のコードを受け取るメソッドを実装する、<xref:System.Windows.Controls.RichTextBox>を引数としてのプレーン テキストの内容を表す文字列を返します、<xref:System.Windows.Controls.RichTextBox>です。  
  
 メソッドが新たに作成<xref:System.Windows.Documents.TextRange>の内容から、<xref:System.Windows.Controls.RichTextBox>を使用して、<xref:System.Windows.Documents.FlowDocument.ContentStart%2A>と<xref:System.Windows.Documents.FlowDocument.ContentEnd%2A>を抽出する内容の範囲を示します。  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> および<xref:System.Windows.Documents.FlowDocument.ContentEnd%2A>各プロパティを返す、 <xref:System.Windows.Documents.TextPointer>、基になる FlowDocument の内容を表すにアクセスし、<xref:System.Windows.Controls.RichTextBox>です。  <xref:System.Windows.Documents.TextRange> プレーン テキスト部分を返します、テキストのプロパティを提供、<xref:System.Windows.Documents.TextRange>を文字列として。  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a>関連項目  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)
