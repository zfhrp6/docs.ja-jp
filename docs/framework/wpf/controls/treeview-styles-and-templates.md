---
title: TreeView のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TreeView
- templates [WPF], TreeView
- parts [WPF], TreeView
- states [WPF], TreeView
- styles [WPF], TreeView
- TreeView [WPF], styles and templates
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
ms.openlocfilehash: 9f963e4b60193197ae56e2021d76d541ad6bfbef
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34456771"
---
# <a name="treeview-styles-and-templates"></a>TreeView のスタイルとテンプレート
このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.TreeView>コントロール。 既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="treeview-parts"></a>TreeView のパーツ  
 <xref:System.Windows.Controls.TreeView>コントロールには、その名前付きの部分はありません。  
  
 作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.TreeView>、テンプレートを含めることがあります、<xref:System.Windows.Controls.ItemsPresenter>内で、<xref:System.Windows.Controls.ScrollViewer>です。 (、<xref:System.Windows.Controls.ItemsPresenter>内の各項目を表示、 <xref:System.Windows.Controls.TreeView>;<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできるように) します。  場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`です。  
  
## <a name="treeview-states"></a>TreeView の状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.TreeView>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem のパーツ  
 次の表に、名前付きのパーツの<xref:System.Windows.Controls.TreeViewItem>コントロール。  
  
|パーツ|型|説明|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|視覚的要素をそのヘッダーのコンテンツを含む、<xref:System.Windows.Controls.TreeView>コントロール。|  
  
## <a name="treeviewitem-states"></a>TreeViewItem の状態  
 次の表に、用ビジュアル状態<xref:System.Windows.Controls.TreeViewItem>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターを置いた、<xref:System.Windows.Controls.TreeViewItem>です。|  
|無効|CommonStates|<xref:System.Windows.Controls.TreeViewItem>は無効になります。|  
|フォーカスされている|FocusStates|<xref:System.Windows.Controls.TreeViewItem>にフォーカスがあります。|  
|フォーカスされていない|FocusStates|<xref:System.Windows.Controls.TreeViewItem>がフォーカスされていません。|  
|展開済み|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem>コントロールが展開されています。|  
|Collapsed|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem>コントロールが折りたたまれています。|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem>項目があります。|  
|項目|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem>に項目がないです。|  
|選択済み|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>が選択されています。|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>が選択したアクティブではありません。|  
|未選択|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>が選択されていません。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="treeview-controltemplate-example"></a>TreeView ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.TreeView>コントロールとその関連する型。  
  
 [!code-xaml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 前の例では、次のリソースの 1 つ以上を使用します。  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
