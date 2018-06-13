---
title: TextBlock の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], TextBlock
- TextBlock control [WPF]
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
ms.openlocfilehash: c18ca64a25f436c3ed2ccd9e04316e25bab00a66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556082"
---
# <a name="textblock-overview"></a><span data-ttu-id="cb653-102">TextBlock の概要</span><span class="sxs-lookup"><span data-stu-id="cb653-102">TextBlock Overview</span></span>
<span data-ttu-id="cb653-103"><xref:System.Windows.Controls.TextBlock>コントロールがテキストの柔軟なサポートを提供[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="cb653-103">The <xref:System.Windows.Controls.TextBlock> control provides flexible text support for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="cb653-104">この要素は、主として、複数段落のテキストを必要としない、基本的な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] シナリオを対象にしています。</span><span class="sxs-lookup"><span data-stu-id="cb653-104">The element is targeted primarily toward basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios that do not require more than one paragraph of text.</span></span> <span data-ttu-id="cb653-105">など、プレゼンテーションを正確に制御を有効にするプロパティの数がサポートしている<xref:System.Windows.Controls.TextBlock.FontFamily%2A>、 <xref:System.Windows.Controls.TextBlock.FontSize%2A>、 <xref:System.Windows.Controls.TextBlock.FontWeight%2A>、 <xref:System.Windows.Controls.TextBlock.TextEffects%2A>、および<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>です。</span><span class="sxs-lookup"><span data-stu-id="cb653-105">It supports a number of properties that enable precise control of presentation, such as <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, and <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>.</span></span> <span data-ttu-id="cb653-106">使用してテキストの内容を追加することができます、<xref:System.Windows.Controls.TextBlock.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="cb653-106">Text content can be added using the <xref:System.Windows.Controls.TextBlock.Text%2A> property.</span></span> <span data-ttu-id="cb653-107">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で使用すると、オープン タグとクローズ タグの間の内容は、要素のテキストとして暗黙的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="cb653-107">When used in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], content between the open and closing tag is implicitly added as the text of the element.</span></span>  
  
 <span data-ttu-id="cb653-108">A<xref:System.Windows.Controls.TextBlock>要素は非常に簡単を使用してインスタンス化できる[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="cb653-108">A <xref:System.Windows.Controls.TextBlock> element can be instantiated very simply using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[TextBlockSnip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 <span data-ttu-id="cb653-109">同様に、使用量を<xref:System.Windows.Controls.TextBlock>コード内の要素は比較的簡単です。</span><span class="sxs-lookup"><span data-stu-id="cb653-109">Similarly, usage of the <xref:System.Windows.Controls.TextBlock> element in code is relatively simple.</span></span>  
  
 [!code-csharp[TextBlockSnip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cb653-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb653-110">See Also</span></span>  
 <xref:System.Windows.Controls.Label>
