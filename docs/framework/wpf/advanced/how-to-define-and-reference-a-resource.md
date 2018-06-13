---
title: '方法 : リソースを定義および参照する'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 347804f0ce6dd3b907d3ac088248a64569a63695
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543495"
---
# <a name="how-to-define-and-reference-a-resource"></a>方法 : リソースを定義および参照する
この例は、内の属性を使用して、参照およびリソースを定義する方法を示しています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。  
  
## <a name="example"></a>例  
 次の例は、次の 2 つの種類のリソースを定義します。、<xref:System.Windows.Media.SolidColorBrush>リソース、およびいくつか<xref:System.Windows.Style>リソース。 <xref:System.Windows.Media.SolidColorBrush>リソース`MyBrush`それぞれ受け取るいくつかのプロパティの値を提供するため、<xref:System.Windows.Media.Brush>値を入力します。 <xref:System.Windows.Style>リソース`PageBackground`、`TitleText`と`Label`特定のコントロール型を対象の各します。 スタイルは、そのスタイル リソースのリソース キーによって参照され、設定に使用されるときに、対象となるコントロールのさまざまなプロパティを設定、<xref:System.Windows.FrameworkElement.Style%2A>プロパティで定義されているいくつかの特定のコントロール要素の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
 注釈のいずれかのプロパティの中の set アクセス操作子、`Label`スタイル参照、`MyBrush`前に定義されたリソース。 これは、一般的な手法が、リソースが解析され、指定した順序でリソース ディクショナリに入力したことに注意してください。 使用する場合は、ディクショナリ内で見つかった順序により、リソースが要求も、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)から別のリソース内で参照します。 参照されている任意のリソースがそのリソースを要求しよりリソースのコレクション内で以前に定義されていることを確認してください。 かどうか、必要に応じてを回避できますリソース refererences の厳密な作成順を使用して、 [DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)代わりに、実行時にリソースを参照する注意する必要がありますをこの DynamicResource手法には、パフォーマンスへの影響があります。 詳細については、「 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>関連項目  
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)
