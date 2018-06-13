---
title: コントロールのフォーカスのスタイルと FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 6c73c8bbfcf7631094ddf89641de9af38f86f88e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549517"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>コントロールのフォーカスのスタイルと FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] キーボード フォーカスを受け取るときに、コントロールの外観を変更するための 2 つの並列メカニズムを提供します。 最初のメカニズムがなどを使用してプロパティの setter のプロパティは<xref:System.Windows.UIElement.IsKeyboardFocused%2A>スタイルまたはコントロールに適用されているテンプレート内で。 2 番目の機構の値として別のスタイルを提供する、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>プロパティです"visual スタイルにフォーカスする"または他の UI コントロールのビジュアル ツリーを変更するのではなく、コントロールの上に描画される装飾用の別個のビジュアル ツリーの作成。置換する要素。 このトピックでは、これらのメカニズムが適切であるシナリオについて説明します。  
   
  
<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>フォーカスの Visual スタイルの目的は、  
 フォーカス visual スタイル機能では、任意の UI 要素にキーボード ナビゲーションに基づいてビジュアル ユーザー フィードバックを導入するため、一般的な「オブジェクト モデル」を提供します。 新しいテンプレートをコントロールに適用するか、特定のテンプレート構成を知ることがなく可能です。  
  
 ただし、正確に機能するため、フォーカス visual スタイル コントロール テンプレートを知らなくても、フォーカスの visual スタイルを使用してコントロールの表示可能な視覚的なフィードバックは必ずしも制限されます。 機能が実際に行うには、コントロールの描画のテンプレートを使用して作成されると、ビジュアル ツリーの上に別のビジュアル ツリー (装飾) をオーバーレイをします。 格納するスタイルを使用してこの別個のビジュアル ツリーを定義する、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>プロパティです。  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>フォーカス Visual スタイルの既定の動作  
 フォーカスの visual スタイルは、キーボードによってフォーカス操作が開始されたときにのみ機能します。 任意のマウス操作またはプログラムでフォーカスの変更は、visual スタイルのフォーカス モードを無効にします。 フォーカス モードの違いの詳細については、次を参照してください。[フォーカス概要](../../../../docs/framework/wpf/advanced/focus-overview.md)です。  
  
 コントロールのテーマには、すべてのコントロールのテーマでのフォーカス visual スタイルになる既定フォーカス visual スタイルの動作が含まれます。 このテーマ スタイルは、静的なキーの値によって識別される<xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>です。 アプリケーション レベルで、独自のフォーカス visual スタイルを宣言する場合は、テーマからこの既定のスタイルの動作を置き換えます。 また、全体のテーマを定義する場合、全体のテーマの既定の動作の線のスタイルを定義するこれと同じキーを使用する必要があります。  
  
 テーマで既定フォーカス visual スタイルは一般に非常に単純です。 おおよその近似値を次に示します。  
  
```  
<Style x:Key="{x:Static SystemParameters.FocusVisualStyleKey}">  
  <Setter Property="Control.Template">  
    <Setter.Value>  
      <ControlTemplate>  
        <Rectangle StrokeThickness="1"  
          Stroke="Black"  
          StrokeDashArray="1 2"  
          SnapsToDevicePixels="true"/>  
      </ControlTemplate>  
    </Setter.Value>  
  </Setter>  
</Style>  
```  
  
