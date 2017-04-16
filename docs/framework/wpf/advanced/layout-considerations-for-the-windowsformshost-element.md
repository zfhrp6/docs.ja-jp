---
title: "WindowsFormsHost 要素のレイアウトに関する考慮事項 | Microsoft Docs"
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
  - "デバイスに依存しないピクセル"
  - "動的レイアウト [WPF 相互運用性]"
  - "相互運用性 [WPF], Windows フォーム"
  - "Windows フォーム [WPF], 相互運用性"
  - "Windows フォーム, WPF 相互運用"
  - "WindowsFormsHost 要素のレイアウトに関する考慮事項"
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# WindowsFormsHost 要素のレイアウトに関する考慮事項
ここでは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素と [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウト システムの対話方法を説明します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] および [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]は、フォームまたはページでの要素のサイズ設定や配置について、違いはあっても似ているロジックをサポートします。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールをホストするハイブリッド ユーザー インターフェイス \(UI\) を作成する場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素により 2 つのレイアウト スキームが統合されます。  
  
## WPF と Windows のフォームのレイアウトの違い  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、解像度に依存しないレイアウトを使用します。  すべての [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウトのサイズは、デバイス非依存ピクセルを使用して指定されます。  デバイス非依存ピクセルのサイズは 1\/96 インチで、解像度に依存しないため、出力先が 72 dpi モニターであっても 19,200 dpi プリンターであっても、同様の結果を得ることができます。  
  
 また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は*動的レイアウト*に基づきます。  つまり、UI 要素は、そのコンテンツ、親レイアウト コンテナー、および使用できる画面サイズに合わせて自身をフォームまたはページ上に配置します。  動的レイアウトは、ローカリゼーションを容易にするために、UI 要素に含まれる文字列の長さが変わると、その要素のサイズと位置を自動的に調整します。  
  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のレイアウトはデバイスに依存し、多くの場合、静的です。  通常、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは、ハードウェア ピクセルで指定されたサイズを使用してフォーム上の絶対的な位置に配置されます。  ただし、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]は動的レイアウト機能もいくつかサポートします。これらのレイアウト機能について、次の表で簡単に説明します。  
  
|レイアウト機能|説明|  
|-------------|--------|  
|自動サイズ変更|一部の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは、コンテンツが正しく表示されるように自身のサイズを変更します。  詳細については、「[AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)」を参照してください。|  
|アンカーとドッキング|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは、親コンテナーに基づく配置とサイズ設定をサポートします。  詳細については、「<xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=fullName>」および「<xref:System.Windows.Forms.Control.Dock%2A?displayProperty=fullName>」を参照してください。|  
|自動スケーリング|コンテナー コントロールは、出力デバイスの解像度、または既定のコンテナー フォントのサイズ \(ピクセル単位\) に基づいて自身とその子のサイズを変更します。  詳細については、「[Windows フォームにおける自動スケーリング](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)」を参照してください。|  
|レイアウト コンテナー|<xref:System.Windows.Forms.FlowLayoutPanel> コントロールと <xref:System.Windows.Forms.TableLayoutPanel> コントロールはその子コンテンツを配置し、そのコンテンツに合わせて自身のサイズを設定します。|  
  
## レイアウトの制限  
 一般的に、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で可能な程度までスケーリングおよび変換することはできません。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素がホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のレイアウト システムに統合する際の既知の制限を次のリストに示します。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、サイズを変更できなかったり、特定のサイズにしか設定できない場合があります。  たとえば、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> コントロールは、コントロールのフォント サイズで定義されている 1 つの高さしかサポートしていません。  要素を垂直方向に伸縮できる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の動的レイアウトでも、ホストされている <xref:System.Windows.Forms.ComboBox> コントロールは同様に伸縮することはできません。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは回転または斜めにすることはできません。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、傾斜または回転変換が適用されると、<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> イベントを発生させます。  この <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> イベントを処理しないと、<xref:System.InvalidOperationException> が発生します。  
  
-   ほとんどの場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、比率を保持したまま拡大縮小することはできません。  コントロール全体のサイズは拡大縮小されますが、コントロールの子コントロールやコンポーネント要素のサイズは希望どおりに変更できません。  この制限は、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] の各コントロールで拡大縮小をどの程度サポートしているかに依存します。  また、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを 0 ピクセルのサイズまで縮小することはできません。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは自動スケーリングをサポートし、フォームは自身とそのコントロールのサイズをフォントのサイズに基づいて自動的に変更します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ユーザー インターフェイスでは、フォント サイズを変更しても、レイアウト全体のサイズは変わりません。ただし、個々の要素は動的にサイズを変更できます。  
  
### z オーダー  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ユーザー インターフェイスでは、要素の z オーダーを変更して重複を制御できます。  ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは別の HWND で描画されるため、常に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素の一番上に描画されます。  
  
 また、ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは <xref:System.Windows.Documents.Adorner> 要素の上に描画されます。  
  
