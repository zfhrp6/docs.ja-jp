---
title: "TextBlock の概要 | Microsoft Docs"
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
  - "TextBlock コントロール"
  - "TextBlock コントロール"
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# TextBlock の概要
<xref:System.Windows.Controls.TextBlock>コントロールは、柔軟性の高いテキストのサポートの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。 要素が、主として、basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]&1; つ以上の段落のテキストを必要としないシナリオです。 いくつかのように、プレゼンテーションを正確に制御が利用可能なプロパティがサポートしている<xref:System.Windows.Controls.TextBlock.FontFamily%2A>、 <xref:System.Windows.Controls.TextBlock.FontSize%2A>、 <xref:System.Windows.Controls.TextBlock.FontWeight%2A>、 <xref:System.Windows.Controls.TextBlock.TextEffects%2A>、および<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>します。 使用してテキストの内容を追加できる、<xref:System.Windows.Controls.TextBlock.Text%2A>プロパティです。 使用すると[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素のテキストとして、オープン、および終了タグの間でコンテンツが暗黙的に追加します。  
  
 A <xref:System.Windows.Controls.TextBlock>非常に簡単に使用して要素をインスタンス化することができます[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
 [!code-xml[TextBlockSnip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 同様に、使用量を<xref:System.Windows.Controls.TextBlock>コード内の要素は比較的簡単です。  
  
 [!code-csharp[TextBlockSnip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Label>