<a name="When"></a>   
## <a name="when-to-use-focus-visual-styles"></a>フォーカスの Visual スタイルを使用する場合  
 概念的には、コントロールに適用されるフォーカス visual スタイルの外観は、コントロール間で一貫している必要があります。 一貫性を実現する方法の 1 つは、テーマで定義されている各コントロールを取得、まったく同じフォーカス visual スタイル、またはスタイルのいくつかのバリエーションのいずれかを全体のテーマを作成している場合にのみ、visual スタイルが関連する視覚的にフォーカスをコントロールから続きを変更するにはロール。 代わりに、ページまたは、UI にキーボード フォーカスのすべての要素のスタイルを設定する同じスタイル (または類似スタイル) を使用する場合があります。  
  
 設定<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>テーマの一部ではない個別のコントロールのスタイルでは、フォーカスの使用目的ではない visual スタイル。 これは、コントロール間の一貫性のない visual 動作がキーボード フォーカスに関するユーザー エクスペリエンスに混乱する可能性があるためです。 されない意図的に一貫性のあるテーマで、キーボード フォーカス コントロール固有の動作する場合は、はるかに優れた方法を使用してトリガーのスタイルでの個々 の入力状態プロパティなど<xref:System.Windows.UIElement.IsFocused%2A>または<xref:System.Windows.UIElement.IsKeyboardFocused%2A>です。  
  
 フォーカスはキーボード フォーカスの専用の visual スタイルが機能します。 そのため、フォーカスの visual スタイルは、ユーザー補助機能の種類です。 場合 UI の変更の種類、フォーカスのマウスを使用しているかどうか、キーボード、またはプログラムでは、次をフォーカスの visual スタイルを使用しないでくださいして代わりに、set アクセス操作子およびスタイルまたはテンプレートの一般的なフォーカス プロパティの値から作業をトリガーに使用する必要があります。ように`IsFocused`または`IsFocusWithin`です。  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>フォーカスの Visual スタイルを作成する方法  
 フォーカスの visual スタイルがある用に作成する、スタイル、<xref:System.Windows.Style.TargetType%2A>の<xref:System.Windows.Controls.Control>します。 スタイルは、主に、<xref:System.Windows.Controls.ControlTemplate>です。 フォーカスの visual スタイルに割り当てられた型にする対象の型を指定しない、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>です。  
  
 対象の型は常にため<xref:System.Windows.Controls.Control>、すべてのコントロールに共通するプロパティを使用してスタイルを設定する必要があります (のプロパティを使用して、<xref:System.Windows.Controls.Control>クラスとその基本クラス)。 UI 要素にオーバーレイとして正しく機能するコントロールの機能領域を隠さない、テンプレートを作成する必要があります。 一般に、視覚的なフィードバック表示されるコントロールの余白の外部またはコントロールのヒット テストがブロックされていない一時または控えめな効果とフォーカス visual スタイルが適用されるつまり。 テンプレート バインディングで使用できるサイズ変更と、オーバーレイ テンプレートの配置を決定するための便利なプロパティが含まれます<xref:System.Windows.FrameworkElement.ActualHeight%2A>、 <xref:System.Windows.FrameworkElement.ActualWidth%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、および<xref:System.Windows.Controls.Control.Padding%2A>です。  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>フォーカスの Visual スタイルを使用に代わる方法  
 フォーカスの visual スタイルを使用してが適切ではありません、1 つのコントロールをスタイル処理のみか、またはコントロール テンプレートをより細かく制御するための場合があるその他の多くのアクセス可能なプロパティやビジュアルを作成できる手法フォーカスの変更に応答で動作します。  
  
 トリガー、setter、およびイベント セッターがすべてで詳しく説明されている[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)です。 ルーティングされたイベントの処理は、後ほど[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)です。  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 キーボード フォーカス、特に関心がある場合、<xref:System.Windows.UIElement.IsKeyboardFocused%2A>プロパティに対して依存関係プロパティを使用できる<xref:System.Windows.Trigger>です。 スタイルまたはテンプレートのプロパティ トリガーは非常に具体的には、1 つのコントロールとその他のコントロールのキーボード フォーカスの動作に一致する可能性がありますいない視覚的には、キーボード フォーカスの動作を定義するためのより適切な手法です。  
  
 別のような依存関係プロパティが<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>、合成内またはコントロールの機能領域内で任意の場所は、キーボード フォーカスを視覚的に呼び出すために必要な場合に使用する適切なされる可能性があります。 たとえば、配置する場合があります、<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>トリガー キーボード フォーカスがより正確にでも複数のコントロールをグループ化するパネルを異なる方法で表示されるようにあるそのパネル内の各要素にします。  
  
 イベントを使用することもできます。<xref:System.Windows.UIElement.GotKeyboardFocus>と<xref:System.Windows.UIElement.LostKeyboardFocus>(およびプレビュー同等)。 これらのイベントを使用するには、基礎として、 <xref:System.Windows.EventSetter>、または分離コードでイベントのハンドラーを記述することができます。  
  
### <a name="other-focus-properties"></a>その他のフォーカス プロパティ  
 Setter を基本または上をトリガーする必要がありますフォーカスを変更するすべての考えられる原因を視覚的な動作を生成する場合は、<xref:System.Windows.UIElement.IsFocused%2A>依存関係プロパティをまたはに、<xref:System.Windows.UIElement.GotFocus>または<xref:System.Windows.UIElement.LostFocus>に使用されるイベント、<xref:System.Windows.EventSetter>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [フォーカスの概要](../../../../docs/framework/wpf/advanced/focus-overview.md)  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)
