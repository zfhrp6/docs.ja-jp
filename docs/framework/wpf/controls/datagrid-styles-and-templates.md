---
title: DataGrid のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
ms.openlocfilehash: 71c9b08407c6e570b42c4fbb7dc264829b5dc17c
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457585"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid のスタイルとテンプレート
このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.DataGrid>コントロール。 既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="datagrid-parts"></a>DataGrid のパーツ  
 次の表に、名前付きのパーツの<xref:System.Windows.Controls.DataGrid>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|列ヘッダーを含んでいる行。|  
  
 作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.DataGrid>、テンプレートを含めることがあります、<xref:System.Windows.Controls.ItemsPresenter>内で、<xref:System.Windows.Controls.ScrollViewer>です。 (、<xref:System.Windows.Controls.ItemsPresenter>内の各項目を表示、 <xref:System.Windows.Controls.DataGrid>;<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできるように) します。  場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`です。  
  
 既定のテンプレート、<xref:System.Windows.Controls.DataGrid>が含まれています、<xref:System.Windows.Controls.ScrollViewer>コントロール。 によって定義されたパートの詳細については、<xref:System.Windows.Controls.ScrollViewer>を参照してください[ScrollViewer スタイルとテンプレート](../../../../docs/framework/wpf/controls/scrollviewer-styles-and-templates.md)です。  
  
## <a name="datagrid-states"></a>DataGrid の状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.DataGrid>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|無効|CommonStates|コントロールが無効になっています。|  
|InvalidFocused|ValidationStates|コントロールが無効で、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールが無効で、フォーカスがありません。|  
|有効|ValidationStates|コントロールは有効です。|  
  
## <a name="datagridcell-parts"></a>DataGridCell 部分  
 <xref:System.Windows.Controls.DataGridCell>要素には、すべて名前付きのパートはありません。  
  
## <a name="datagridcell-states"></a>DataGridCell 状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.DataGridCell>要素。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがセル上で配置されます。|  
|フォーカスされている|FocusStates|セルには、フォーカスがあります。|  
|フォーカスされていない|FocusStates|セルにフォーカスがないです。|  
|現在|CurrentStates|セルは、現在のセルです。|  
|Regular|CurrentStates|セルは、現在のセルではありません。|  
|表示|InteractionStates|セルが表示モードです。|  
|編集|InteractionStates|セルが編集モードです。|  
|選択済み|SelectionStates|セルが選択されます。|  
|未選択|SelectionStates|セルが選択されていません。|  
|InvalidFocused|ValidationStates|セルが正しくないと、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|セルが正しくないと、フォーカスされていません。|  
|有効|ValidationStates|セルは有効です。|  
  
## <a name="datagridrow-parts"></a>DataGridRow 部分  
 <xref:System.Windows.Controls.DataGridRow>要素には、すべて名前付きのパートはありません。  
  
## <a name="datagridrow-states"></a>DataGridRow 状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.DataGridRow>要素。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターが行位置します。|  
|MouseOver_Editing|CommonStates|行の上にマウス ポインターが配置されているし、行が編集モードにします。|  
|MouseOver_Selected|CommonStates|行の上にマウス ポインターが配置されているし、行を選択します。|  
|MouseOver_Unfocused_Editing|CommonStates|行の上にマウス ポインターが配置されているは、行モードを編集し、フォーカスを持っていません。|  
|MouseOver_Unfocused_Selected|CommonStates|行の上にマウス ポインターが配置されている、行が選択され、フォーカスを持っていません。|  
|Normal_AlternatingRow|CommonStates|その行は、交互の行です。|  
|Normal_Editing|CommonStates|行は編集モードです。|  
|Normal_Selected|CommonStates|行が選択されます。|  
|Unfocused_Editing|CommonStates|この行は、編集モードでは、れ、フォーカスされていません。|  
|Unfocused_Selected|CommonStates|行が選択され、フォーカスを持っていません。|  
|InvalidFocused|ValidationStates|コントロールが無効で、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールが無効で、フォーカスがありません。|  
|有効|ValidationStates|コントロールは有効です。|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader 部分  
 次の表に、名前付きのパーツの<xref:System.Windows.Controls.Primitives.DataGridRowHeader>要素。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|上部の行ヘッダーのサイズを変更するために使用する要素。|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|下部から、行ヘッダーのサイズを変更するために使用する要素。|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader 状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.DataGridRowHeader>要素。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターが行位置します。|  
|MouseOver_CurrentRow|CommonStates|行の上にマウス ポインターが配置されているし、行は、現在の行。|  
|MouseOver_CurrentRow_Selected|CommonStates|、行の上にマウス ポインターが配置されているし、は、行の現在および選択します。|  
|MouseOver_EditingRow|CommonStates|行の上にマウス ポインターが配置されているし、行が編集モードにします。|  
|MouseOver_Selected|CommonStates|行の上にマウス ポインターが配置されているし、行を選択します。|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|マウス ポインターが配置されている、行、行は、現在選択されているとにフォーカスがないです。|  
|MouseOver_Unfocused_EditingRow|CommonStates|行の上にマウス ポインターが配置されているは、行モードを編集し、フォーカスを持っていません。|  
|MouseOver_Unfocused_Selected|CommonStates|行の上にマウス ポインターが配置されている、行が選択され、フォーカスを持っていません。|  
|Normal_CurrentRow|CommonStates|行は、現在の行です。|  
|Normal_CurrentRow_Selected|CommonStates|行は、現在の行は、され、選択されます。|  
|Normal_EditingRow|CommonStates|行は編集モードです。|  
|Normal_Selected|CommonStates|行が選択されます。|  
|Unfocused_CurrentRow_Selected|CommonStates|行を現在の行が選択されている、フォーカスを持っていません。|  
|Unfocused_EditingRow|CommonStates|この行は、編集モードでは、れ、フォーカスされていません。|  
|Unfocused_Selected|CommonStates|行が選択され、フォーカスを持っていません。|  
|InvalidFocused|ValidationStates|コントロールが無効で、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールが無効で、フォーカスがありません。|  
|有効|ValidationStates|コントロールは有効です。|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter 部分  
 次の表に、名前付きのパーツの<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>要素。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|列ヘッダーのプレース ホルダーです。|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter 状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>要素。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|InvalidFocused|ValidationStates|セルが正しくないと、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|セルが正しくないと、フォーカスされていません。|  
|有効|ValidationStates|セルは有効です。|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader 部分  
 次の表に、名前付きのパーツの<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>要素。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|左側の列ヘッダーのサイズを変更するために使用する要素。|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|右側の列ヘッダーのサイズを変更するために使用する要素。|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader 状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>要素。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|押されている|CommonStates|コントロールが押されています。|  
|SortAscending|SortStates|列は、昇順で並べ替えられます。|  
|SortDescending|SortStates|列は、降順で並べ替えられます。|  
|並べ替えられていません。|SortStates|列が並べ替えられていません。|  
|InvalidFocused|ValidationStates|コントロールが無効で、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールが無効で、フォーカスがありません。|  
|有効|ValidationStates|コントロールは有効です。|  
  
## <a name="datagrid-controltemplate-example"></a>DataGrid ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.DataGrid>コントロールとその関連する型。  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
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
