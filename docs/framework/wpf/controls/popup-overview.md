---
title: "ポップアップの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コントロール, ポップアップ"
  - "ポップアップ コントロール [WPF], ポップアップ コントロールの概要"
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# ポップアップの概要
<xref:System.Windows.Controls.Primitives.Popup> コントロールは、現在のアプリケーション ウィンドウの上の別のウィンドウにコンテンツを表示するための手段です。ウィンドウの表示位置は、特定の要素を基準として、または画面座標として指定されます。  ここでは、<xref:System.Windows.Controls.Primitives.Popup> コントロールの概要と、使用方法に関する情報を示します。  
  
   
  
<a name="What_Is_a_Popup_"></a>   
## ポップアップとは  
 <xref:System.Windows.Controls.Primitives.Popup> コントロールは、画面上の要素または点を基準として別のウィンドウにコンテンツを表示します。  <xref:System.Windows.Controls.Primitives.Popup> が表示されているときは、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> プロパティが `true` に設定されています。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Primitives.Popup> は、マウス ポインターが親オブジェクト上に移動したときに自動的に開くわけではありません。  <xref:System.Windows.Controls.Primitives.Popup> が自動的に開くようにする場合は、<xref:System.Windows.Controls.ToolTip> クラスまたは <xref:System.Windows.Controls.ToolTipService> クラスを使用します。  詳細については、「[ToolTip の概要](../../../../docs/framework/wpf/controls/tooltip-overview.md)」を参照してください。  
  
