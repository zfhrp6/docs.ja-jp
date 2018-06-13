---
title: ポップアップの概要
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: c9261e2151f116b46a0c25d8dc775bf41bf932b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557577"
---
# <a name="popup-overview"></a>ポップアップの概要
<xref:System.Windows.Controls.Primitives.Popup>コントロールは、指定された要素または画面座標の基準とした、現在のアプリケーション ウィンドウで別のウィンドウの内容を表示する方法を提供します。 このトピックでは、<xref:System.Windows.Controls.Primitives.Popup>制御し、その使用に関する情報を提供します。  
  
 
  
<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>ポップアップとは  
 A<xref:System.Windows.Controls.Primitives.Popup>要素または画面上のポイントを基準とした別のウィンドウでコントロールがコンテンツを表示します。 ときに、<xref:System.Windows.Controls.Primitives.Popup>が表示されて、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>プロパティに設定されている`true`です。  
  
> [!NOTE]
>  A<xref:System.Windows.Controls.Primitives.Popup>が自動的に開かないその親オブジェクト上にマウス ポインターが移動したとき。 場合は、<xref:System.Windows.Controls.Primitives.Popup>を自動的に開くを使用して、<xref:System.Windows.Controls.ToolTip>または<xref:System.Windows.Controls.ToolTipService>クラスです。 詳細については、[ToolTip の概要](../../../../docs/framework/wpf/controls/tooltip-overview.md)を参照してください。  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>ポップアップの作成  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.Primitives.Popup>であるコントロールの子要素、<xref:System.Windows.Controls.Button>コントロール。 <xref:System.Windows.Controls.Button> 1 つだけの子要素を持つことができます、この例のテキストの配置、<xref:System.Windows.Controls.Button>と<xref:System.Windows.Controls.Primitives.Popup>コントロールで、<xref:System.Windows.Controls.StackPanel>です。 内容、<xref:System.Windows.Controls.Primitives.Popup>に表示されます、<xref:System.Windows.Controls.TextBlock>近く、関連アプリケーションのウィンドウで別のウィンドウでテキストを表示するコントロールを<xref:System.Windows.Controls.Button>コントロール。  
  
 [!code-xaml[PopupSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>ポップアップを実装するコントロール  
 構築できます<xref:System.Windows.Controls.Primitives.Popup>を他のコントロールにコントロールできます。 次のコントロールは、実装、<xref:System.Windows.Controls.Primitives.Popup>特定の使用目的。  
  
-   <xref:System.Windows.Controls.ToolTip>。 要素にツールヒントを作成する場合は、使用、<xref:System.Windows.Controls.ToolTip>と<xref:System.Windows.Controls.ToolTipService>クラスです。 詳細については、[ToolTip の概要](../../../../docs/framework/wpf/controls/tooltip-overview.md)を参照してください。  
  
-   <xref:System.Windows.Controls.ContextMenu>。 要素のコンテキスト メニューを作成する場合は、使用、<xref:System.Windows.Controls.ContextMenu>コントロール。 詳細については、[ContextMenu の概要](../../../../docs/framework/wpf/controls/contextmenu-overview.md)を参照してください。  
  
-   <xref:System.Windows.Controls.ComboBox>。 表示または非表示に使用することができるドロップダウン リスト ボックスのある選択コントロールを作成する場合、<xref:System.Windows.Controls.ComboBox>コントロール。  
  
-   <xref:System.Windows.Controls.Expander>。 コンテンツを表示する折りたたみ可能な領域を持つヘッダーを表示するコントロールを作成する場合、使用して、<xref:System.Windows.Controls.Expander>コントロール。 詳細については、 [Expander の概要](../../../../docs/framework/wpf/controls/expander-overview.md)を参照してください。  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>ポップアップの動作と外観  
 <xref:System.Windows.Controls.Primitives.Popup>コントロールには、その動作と外観をカスタマイズできるようにする機能が用意されています。 オープンとクローズの動作、アニメーション、不透明度およびビットマップ効果を設定するなどして<xref:System.Windows.Controls.Primitives.Popup>サイズと位置。  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>オープンとクローズの動作  
 A<xref:System.Windows.Controls.Primitives.Popup>コントロールには、そのコンテンツが表示されます。 ときに、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>プロパティがに設定されている`true`です。 既定では、<xref:System.Windows.Controls.Primitives.Popup>まで開いたまま、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>プロパティに設定されている`false`です。 ただしを設定して既定の動作を変更することができます、<xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A>プロパティを`false`です。 このプロパティを設定すると`false`、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ ウィンドウがマウス キャプチャを保持します。 <xref:System.Windows.Controls.Primitives.Popup>外、マウス イベントが発生したときにキャプチャし、ウィンドウを閉じますマウスを失った、<xref:System.Windows.Controls.Primitives.Popup>ウィンドウです。  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened>と<xref:System.Windows.Controls.Primitives.Popup.Closed>イベントが発生するときに、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ ウィンドウが開いているか閉じています。  
  
<a name="Animation"></a>   
### <a name="animation"></a>アニメーション  
 <xref:System.Windows.Controls.Primitives.Popup>コントロールがフェードインやスライド ショーのような動作に通常関連付けられているアニメーション用の組み込みサポートを備えています。 これらのアニメーションをオンに設定して、<xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A>プロパティを<xref:System.Windows.Controls.Primitives.PopupAnimation>列挙値。 <xref:System.Windows.Controls.Primitives.Popup>アニメーションが正常に動作を設定する必要があります、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>プロパティを`true`です。  
  
 ようなアニメーションを適用することもできます。<xref:System.Windows.Media.Animation.Storyboard>を、<xref:System.Windows.Controls.Primitives.Popup>コントロール。  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>不透明度とビットマップ効果  
 <xref:System.Windows.UIElement.Opacity%2A>プロパティを<xref:System.Windows.Controls.Primitives.Popup>コントロールがそのコンテンツに対する影響を与えません。 既定では、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ ウィンドウは非透過的です。 透過的なを作成する<xref:System.Windows.Controls.Primitives.Popup>、設定、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>プロパティを`true`です。  
  
 内容、<xref:System.Windows.Controls.Primitives.Popup>などビットマップ効果を引き継がない<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>、直接に対して設定すること、<xref:System.Windows.Controls.Primitives.Popup>コントロールまたはその他の要素の親ウィンドウにします。 ビットマップ効果の内容を<xref:System.Windows.Controls.Primitives.Popup>、その内容に直接ビットマップ効果を設定する必要があります。 たとえば場合の子、<xref:System.Windows.Controls.Primitives.Popup>は、<xref:System.Windows.Controls.StackPanel>のビットマップ効果を設定、<xref:System.Windows.Controls.StackPanel>です。  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>ポップアップのサイズ  
 既定では、<xref:System.Windows.Controls.Primitives.Popup>そのコンテンツのサイズが自動的にします。 自動サイズ変更が発生すると一部のビットマップ効果が非表示にするために定義されている画面の領域の既定のサイズ、<xref:System.Windows.Controls.Primitives.Popup>コンテンツがビットマップ効果を表示するのに十分な容量を提供していません。  
  
 <xref:System.Windows.Controls.Primitives.Popup> 設定すると、コンテンツを隠されることも、<xref:System.Windows.UIElement.RenderTransform%2A>内容にします。 このシナリオでいくつかのコンテンツが非表示にする場合、変換後のコンテンツ<xref:System.Windows.Controls.Primitives.Popup>、元の領域からはみ出した<xref:System.Windows.Controls.Primitives.Popup>です。 ビットマップ効果または変換より多くの領域が必要とする場合は、周囲に余白を定義することができます、<xref:System.Windows.Controls.Primitives.Popup>コンテンツ コントロールの複数の領域を提供するためにします。  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>ポップアップ位置の定義  
 ポップアップを配置するには、設定、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および<xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty>プロパティです。 詳細については、「[Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md)」を参照してください。 ときに<xref:System.Windows.Controls.Primitives.Popup>表示される画面にが再配置されない場合は、親の位置を変更します。  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>ポップアップの配置のカスタマイズ  
 配置をカスタマイズすることができます、<xref:System.Windows.Controls.Primitives.Popup>コントロールを基準には、座標のセットを指定することによって、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>する場所、<xref:System.Windows.Controls.Primitives.Popup>を表示します。  
  
 配置をカスタマイズする設定、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>です。 定義し、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>のような配置ポイントとの優先順位) の「プライマリ軸のセット返すデリゲート、<xref:System.Windows.Controls.Primitives.Popup>です。 最大の一部を示しています、ポイント、<xref:System.Windows.Controls.Primitives.Popup>が自動的に選択します。 例については、「[方法 : ポップアップのカスタム位置を指定する](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md)」をご覧ください。  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>ポップアップとビジュアル ツリー  
 A<xref:System.Windows.Controls.Primitives.Popup>コントロールには、独自のビジュアル ツリーがありません。 代わりに、サイズは 0 を返します (ゼロ) の場合に、<xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A>メソッド<xref:System.Windows.Controls.Primitives.Popup>と呼びます。 ただし、設定、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A>プロパティ<xref:System.Windows.Controls.Primitives.Popup>に`true`、独自のビジュアル ツリーを新しいウィンドウを作成します。 新しいウィンドウには、<xref:System.Windows.Controls.Primitives.Popup.Child%2A>のコンテンツ<xref:System.Windows.Controls.Primitives.Popup>です。 新しいウィンドウの幅および高さは、画面の幅または高さの 75% より大きくすることはできません。  
  
 <xref:System.Windows.Controls.Primitives.Popup>コントロールへの参照を保持する、<xref:System.Windows.Controls.Primitives.Popup.Child%2A>論理子としてコンテンツ。 作成時に、新しいウィンドウが、コンテンツの<xref:System.Windows.Controls.Primitives.Popup>visual の子ウィンドウの論理子のままになり<xref:System.Windows.Controls.Primitives.Popup>です。 これに対し、<xref:System.Windows.Controls.Primitives.Popup>の論理上の親のまま、<xref:System.Windows.Controls.Primitives.Popup.Child%2A>コンテンツ。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Primitives.Popup>  
 <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>  
 <xref:System.Windows.Controls.Primitives.PlacementMode>  
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>  
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [方法トピック](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