## レイアウトの動作  
 次のセクションでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールをホストしているときのレイアウト動作の固有の側面について説明します。  
  
### スケーリング、単位変換、およびデバイス非依存  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素が [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] や [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のサイズに関連する操作を実行する場合には、常に 2 つの座標系が関連します。この 2 つの座標系は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] についてはデバイス非依存ピクセル、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]についてはハードウェア ピクセルです。  したがって、一貫性のあるレイアウトを実現するためには、正しい単位変換とスケーリング変換を適用する必要があります。  
  
 座標系間の変換は、現在のデバイスの解像度、および <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素やその先祖に適用されたレイアウトまたはレンダリングの変換に基づいて行われます。  
  
 出力デバイスが 96 dpi で、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素にスケーリングが適用されていない場合、1 デバイス非依存ピクセルは 1 ハードウェア ピクセルと等しくなります。  
  
 他のすべての場合には、座標系のスケーリングが必要です。  ホストされているコントロールのサイズは変更されません。  代わりに、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、ホストされているコントロールと、そのすべての子コントロールをスケーリングしようとします。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]はスケーリングを完全にはサポートしないため、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、特定のコントロールがサポートする水準までスケーリングされます。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> メソッドをオーバーライドして、ホスト対象の [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] コントロールにカスタムのスケーリング動作を提供します。  
  
 スケーリングに加えて、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、次の表で説明するように丸めおよびオーバーフローを処理します。  
  
|変換の問題|説明|  
|-----------|--------|  
|丸め|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のデバイス非依存ピクセルのサイズは `double` として指定され、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] のハードウェア ピクセルのサイズは `int` として指定されます。  `double` に基づくサイズが `int` に基づくサイズに変換される場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は標準の丸めを使用して、0.5 未満の小数値を 0 に切り下げます。|  
|オーバーフロー|<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素が、`double` 値から `int` 値に変換されると、オーバーフローが発生する可能性があります。  <xref:System.Int32.MaxValue> よりも大きい値は、<xref:System.Int32.MaxValue> に設定されます。|  
  
### レイアウト関連のプロパティ  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールと [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素のレイアウト関連の動作を制御するプロパティは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素によって正しくマップされます。  詳細については、「[Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)」を参照してください。  
  
### ホストされているコントロールのレイアウトの変更  
 ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールのレイアウトの変更は [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に伝達されて、レイアウトの更新をトリガーします。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> の <xref:System.Windows.UIElement.InvalidateMeasure%2A> メソッドにより、ホストされているコントロールでレイアウトが変更されると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウト エンジンが実行されます。  
  
### 連続的にサイズ設定される Windows フォーム コントロール  
 連続的なスケーリングをサポートする [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウト システムと全面的に対話します。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、通常どおり <xref:System.Windows.FrameworkElement.MeasureOverride%2A> メソッドと <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> メソッドを使用して、ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールのサイズを設定し、配置します。  
  
### サイズ設定アルゴリズム  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、次の手順を使用して、ホストされているコントロールのサイズを設定します。  
  
1.  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、<xref:System.Windows.FrameworkElement.MeasureOverride%2A> メソッドと <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> メソッドをオーバーライドします。  
  
2.  ホストされているコントロールのサイズを決定するために、<xref:System.Windows.FrameworkElement.MeasureOverride%2A> メソッドは、<xref:System.Windows.FrameworkElement.MeasureOverride%2A> メソッドに渡された制約から変換された制約を使用して、ホストされているコントロールの <xref:System.Windows.Forms.Control.GetPreferredSize%2A> メソッドを呼び出します。  
  
3.  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> メソッドは、ホストされているコントロールを指定されたサイズ制約に設定しようとします。  
  
4.  ホストされているコントロールの <xref:System.Windows.Forms.Control.Size%2A> プロパティが指定された制約に一致すると、ホストされたコントロールのサイズは、その制約に合わせて設定されます。  
  
 指定された制約に <xref:System.Windows.Forms.Control.Size%2A> プロパティが一致しない場合、ホストされているコントロールは連続的なサイズ設定をサポートしません。  たとえば、<xref:System.Windows.Forms.MonthCalendar> コントロールは不連続のサイズのみを許可します。  このコントロールで許可されるサイズは、高さと幅の両方について整数 \(月数を表す\) で構成されます。  このような場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は次のように動作します。  
  
-   指定された制約よりも大きいサイズを <xref:System.Windows.Forms.Control.Size%2A> プロパティが返す場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素はホストされているコントロールをクリップします。  高さと幅は別個に処理されるため、ホストされているコントロールはいずれの方向にもクリップされる可能性があります。  
  
-   指定された制約よりも小さいサイズを <xref:System.Windows.Forms.Control.Size%2A> プロパティが返す場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost> はこのサイズ値を受け入れて、その値を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウト システムに返します。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [チュートリアル: WPF での Windows フォーム コントロールの配置](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)   
 [WPF 個の Windows フォームのコントロールの階層化](http://go.microsoft.com/fwlink/?LinkID=159971)   
 [Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)   
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)