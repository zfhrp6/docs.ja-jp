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
# <a name="textblock-overview"></a>TextBlock の概要
<xref:System.Windows.Controls.TextBlock>コントロールがテキストの柔軟なサポートを提供[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。 この要素は、主として、複数段落のテキストを必要としない、基本的な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] シナリオを対象にしています。 など、プレゼンテーションを正確に制御を有効にするプロパティの数がサポートしている<xref:System.Windows.Controls.TextBlock.FontFamily%2A>、 <xref:System.Windows.Controls.TextBlock.FontSize%2A>、 <xref:System.Windows.Controls.TextBlock.FontWeight%2A>、 <xref:System.Windows.Controls.TextBlock.TextEffects%2A>、および<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>です。 使用してテキストの内容を追加することができます、<xref:System.Windows.Controls.TextBlock.Text%2A>プロパティです。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で使用すると、オープン タグとクローズ タグの間の内容は、要素のテキストとして暗黙的に追加されます。  
  
 A<xref:System.Windows.Controls.TextBlock>要素は非常に簡単を使用してインスタンス化できる[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。  
  
 [!code-xaml[TextBlockSnip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 同様に、使用量を<xref:System.Windows.Controls.TextBlock>コード内の要素は比較的簡単です。  
  
 [!code-csharp[TextBlockSnip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Label>
