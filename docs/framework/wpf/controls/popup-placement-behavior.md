---
title: ポップアップの配置動作
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 3aef3d7863bc02aa4164b1fc9ef4464fbe799cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="popup-placement-behavior"></a>ポップアップの配置動作
A<xref:System.Windows.Controls.Primitives.Popup>コントロールは、アプリケーションで別のウィンドウでコンテンツを表示します。 位置を指定することができます、<xref:System.Windows.Controls.Primitives.Popup>コントロール、マウス、またはを使用して、画面の基準とした、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>プロパティです。  これらのプロパティは指定した位置で柔軟性が協力して、<xref:System.Windows.Controls.Primitives.Popup>です。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip>と<xref:System.Windows.Controls.ContextMenu>クラスは、またこれら 5 つのプロパティを定義して、同様に動作します。  
  

  
<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>ポップアップの配置  
 配置、<xref:System.Windows.Controls.Primitives.Popup>を基準にすることができます、<xref:System.Windows.UIElement>または画面全体にします。  次の例は、4 つ作成<xref:System.Windows.Controls.Primitives.Popup>基準になるコントロール、 <xref:System.Windows.UIElement>— この場合は、イメージにします。 すべての<xref:System.Windows.Controls.Primitives.Popup>コントロールがある、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>プロパティに設定`image1`が各<xref:System.Windows.Controls.Primitives.Popup>配置のプロパティに異なる値を持ちます。  
  
 [!code-xaml[PopupPositionSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 次の図は、イメージ、および<xref:System.Windows.Controls.Primitives.Popup>コントロール  
  
 ![次の 4 つのポップアップ コントロールを持つイメージ](../../../../docs/framework/wpf/controls/media/popupplacementintro.png "PopupPlacementIntro")  
4 つのポップアップを含む画像  
  
 この簡単な例を設定する方法を示しています、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>と<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを使用して、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>、および<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>プロパティ、where より詳細に制御がある、<xref:System.Windows.Controls.Primitives.Popup>が配置されています。  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>用語の定義: ポップアップの構造  
 次の用語が理解に役立つ方法、 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>プロパティが相互に関連付けると<xref:System.Windows.Controls.Primitives.Popup>:  
  
-   ターゲット オブジェクト  
  
-   ターゲット領域  
  
-   ターゲットの始点  
  
-   ポップアップ配置ポイント  
  
 これらの用語のさまざまな側面を参照する便利な手段を提供する、<xref:System.Windows.Controls.Primitives.Popup>と関連付けられているコントロール。  
  
### <a name="target-object"></a>ターゲット オブジェクト  
 *ターゲット オブジェクト*要素を<xref:System.Windows.Controls.Primitives.Popup>に関連付けられています。 場合、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>プロパティが設定されて、ターゲット オブジェクトを指定します。  場合<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>が設定されていないと、<xref:System.Windows.Controls.Primitives.Popup>親を持つ、親は、ターゲット オブジェクト。  ある場合なし<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>値と親のない、ターゲット オブジェクトが存在しないと、<xref:System.Windows.Controls.Primitives.Popup>画面に対して相対的に配置します。  
  
 次の例を作成、<xref:System.Windows.Controls.Primitives.Popup>の子は、<xref:System.Windows.Controls.Canvas>です。  例は設定されません、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>プロパティを<xref:System.Windows.Controls.Primitives.Popup>です。 既定値<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>ので、<xref:System.Windows.Controls.Primitives.Popup>下に表示されます、<xref:System.Windows.Controls.Canvas>です。  
  
 [!code-xaml[PopupPositionSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 次の図は、ことを示しています、<xref:System.Windows.Controls.Primitives.Popup>に対して相対的な位置、<xref:System.Windows.Controls.Canvas>です。  
  
 ![Placementtarget のないポップアップ コントロール](../../../../docs/framework/wpf/controls/media/popupplacementnoplacementtarget.PNG "PopupPlacementNoPlacementTarget")  
PlacementTarget がないポップアップ  
  
 次の例を作成、<xref:System.Windows.Controls.Primitives.Popup>の子は、 <xref:System.Windows.Controls.Canvas>、今度は、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>に設定されている`ellipse1`の下のポップアップが表示されるように、<xref:System.Windows.Shapes.Ellipse>です。  
  
 [!code-xaml[PopupPositionSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 次の図は、ことを示しています、<xref:System.Windows.Controls.Primitives.Popup>に対して相対的な位置、<xref:System.Windows.Shapes.Ellipse>です。  
  
 ![楕円に相対的に配置されるポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementwithplacementtarget.PNG "PopupPlacementWithPlacementTarget")  
PlacementTarget があるポップアップ  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip>、既定値の<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>します。  <xref:System.Windows.Controls.ContextMenu>、既定値の<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>します。 これらの値については、後ほど「プロパティの連携のしくみ」で説明します。  
  
### <a name="target-area"></a>ターゲット領域  
 *ターゲット領*が画面上の領域を<xref:System.Windows.Controls.Primitives.Popup>に相対的であります。 前の例で、<xref:System.Windows.Controls.Primitives.Popup>は場合によっては、ターゲット オブジェクトの境界内で整列、<xref:System.Windows.Controls.Primitives.Popup>は他の境界に配置場合でも、<xref:System.Windows.Controls.Primitives.Popup>ターゲット オブジェクトがあります。  場合、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>プロパティが設定されて、ターゲットの領域がターゲット オブジェクトの境界と異なる。  
  
 次の例では、2 つ作成されます<xref:System.Windows.Controls.Canvas>オブジェクト、1 つを含む、<xref:System.Windows.Shapes.Rectangle>と<xref:System.Windows.Controls.Primitives.Popup>です。  どちらの場合、対象のオブジェクトを<xref:System.Windows.Controls.Primitives.Popup>は、<xref:System.Windows.Controls.Canvas>です。 <xref:System.Windows.Controls.Primitives.Popup> 、最初の<xref:System.Windows.Controls.Canvas>が、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定と、その<xref:System.Windows.Rect.X%2A>、 <xref:System.Windows.Rect.Y%2A>、 <xref:System.Windows.Rect.Width%2A>、および<xref:System.Windows.Rect.Height%2A>プロパティがそれぞれ 50、50、50、および 100 に設定します。 <xref:System.Windows.Controls.Primitives.Popup> 、2 番目の<xref:System.Windows.Controls.Canvas>はありません、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>を設定します。  その結果、最初の<xref:System.Windows.Controls.Primitives.Popup>の下にある、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、2 番目<xref:System.Windows.Controls.Primitives.Popup>の下にある、<xref:System.Windows.Controls.Canvas>です。 各<xref:System.Windows.Controls.Canvas>も含まれています、<xref:System.Windows.Shapes.Rectangle>と同じ境界を持つ、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>初めて<xref:System.Windows.Controls.Primitives.Popup>です。  なお、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>アプリケーションに表示されている要素を作成しません例は、作成、<xref:System.Windows.Shapes.Rectangle>を表す、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>です。  
  
 [!code-xaml[PopupPositionSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 次の図は、前の例の結果を示しています。  
  
 ![Placementrectangle がポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementplacementrectangle.PNG "PopupPlacementPlacementRectangle")  
PlacementRectangle がある (またはない) ポップアップ  
  
### <a name="target-origin-and-popup-alignment-point"></a>ターゲットの始点とポップアップ配置ポイント  
 *ターゲットの始点*と*ポップアップ配置ポイント*は、それぞれターゲット領域とポップアップ上の基準点であり、配置に使用します。 使用することができます、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>プロパティを対象となる領域からのポップアップをオフセットします。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>はターゲットの基準とポップアップ配置ポイントを基準とします。 値、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティは、ターゲットの基準とポップアップ配置ポイントがある場所を決定します。  
  
 次の例を作成、<xref:System.Windows.Controls.Primitives.Popup>設定と、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>20 プロパティです。  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティに設定されている<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>(既定)、ターゲットの基準は、対象領域の左下隅で、ポップアップ配置ポイントの左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。  
  
 [!code-xaml[PopupPositionSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 次の図は、前の例の結果を示しています。  
  
 ![ターゲットの元の配置ポイントを含むポップアップ配置](../../../../docs/framework/wpf/controls/media/popupplacementtargetoriginalignmentpoint.PNG "PopupPlacementTargetOriginAlignmentPoint")  
HorizontalOffset と VerticalOffset があるポップアップ  
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>プロパティの連携のしくみ  
 値<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、および<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>正しい対象領域、ターゲットの基準、およびポップアップ配置ポイントを一緒に考慮する必要があります。  たとえば場合の値<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、ターゲット オブジェクトが存在しない、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>は無視され、対象となる領域は、マウス ポインターの境界と。 その一方で場合、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>では、<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>または親が、ターゲット オブジェクトを判断し、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>対象領域を指定します。  
  
 次の表に、ターゲット オブジェクト、ターゲットの領域、ターゲットの基準、ポップアップ配置ポイントを説明を示し、かどうか<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>と<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>ごとに使用される<xref:System.Windows.Controls.Primitives.PlacementMode>列挙値。  
  
|PlacementMode|ターゲット オブジェクト|ターゲット領域|ターゲットの始点|ポップアップ配置ポイント|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|該当なし。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 無視されます。|画面または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>画面に対する相対パスです。|ターゲット領域の左上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|該当なし。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 無視されます。|画面または<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>画面に対する相対パスです。|ターゲット領域の左上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクトまたは<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>対象のオブジェクトに対する相対パスです。|ターゲット領域の左下隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクトまたは<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>対象のオブジェクトに対する相対パスです。|ターゲット領域の中央。|中央、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクトまたは<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>対象のオブジェクトに対する相対パスです。|定義される、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>です。|定義される、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクトまたは<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>対象のオブジェクトに対する相対パスです。|ターゲット領域の左上隅。|右上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|該当なし。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 無視されます。|マウス ポインターの境界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 無視されます。|ターゲット領域の左下隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|該当なし。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 無視されます。|マウス ポインターの境界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 無視されます。|ターゲット領域の左上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクトまたは<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>対象のオブジェクトに対する相対パスです。|ターゲット領域の左上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクトまたは<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>対象のオブジェクトに対する相対パスです。|ターゲット領域の左上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクトまたは<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>対象のオブジェクトに対する相対パスです。|ターゲット領域の右上隅。|左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> または、親。|ターゲット オブジェクトまたは<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>設定されている場合。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>対象のオブジェクトに対する相対パスです。|ターゲット領域の左上隅。|左下隅、<xref:System.Windows.Controls.Primitives.Popup>です。|  
  
 次の図に示さ、 <xref:System.Windows.Controls.Primitives.Popup>、対象となる領域、ターゲットの基準、およびポップアップ配置ポイントごとに<xref:System.Windows.Controls.Primitives.PlacementMode>値。 各図では、対象領域は黄色、および<xref:System.Windows.Controls.Primitives.Popup>は青で表示します。  
  
 ![Absolute または AbsolutePoint 配置を含むポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementabsolute.png "PopupPlacementAbsolute")  
Placement が Absolute または AbsolutePoint  
  
 ![Bottom 配置を含むポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementbottom.png "PopupPlacementBottom")  
Placement が Bottom  
  
 ![Center 配置を含むポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementcenter.png "PopupPlacementCenter")  
Placement が Center  
  
 ![左側の配置を含むポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementleft.png "PopupPlacementLeft")  
Placement が Left  
  
 ![マウスの配置を含むポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementmouse.png "PopupPlacementMouse")  
Placement が Mouse  
  
 ![MousePoint 配置を含むポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementmousepoint.png "PopupPlacementMousePoint")  
Placement が MousePoint  
  
 ![Relative または RelativePoint 配置を含むポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementrelative.png "PopupPlacementRelative")  
Placement が Relative または RelativePoint  
  
 ![Right 配置を含むポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementright.png "PopupPlacementRight")  
Placement が Right  
  
 ![Top 配置を含むポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementtop.png "PopupPlacementTop")  
Placement が Top  
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>ポップアップが画面の端と重なった場合  
 セキュリティ上の理由、<xref:System.Windows.Controls.Primitives.Popup>画面の端で非表示にすることはできません。 次の 3 つのいずれかが実行時に、<xref:System.Windows.Controls.Primitives.Popup>画面の端を検出します。  
  
-   ポップアップ ウィンドウが隠れてしまわないように画面の端に沿って realigns 自体、<xref:System.Windows.Controls.Primitives.Popup>です。  
  
-   ポップアップは別のポップアップ配置ポイントを使用します。  
  
-   ポップアップは別のターゲットの始点とポップアップ配置ポイントを使用します。  
  
 これらのオプションについては、このセクションの後半で詳しく説明します。  
  
 動作、<xref:System.Windows.Controls.Primitives.Popup>画面の端がの値に依存を検出すると、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティと画面の端のポップアップが発生しました。 次の表に、動作時に、<xref:System.Windows.Controls.Primitives.Popup>各画面の端を検出した<xref:System.Windows.Controls.Primitives.PlacementMode>値。  
  
|PlacementMode|上端|下端|左端|右端|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|上端に揃えます。|左下隅にポップアップ配置ポイントを変更、<xref:System.Windows.Controls.Primitives.Popup>です。|左端に揃えます。|右上隅にポップアップ配置ポイントを変更、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|上端に揃えます。|ターゲットの基準が対象領域の左上隅に変更され、ポップアップ配置ポイントの左下隅に変更、<xref:System.Windows.Controls.Primitives.Popup>です。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|上端に揃えます。|下端に揃えます。|ターゲットの基準を対象となる領域の右上隅とポップアップ配置ポイントに変更されますの左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>です。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|上端に揃えます。|ターゲットの基準を対象となる領域 (マウス ポインターの境界内) の左上隅とポップアップ配置ポイントに変更されますの左下隅、<xref:System.Windows.Controls.Primitives.Popup>です。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|上端に揃えます。|左下隅にポップアップ配置ポイントを変更、<xref:System.Windows.Controls.Primitives.Popup>です。|左端に揃えます。|ポップアップ配置ポイントが、ポップアップの右上隅に変更されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|上端に揃えます。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|上端に揃えます。|左下隅にポップアップ配置ポイントを変更、<xref:System.Windows.Controls.Primitives.Popup>です。|左端に揃えます。|ポップアップ配置ポイントが、ポップアップの右上隅に変更されます。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|上端に揃えます。|下端に揃えます。|左端に揃えます。|ターゲットの基準が対象となる領域の左上隅に変更およびの右上隅にポップアップ配置ポイントの変更、<xref:System.Windows.Controls.Primitives.Popup>です。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|ターゲットの基準が対象となる領域の左下隅に変更およびの左上隅にポップアップ配置ポイントの変更、<xref:System.Windows.Controls.Primitives.Popup>です。 実際には、これと同じ場合に<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>します。|下端に揃えます。|左端に揃えます。|右端に揃えます。|  
  
### <a name="aligning-to-the-screen-edge"></a>画面の端への配置  
 A<xref:System.Windows.Controls.Primitives.Popup>揃えることが、画面の端にため自体を再配置して全体<xref:System.Windows.Controls.Primitives.Popup>が画面に表示します。  この場合、ターゲットの基準とポップアップ配置ポイント間の距離可能性がありますの値と異なる<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>です。 ときに<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>、 <xref:System.Windows.Controls.Primitives.PlacementMode.Center>、または<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>、<xref:System.Windows.Controls.Primitives.Popup>自体を各画面の端に揃えます。  たとえば、あると想定、<xref:System.Windows.Controls.Primitives.Popup>が<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>'éý'<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>と<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>を 100 に設定します。  画面の下端の全部または一部を非表示にする場合、 <xref:System.Windows.Controls.Primitives.Popup>、<xref:System.Windows.Controls.Primitives.Popup>自体を再配置、画面とターゲットの基準とポップアップの間の垂直距離の下端に沿って配置ポイントが 100 よりも小さいです。 これを次の図で示します。  
  
 ![画面の端に配置されるポップアップ](../../../../docs/framework/wpf/controls/media/popupplacementrelativescreenedge.png "PopupPlacementRelativeScreenEdge")  
ポップアップが画面の端に揃えて配置されます  
  
### <a name="changing-the-popup-alignment-point"></a>ポップアップ配置ポイントの変更  
 場合<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>、 <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>、または<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>、ポップアップ配置ポイント下または右の画面の端を検出すると、ポップアップ画面を変更します。  
  
 画面の下端の全部または一部を非表示にするとすると、次の図は、プログラムことを示します、 <xref:System.Windows.Controls.Primitives.Popup>、ポップアップ配置ポイントの左下隅は、<xref:System.Windows.Controls.Primitives.Popup>です。  
  
 ![画面の下端による新しい配置ポイント](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointscreenedge.png "PopupPlacementRelativePointScreenEdge")  
ポップアップが画面の下端と重なり、ポップアップ配置ポイントが変更されます  
  
 次の図に示す時に、<xref:System.Windows.Controls.Primitives.Popup>を非表示にポップアップ配置ポイントの右上隅にあるの画面の右端で、<xref:System.Windows.Controls.Primitives.Popup>です。  
  
 ![画面の端による新しいポップアップ配置ポイント](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointrightscreenedge.png "PopupPlacementRelativePointRightScreenEdge")  
ポップアップが画面の右端と重なり、ポップアップ配置ポイントが変更されます  
  
 場合、<xref:System.Windows.Controls.Primitives.Popup>下と右の画面の端を検出したポップアップ配置ポイントの右下隅は、<xref:System.Windows.Controls.Primitives.Popup>です。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>ターゲットの始点とポップアップ配置ポイントの変更  
 ときに<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>、 <xref:System.Windows.Controls.Primitives.PlacementMode.Left>、 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、 <xref:System.Windows.Controls.Primitives.PlacementMode.Right>、または<xref:System.Windows.Controls.Primitives.PlacementMode.Top>、特定の画面の端が発生した場合、ターゲットの基準とポップアップ配置ポイント変更します。  画面の端を変更する位置の原因となるによって異なります、<xref:System.Windows.Controls.Primitives.PlacementMode>値。  
  
 次の図に示す時に<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>と<xref:System.Windows.Controls.Primitives.Popup>下部にある画面の端を検出したターゲットの基準は、対象領域の左上隅、ポップアップ配置ポイントの左下隅、<xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![画面の下端による新しい配置ポイント](../../../../docs/framework/wpf/controls/media/popupplacementbottomscreenedge.png "PopupPlacementBottomScreenEdge")  
Placement が Bottom で、ポップアップが画面の下端と重なりました  
  
 次の図に示す時に<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Left>と<xref:System.Windows.Controls.Primitives.Popup>画面の左端を検出したターゲットの基準は対象となる領域の右上隅にある、ポップアップ配置ポイント、の左上隅にあります<xref:System.Windows.Controls.Primitives.Popup>。  
  
 ![画面の左端による新しい配置ポイント](../../../../docs/framework/wpf/controls/media/popupplacementleftscreenedge.png "PopupPlacementLeftScreenEdge")  
Placement が Left で、ポップアップが画面の左端と重なりました  
  
 次の図に示す時に<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Right>と<xref:System.Windows.Controls.Primitives.Popup>画面の右端を検出したターゲットの基準は、対象領域の左上隅、ポップアップ配置ポイントの右上隅にある、<xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![画面の右端による新しい配置ポイント](../../../../docs/framework/wpf/controls/media/popupplacementrightscreenedge.png "PopupPlacementRightScreenEdge")  
Placement が Right で、ポップアップが画面の右端と重なりました  
  
 次の図に示す時に<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Top>と<xref:System.Windows.Controls.Primitives.Popup>画面の上端を検出したターゲットの基準は、対象領域の左下隅、ポップアップ配置ポイントの左上隅にある、<xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![画面の上端による新しい配置ポイント](../../../../docs/framework/wpf/controls/media/popupplacementtopscreenedge.png "PopupPlacementTopScreenEdge")  
Placement が Top で、ポップアップが画面の上端と重なりました  
  
 次の図に示す時に<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>は<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>と<xref:System.Windows.Controls.Primitives.Popup>下部にある画面の端を検出したターゲットの基準は、対象領域 (マウス ポインターの境界内) とポップアップの配置の左上隅にあります。ポイントの左下隅は、<xref:System.Windows.Controls.Primitives.Popup>です。  
  
 ![画面の端に近いマウスによる新しい配置ポイント](../../../../docs/framework/wpf/controls/media/popupplacementmousescreenedge.png "PopupPlacementMouseScreenEdge")  
Placement が Mouse で、ポップアップが画面の下端と重なりました  
  
### <a name="customizing-popup-placement"></a>ポップアップの配置のカスタマイズ  
 ターゲットの基準とポップアップ配置ポイントをカスタマイズするには、設定、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>です。 定義し、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>のような配置ポイントとの優先順位) の「プライマリ軸のセット返すデリゲート、<xref:System.Windows.Controls.Primitives.Popup>です。 最大の部分を表示するポイント、<xref:System.Windows.Controls.Primitives.Popup>が選択されています。  位置、<xref:System.Windows.Controls.Primitives.Popup>場合は自動的に調整、<xref:System.Windows.Controls.Primitives.Popup>画面の端で非表示になります。 例については、「[方法 : ポップアップのカスタム位置を指定する](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [ポップアップの配置のサンプル](http://go.microsoft.com/fwlink/?LinkID=160032)
