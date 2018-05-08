---
title: WindowsFormsHost 要素のレイアウトに関する考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
ms.openlocfilehash: 786e3adae6c5b8167fbba00aa140d4d728308dc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>WindowsFormsHost 要素のレイアウトに関する考慮事項
このトピックの内容について説明しますが、どのように<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の対話、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト システムです。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] および[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]フォームまたはページ上の要素を配置してサイズ変更の異なる、ただしと同様に、ロジックをサポートします。 ハイブリッド ユーザー インターフェイス (UI) を作成する場合をホストする[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素には、2 つのレイアウト スキームが統合されています。  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>WPF と Windows フォームのレイアウトでの違い  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 解像度に依存しないレイアウトを使用します。 すべて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト寸法を指定する*デバイス非依存ピクセル*です。 デバイス非依存ピクセルは 72 dpi モニターまたは 19,200 dpi プリンターにレンダリングするかどうかに関係なく同様の結果を取得するためのサイズと解像度に依存せず、インチの 1 つの 90-6 番目です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] またに基づいて*動的レイアウト*です。 これは、UI 要素自体の整列をフォームまたはその内容、その親レイアウト コンテナー、および使用可能な画面サイズに応じてページのことを意味します。 動的レイアウトでは、自動的に調整することで UI 要素の位置とサイズが含まれている文字列の長さを変更するローカライズが容易になります。  
  
 レイアウトで[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]がデバイスに依存し、静的である可能性が高くなります。 通常、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ハードウェアのピクセル単位で指定されたディメンションを使用してフォームにコントロールを絶対的に配置されます。 ただし、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の次の表に示すように、いくつかの動的なレイアウト機能をサポートしています。  
  
|レイアウト機能|説明|  
|--------------------|-----------------|  
|サイズの自動変更|いくつか[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]自体の内容を正しく表示するコントロールのサイズを変更します。 詳細については、次を参照してください。 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)です。|  
|固定およびドッキング|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、配置と親コンテナーに基づくサイズ変更をサポートします。 詳細については、<xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> および <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType> を参照してください。|  
|自動スケーリング|自身とその子を出力デバイス、または (ピクセル単位) の既定のコンテナーのフォント、サイズの解像度に基づくコンテナー コントロールのサイズを変更します。 詳細については、次を参照してください。 [Windows フォームにおける自動スケーリング](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)です。|  
|レイアウト コンテナー|<xref:System.Windows.Forms.FlowLayoutPanel>と<xref:System.Windows.Forms.TableLayoutPanel>コントロールがその子コントロールを配置し、その内容に従って自体のサイズします。|  
  
## <a name="layout-limitations"></a>レイアウトの制限事項  
 一般に、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを拡張し、可能な範囲に変換されることはできません[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 次の一覧が既知の制限事項について説明しますと、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が、そのホストされている統合しようとしています。[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]にコントロールを、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト システムです。  
  
-   場合によっては、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールのサイズを変更することはできません、または特定のディメンションにのみサイズを変更できます。 たとえば、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox>コントロールにのみ、1 つの高さ、コントロールのフォント サイズで定義されているがサポートしています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]場所要素ストレッチできます垂直方向に、ホストされる動的レイアウト<xref:System.Windows.Forms.ComboBox>期待どおりに、コントロールは伸縮しません。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、回転または傾斜ことはできません。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を発生させる、<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>イベント傾斜または回転変換を適用する場合。 処理しない場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>イベント、<xref:System.InvalidOperationException>が発生します。  
  
