---
title: '方法 : FocusVisualStyle をコントロールに適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 34af5ca6f5ce6b3714d7d7e0d707841cdfc61349
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543733"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>方法 : FocusVisualStyle をコントロールに適用する
この例は、リソースにフォーカス visual スタイルを作成して、コントロールにスタイルを適用する方法を示しますを使用して、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>プロパティです。  
  
## <a name="example"></a>例  
 次の例は、そのコントロールがキーボードでのフォーカスされたときにのみ適用する追加コントロールの複合を作成するスタイルを定義、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。 設定されたスタイルを定義することによってこれは、 <xref:System.Windows.Controls.ControlTemplate>、参照をリソースとしてのスタイルを設定するときに、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>プロパティ。  
  
 境界線に似た外部四角形は四角形の領域の外側に配置します。 スタイルのサイジングを使用して、それ以外の場合は変更しない限り、<xref:System.Windows.FrameworkElement.ActualHeight%2A>と<xref:System.Windows.FrameworkElement.ActualWidth%2A>四角形のコントロールがフォーカス visual スタイルが適用されるのです。 この例に負の値の設定、<xref:System.Windows.FrameworkElement.Margin%2A>フォーカスされたコントロールの外に若干表示枠を作成します。  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 A<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>に付属している任意のコントロール テンプレート スタイル加法から、明示的なスタイルまたはテーマ スタイル; コントロールの主なスタイルも作成できますを使用して、<xref:System.Windows.Controls.ControlTemplate>にそのスタイルを設定して、<xref:System.Windows.FrameworkElement.Style%2A>プロパティです。  
  
 Visual スタイルは、テーマ、または、UI の間で一貫して使用する必要がありますフォーカス フォーカス可能な要素ごとに別の名前を使用するのではなくです。 詳細については、「[コントロール、および FocusVisualStyle でフォーカスのスタイルは](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [コントロールのフォーカスのスタイルと FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