<a name="APopupExample"></a>   
## ポップアップの作成  
 <xref:System.Windows.Controls.Button> コントロールの子要素である <xref:System.Windows.Controls.Primitives.Popup> コントロールを定義する方法を次の例に示します。  <xref:System.Windows.Controls.Button> が持つことのできる子要素は 1 つだけであるので、この例では、<xref:System.Windows.Controls.Button> コントロールおよび <xref:System.Windows.Controls.Primitives.Popup> コントロールのテキストを <xref:System.Windows.Controls.StackPanel> の中に配置します。  <xref:System.Windows.Controls.Primitives.Popup> のコンテンツは <xref:System.Windows.Controls.TextBlock> コントロールに表示されます。このコントロールのテキストは、アプリケーション ウィンドウ上の、関連付けられた <xref:System.Windows.Controls.Button> コントロールの近くにフロート表示される別のウィンドウに表示されます。  
  
 [!code-xml[PopupSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xml[PopupSimple#CreatePopupCodeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## ポップアップを実装するコントロール  
 <xref:System.Windows.Controls.Primitives.Popup> コントロールは、他のコントロールの中に組み込むことができます。  次のコントロールは、特定の使用目的の <xref:System.Windows.Controls.Primitives.Popup> コントロールを実装します。  
  
-   <xref:System.Windows.Controls.ToolTip>.  要素のツールヒントを作成する場合は、<xref:System.Windows.Controls.ToolTip> クラスと <xref:System.Windows.Controls.ToolTipService> クラスを使用します。  詳細については、「[ToolTip の概要](../../../../docs/framework/wpf/controls/tooltip-overview.md)」を参照してください。  
  
-   <xref:System.Windows.Controls.ContextMenu>.  要素のコンテキスト メニューを作成する場合は、<xref:System.Windows.Controls.ContextMenu> コントロールを使用します。  詳細については、「[ContextMenu の概要](../../../../docs/framework/wpf/controls/contextmenu-overview.md)」を参照してください。  
  
-   <xref:System.Windows.Controls.ComboBox>.  表示と非表示の切り替えが可能なドロップダウン リスト ボックスを持つ選択コントロールを作成する場合は、<xref:System.Windows.Controls.ComboBox> コントロールを使用します。  
  
-   <xref:System.Windows.Controls.Expander>.  コンテンツを表示するための折りたたみ可能な領域を持つヘッダーを表示するコントロールを作成する場合は、<xref:System.Windows.Controls.Expander> コントロールを使用します。  詳細については、「[エキスパンダーの概要](../../../../docs/framework/wpf/controls/expander-overview.md)」を参照してください。  
  
<a name="PopupBehaviorandAppearance"></a>   
## ポップアップの動作および外観  
 <xref:System.Windows.Controls.Primitives.Popup> コントロールには、その動作および外観をカスタマイズするための機能があります。  たとえば、開く動作と閉じる動作、アニメーション、透過度効果とビットマップ効果、および <xref:System.Windows.Controls.Primitives.Popup> のサイズと位置を設定できます。  
  
<a name="OpenandCloseBehavior"></a>   
### 開く\/閉じるの動作  
 <xref:System.Windows.Controls.Primitives.Popup> コントロールのコンテンツが表示されるのは、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> プロパティが `true` に設定されているときです。  既定の設定では、<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> プロパティが `false` に設定されるまでは <xref:System.Windows.Controls.Primitives.Popup> が開いたままになります。  この既定の動作を変更するには、<xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> プロパティを `false` に設定します。  このプロパティが `false` に設定されると、<xref:System.Windows.Controls.Primitives.Popup> コンテンツ ウィンドウがマウス キャプチャを持ちます。  <xref:System.Windows.Controls.Primitives.Popup> ウィンドウの外部でマウス イベントが発生すると、<xref:System.Windows.Controls.Primitives.Popup> はマウス キャプチャを失い、ウィンドウが閉じます。  
  
 <xref:System.Windows.Controls.Primitives.Popup> コンテンツ ウィンドウが開いたときと閉じたときに、<xref:System.Windows.Controls.Primitives.Popup.Opened> イベントおよび <xref:System.Windows.Controls.Primitives.Popup.Closed> イベントが発生します。  
  
<a name="Animation"></a>   
### アニメーション  
 <xref:System.Windows.Controls.Primitives.Popup> コントロールには、フェード インやスライド インのような動作に関連付けられているアニメーションのサポートが組み込まれています。  このようなアニメーションを有効にするには、<xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> プロパティを <xref:System.Windows.Controls.Primitives.PopupAnimation> 列挙値に設定します。  <xref:System.Windows.Controls.Primitives.Popup> アニメーションを正常に動作させるためには、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> プロパティを `true` に設定する必要があります。  
  
 <xref:System.Windows.Media.Animation.Storyboard> のようなアニメーションを <xref:System.Windows.Controls.Primitives.Popup> コントロールに適用することもできます。  
  
<a name="OpacityandBitmapEffects"></a>   
### 透過度効果とビットマップ効果  
 <xref:System.Windows.Controls.Primitives.Popup> コントロールの <xref:System.Windows.UIElement.Opacity%2A> プロパティは、コンテンツには影響しません。  既定の設定では、<xref:System.Windows.Controls.Primitives.Popup> コンテンツ ウィンドウは不透明です。  透明の <xref:System.Windows.Controls.Primitives.Popup> を作成するには、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> プロパティを `true` に設定します。  
  
 <xref:System.Windows.Controls.Primitives.Popup> のコンテンツは、<xref:System.Windows.Media.Effects.DropShadowBitmapEffect> などのビットマップ効果を継承しません。ビットマップ効果は、<xref:System.Windows.Controls.Primitives.Popup> コントロールに対して直接設定されることも、親ウィンドウのその他の要素に対して設定されることもあります。  ビットマップ効果を <xref:System.Windows.Controls.Primitives.Popup> のコンテンツに反映させるには、ビットマップ効果を直接コンテンツに対して設定する必要があります。  たとえば、<xref:System.Windows.Controls.Primitives.Popup> の子が <xref:System.Windows.Controls.StackPanel> の場合は、<xref:System.Windows.Controls.StackPanel> に対してビットマップ効果を設定します。  
  
<a name="PopupSize"></a>   
### ポップアップのサイズ  
 既定の設定では、<xref:System.Windows.Controls.Primitives.Popup> のサイズはコンテンツに合わせて自動的に調整されます。  自動サイズ変更が行われたときに、ビットマップ効果の一部が反映されなくなることがあります。<xref:System.Windows.Controls.Primitives.Popup> のコンテンツに対して定義された画面領域の既定のサイズが、ビットマップ効果を表示するのに十分ではない場合です。  
  
 また、コンテンツに対して <xref:System.Windows.UIElement.RenderTransform%2A> を設定した場合も、<xref:System.Windows.Controls.Primitives.Popup> のコンテンツが隠されることがあります。  このシナリオでは、変換後の <xref:System.Windows.Controls.Primitives.Popup> の領域が元の <xref:System.Windows.Controls.Primitives.Popup> の領域よりも広い場合に、一部のコンテンツが非表示になります。  ビットマップ効果または変換のために広い領域が必要な場合は、<xref:System.Windows.Controls.Primitives.Popup> コンテンツの周囲のマージンを定義して、コントロールの領域を広げます。  
  
<a name="DefiningPopupPosition"></a>   
## ポップアップの位置の定義  
 ポップアップの配置は、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、<xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> の各プロパティを設定して指定できます。  詳細については、「[ポップアップの配置動作](../../../../docs/framework/wpf/controls/popup-placement-behavior.md)」を参照してください。  <xref:System.Windows.Controls.Primitives.Popup> が画面に表示されると、その親の位置が変更された場合でも、それ自体の位置は変更されません。  
  
<a name="CustomizingPopupPlacement"></a>   
### ポップアップの配置のカスタマイズ  
 <xref:System.Windows.Controls.Primitives.Popup> コントロールを表示する位置を、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> を基準とする相対座標として指定することで、<xref:System.Windows.Controls.Primitives.Popup> の配置をカスタマイズできます。  
  
 配置をカスタマイズするには、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> プロパティを <xref:System.Windows.Controls.Primitives.PlacementMode> に設定します。  次に、<xref:System.Windows.Controls.Primitives.Popup> で使用可能な配置ポイントおよび主軸のセット \(優先度順\) を返す <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> デリゲートを定義します。  <xref:System.Windows.Controls.Primitives.Popup> の最大部分を示すポイントは、自動的に選択されます。  例については、「[ポップアップのカスタム位置を指定する](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md)」を参照してください。  
  
<a name="PopupandtheVisualTree"></a>   
## ポップアップとビジュアル ツリー  
 <xref:System.Windows.Controls.Primitives.Popup> コントロールは独自の[ビジュアル ツリー](GTMT)を持たないので、<xref:System.Windows.Controls.Primitives.Popup> の <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> メソッドが呼び出されると、代わりにサイズ 0 を返します。  ただし、<xref:System.Windows.Controls.Primitives.Popup> の <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> プロパティを `true` に設定すると、独自のビジュアル ツリーを持つ新しいウィンドウが作成されます。  新しいウィンドウには、<xref:System.Windows.Controls.Primitives.Popup> の <xref:System.Windows.Controls.Primitives.Popup.Child%2A> コンテンツが表示されます。  新しいウィンドウの幅と高さは、最大で画面の幅または高さの 75% までです。  
  
 <xref:System.Windows.Controls.Primitives.Popup> コントロールは、論理上の子として <xref:System.Windows.Controls.Primitives.Popup.Child%2A> コンテンツへの参照を保持します。  新しいウィンドウが作成されたときに、<xref:System.Windows.Controls.Primitives.Popup> のコンテンツはビジュアル ツリー上でウィンドウの子になりますが、<xref:System.Windows.Controls.Primitives.Popup> の論理上の子のままです。  逆に、<xref:System.Windows.Controls.Primitives.Popup> は、<xref:System.Windows.Controls.Primitives.Popup.Child%2A> コンテンツの論理上の親のままです。  
  
## 参照  
 <xref:System.Windows.Controls.Primitives.Popup>   
 <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>   
 <xref:System.Windows.Controls.Primitives.PlacementMode>   
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>   
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>   
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipService>   
 [方法のトピック](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)