-   ほとんどの場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは比例拡大/縮小をサポートしていません。 コントロール全体のサイズをスケールが子コントロールおよびコントロールのコンポーネント要素可能性がありますいないサイズを変更する期待どおりにします。 この制限はどの程度それぞれ異なります[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがスケーリングをサポートします。 さらに、拡張することはできません[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは、0 ピクセルのサイズまでです。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、自動スケーリング、フォームは自身とそのコントロールのフォント サイズに基づいて自動的に変更をサポートします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]個々 の要素が動的に変更が、フォント サイズを変更するユーザー インターフェイスは全体のレイアウトのサイズを変更できません。  
  
### <a name="z-order"></a>Z オーダー  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ユーザー インターフェイス コントロールの動作の重複する要素の z オーダーを変更することができます。 ホストされた[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の上に常に描画されるように、別の HWND にコントロールが描画される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素。  
  
 ホストされた[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがいずれかの上に描画されるも<xref:System.Windows.Documents.Adorner>要素。  
  
## <a name="layout-behavior"></a>レイアウトの動作  
 ホストしているときに、次のセクションがレイアウトの動作の特定の側面を記述[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>スケーリング、単位変換、およびデバイスに依存しません。  
 たびに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素などの操作を実行する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]次元、2 つの座標系が関係している: のデバイスに依存しないピクセル[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のハードウェア ピクセル[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]です。 したがって、正しい単位変換と変換をスケーリングさせるための一貫したレイアウトを適用する必要があります。  
  
 座標系の間で変換は、現在のデバイスの解像度と任意のレイアウトによって異なります。 または、に適用される変換の表示、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素またはその先祖にします。  
  
 出力デバイスが 96 dpi とスケーリングに適用されていないかどうか、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素、1 つのデバイスに依存しないピクセルは 1 つのハードウェア ピクセルに等しい。  
  
 その他のすべてのケースでは、座標系のスケーリングが必要です。 ホストされるコントロールのサイズは変更されません。 代わりに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、ホストされるコントロールおよびすべての子コントロールを拡張しようとしています。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]スケーリングをサポートしていません、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の特定のコントロールでサポートされる度にスケールを設定します。  
  
 上書き、<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A>ホストされる Windows フォーム コントロールのカスタムのスケーリングの動作を提供するメソッド。  
  
 スケールのほか、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、次の表に示すように丸め処理やオーバーフローの場合を処理します。  
  
|変換の問題|説明|  
|----------------------|-----------------|  
|丸め|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] デバイスに依存しないピクセル数は、として指定`double`、および[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ハードウェア ピクセル数は、として指定`int`です。 場合、 `double`-寸法に変換されます`int`-ディメンションのベース、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が 0.5 未満の小数部の値に切り上げられます 0 ように標準の丸めを使用します。|  
|オーバーフロー|ときに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>から要素を変換`double`値を`int`値、オーバーフローが可能です。 も大きい値は<xref:System.Int32.MaxValue>に設定されている<xref:System.Int32.MaxValue>です。|  
  
### <a name="layout-related-properties"></a>レイアウトに関連するプロパティ  
 レイアウトの動作を制御するプロパティを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素が、適切にマップされている、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。 詳細については、次を参照してください。 [Windows フォームと WPF プロパティ マッピング](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)です。  
  
### <a name="layout-changes-in-the-hosted-control"></a>ホストされるコントロールのレイアウトの変更  
 ホストのレイアウトの変更[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールに反映されます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をレイアウトの更新をトリガーします。 <xref:System.Windows.UIElement.InvalidateMeasure%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストされるコントロールのレイアウトの変更が発生することにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト エンジンを実行します。  
  
### <a name="continuously-sized-windows-forms-controls"></a>Windows フォーム コントロールを継続的にサイズ設定  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 継続的なスケーリングを完全にサポートするコントロールとの対話、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト システムです。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を使用して、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>と<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドのサイズし、ホスト型配置を通常どおり[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
### <a name="sizing-algorithm"></a>サイズ調整アルゴリズム  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、次の手順を使用してホストされるコントロールのサイズを変更します。  
  
1.  <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素よりも優先、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>と<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドです。  
  
2.  ホストされるコントロールのサイズを決定する、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッドを呼び出すホストされるコントロールの<xref:System.Windows.Forms.Control.GetPreferredSize%2A>制約を持つメソッドに渡される制約から変換されます、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッドです。  
  
3.  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドは、指定されたサイズの制約にホストされるコントロールを設定しようとしています。  
  
4.  場合、ホストされるコントロールの<xref:System.Windows.Forms.Control.Size%2A>プロパティが指定された制約と一致する、ホストされるコントロールのサイズは、制約します。  
  
 場合、<xref:System.Windows.Forms.Control.Size%2A>プロパティが指定された制約と一致しません、ホストされるコントロールが継続的なサイズ変更をサポートしていません。 たとえば、<xref:System.Windows.Forms.MonthCalendar>コントロールは、不連続サイズのみを使用します。 このコントロールで許可されるサイズは、幅と高さの両方の整数 (月の数を表す) で構成されます。 など、この場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は次のように動作します。  
  
-   場合、<xref:System.Windows.Forms.Control.Size%2A>プロパティを返します、サイズ、指定された制約より大きく、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、ホストされるコントロールをクリップします。 高さと幅を個別に処理されます、ため、どちらの方向にホストされるコントロールをクリップすることがあります。  
  
-   場合、<xref:System.Windows.Forms.Control.Size%2A>プロパティ、指定された制約よりも小さいサイズを返します<xref:System.Windows.Forms.Integration.WindowsFormsHost>このサイズの値を受け取り、値を返します、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト システムです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [チュートリアル: WPF での Windows フォーム コントロールの配置](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)  
 [WPF のサンプルでのフォーム コントロールのウィンドウの配置](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
