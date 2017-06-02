---
title: "ハイブリッド アプリケーションのトラブルシューティング | Microsoft Docs"
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
  - "ハイブリッド アプリケーション [WPF 相互運用性]"
  - "相互運用性 [WPF], Windows フォーム"
  - "メッセージ ループ [WPF]"
  - "重複するコントロール"
  - "Windows フォーム [WPF], 相互運用性"
  - "Windows フォーム, WPF 相互運用"
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# ハイブリッド アプリケーションのトラブルシューティング
<a name="introduction"></a> ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の両方のテクノロジを使用するハイブリッド アプリケーションを作成するときに発生する可能性のある一般的な問題について説明します。  
  
   
  
<a name="overlapping_controls"></a>   
## コントロールの重複  
 コントロールが意図したように重ならない場合があります。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] は、コントロールごとに異なる HWND を使用します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、ページ上のすべてのコンテンツに 1 つの HWND を使用します。  このような実装の違いにより、意図したものとは異なる重なり方になります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、常に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの一番上に表示されます。  
  
 <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされている [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、<xref:System.Windows.Forms.Integration.ElementHost> コントロールの z オーダーで表示されます。  <xref:System.Windows.Forms.Integration.ElementHost> コントロールを重ねることはできますが、ホストされている [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは相互に結合または対話しません。  
  
<a name="child_property"></a>   
## 子プロパティ  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> クラスおよび <xref:System.Windows.Forms.Integration.ElementHost> クラスがホストできる子コントロールまたは要素は 1 つだけです。  複数のコントロールまたは要素をホストするには、子コンテンツとしてコンテナーを使用する必要があります。  たとえば、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のボタン コントロールとチェック ボックス コントロールを <xref:System.Windows.Forms.Panel?displayProperty=fullName> コントロールに追加し、パネルを <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールの <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> プロパティに割り当てることはできます。  しかし、ボタン コントロールとチェック ボックス コントロールを個別に同じ <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールに追加することはできません。  
  
<a name="scaling"></a>   
## スケーリング  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]では、スケーリング モデルが異なります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のスケーリング変換には、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールに対して意味のあるものと意味のないものがあります。  たとえば、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールの 0 へのスケーリングは機能しますが、同じコントロールを 0 以外の値にスケーリングして戻そうとしても、コントロールのサイズは 0 のままです。  詳細については、「[WindowsFormsHost 要素のレイアウトに関する考慮事項](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)」を参照してください。  
  
<a name="adapter"></a>   
## アダプター  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> クラスと <xref:System.Windows.Forms.Integration.ElementHost> クラスには非表示のコンテナーが含まれるため、これらを使用する際には混乱が生じる場合があります。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> クラスと <xref:System.Windows.Forms.Integration.ElementHost> クラスはどちらもアダプターと呼ばれる非表示のコンテナーを持っており、コンテンツをホストするために使用します。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の場合、アダプターは <xref:System.Windows.Forms.ContainerControl?displayProperty=fullName> クラスから派生します。  <xref:System.Windows.Forms.Integration.ElementHost> コントロールの場合、アダプターは <xref:System.Windows.Controls.DockPanel> 要素から派生します。  このコンテナーについては、相互運用性に関する他のトピックでアダプターに関する説明を参照してください。  
  
<a name="nesting"></a>   
## 入れ子  
 <xref:System.Windows.Forms.Integration.ElementHost> コントロールの内部への <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の入れ子は、サポートされていません。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の内部への <xref:System.Windows.Forms.Integration.ElementHost> コントロールの入れ子も、サポートされていません。  
  
<a name="focus"></a>   
## フォーカス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ではフォーカスの動作が異なり、ハイブリッド アプリケーションではフォーカスに関する問題が発生する可能性があります。  たとえば、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の内部にフォーカスがある場合、ページを最小化して元に戻すと、またはモーダル ダイアログ ボックスを表示すると、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の内部のフォーカスが失われる可能性があります。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素はまだフォーカスを保持していますが、内部のコントロールはフォーカスを失う場合があります。  
  
 データの検証も、フォーカスによって影響されます。  検証は <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の中では機能しますが、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素から外へ Tab キーで移動する場合や、2 つの異なる <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の間では、検証が機能しません。  
  
<a name="property_mapping"></a>   
## プロパティの割り当て  
 一部のプロパティの割り当てでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] テクノロジと [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] テクノロジの間の異なる実装をブリッジするために、広範な解釈が必要になります。  プロパティの割り当てを使用すると、フォント、色、およびその他のプロパティの変更にコードで対応できます。  一般に、プロパティの割り当ては、*Property*Changed イベントまたは On*Property*Changed 呼び出しをリッスンし、子コントロールまたはそのアダプターで適切なプロパティを設定することで機能します。  詳細については、「[Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)」を参照してください。  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## ホストされるコンテンツでのレイアウト関連のプロパティ  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=fullName> プロパティまたは <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=fullName> プロパティを割り当てると、ホストされるコンテンツで複数のレイアウト関連プロパティが自動的に設定されます。  これらのコンテンツ プロパティを変更すると、予期しないレイアウト動作が発生する場合があります。  
  
 ホストされるコンテンツは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> および親の <xref:System.Windows.Forms.Integration.ElementHost> を埋めるようにドッキングされます。  この動作を有効にするため、子プロパティを設定すると複数のプロパティが設定されます。  <xref:System.Windows.Forms.Integration.ElementHost> クラスおよび <xref:System.Windows.Forms.Integration.WindowsFormsHost> クラスによって設定されるコンテンツ プロパティを次の表に示します。  
  
|ホスト クラス|コンテンツ プロパティ|  
|-------------|-----------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 ホストされるコンテンツで、これらのプロパティを直接設定しないでください。  詳細については、「[WindowsFormsHost 要素のレイアウトに関する考慮事項](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)」を参照してください。  
  
<a name="navigation_applications"></a>   
## ナビゲーション アプリケーション  
 ナビゲーション アプリケーションが、ユーザーの状態を保持しない場合があります。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、ナビゲーション アプリケーションで使用されると、コントロールを再作成します。  ユーザーが <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素をホストするページから移動した後、そのページに戻ると、子コントロールの再作成が発生します。  ユーザーがそれまでに入力したコンテンツは失われます。  
  
<a name="message_loop_interoperation"></a>   
## メッセージ ループの相互運用  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のメッセージ ループを使用するとき、メッセージが意図したように処理されない場合があります。  <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> メソッドは <xref:System.Windows.Forms.Integration.WindowsFormsHost> コンストラクターによって呼び出されます。  このメソッドは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のメッセージ ループにメッセージ フィルターを追加します。  このフィルターは、<xref:System.Windows.Forms.Control?displayProperty=fullName> がメッセージの送信先であった場合は <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=fullName> メソッドを呼び出し、メッセージを変換およびディスパッチします。  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=fullName> で [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のメッセージ ループ内の <xref:System.Windows.Window> を表示した場合、<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> メソッドを呼び出さない限り、何も入力できません。  <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> メソッドは <xref:System.Windows.Window> を受け取り、キー関連のメッセージ再ルーティングする <xref:System.Windows.Forms.IMessageFilter?displayProperty=fullName> を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のメッセージ ループに追加します。  詳細については、「[Windows フォームと WPF の相互運用性入力アーキテクチャ](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)」を参照してください。  
  
<a name="opacity_and_layering"></a>   
## 不透明度とレイヤー表示  
 <xref:System.Windows.Interop.HwndHost> クラスは、レイヤー表示をサポートしません。  つまり、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素で <xref:System.Windows.UIElement.Opacity%2A> プロパティを設定しても何の効果もなく、<xref:System.Windows.Window.AllowsTransparency%2A> が `true` に設定されている他の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ウィンドウとのブレンド操作は行われません。  
  
<a name="dispose"></a>   
## Dispose  
 クラスを適切に破棄しないと、リソースがリークする可能性があります。  ハイブリッド アプリケーションでは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> クラスと <xref:System.Windows.Forms.Integration.ElementHost> クラスを確実に破棄してください。そうしないと、リソースがリークする可能性があります。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] は、モーダルではない親の <xref:System.Windows.Forms.Form> が閉じると、<xref:System.Windows.Forms.Integration.ElementHost> コントロールを破棄します。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、アプリケーションがシャットダウンすると <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を破棄します。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のメッセージ ループ内の <xref:System.Windows.Window> で <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を表示する場合があります。  この場合は、アプリケーションがシャットダウンしているという通知をコードが受け取らない可能性があります。  
  
<a name="enabling_visual_styles"></a>   
## visual スタイルの有効化  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールで [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] の視覚スタイルが有効にならない場合があります。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アプリケーションのテンプレートでは、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> メソッドが呼び出されます。  この方法は既定で名前はされず、プロジェクトを作成する場合は [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] を使用すると Comctl32.dll Version 6.0 が使用可能な場合は、[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] にコントロールの外観を取得します。処理がスレッドで作成する前に <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法を追加する必要があります。  詳細については、「[方法 : ハイブリッド アプリケーションで視覚スタイルを有効にする](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)」を参照してください。  
  
<a name="licensed_controls"></a>   
## ライセンスされたコントロール  
 メッセージ ボックスでライセンス情報を表示するライセンスされた [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、ハイブリッド アプリケーションでは予期しない動作を示す場合があります。  ライセンスされたコントロールの中には、ハンドルの作成に対してダイアログ ボックスを表示するものがあります。  たとえば、ライセンスされたコントロールは、ライセンスが必要なことや、コントロールの残りの試用ライセンスが 3 つであることなどを、ユーザーに通知する場合があります。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は <xref:System.Windows.Interop.HwndHost> クラスから派生し、子コントロールのハンドルは <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> メソッドの内部で作成されます。  <xref:System.Windows.Interop.HwndHost> クラスは <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> メソッドでのメッセージの処理を許可しませんが、ダイアログ ボックスを表示するとメッセージが送信されます。  このライセンス シナリオを有効にするには、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の子としてコントロールを割り当てる前に、コントロールで <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=fullName> メソッドを呼び出します。  
  
<a name="wpf_designer"></a>   
## WPF デザイナー  
 WPF コンテンツは、[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] を使用してデザインできます。  以下では、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]でハイブリッド アプリケーションを作成するときに発生する可能性のある一般的な問題について説明します。  
  
### デザイン時に無視される BackColorTransparent  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> プロパティは、デザイン時には意図したとおりに動作しない場合があります。  
  
 WPF コントロールが表示される親の上にない場合、WPF ランタイムは <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> の値を無視します。  <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> が無視されることがあるのは、<xref:System.Windows.Forms.Integration.ElementHost> オブジェクトが異なる <xref:System.AppDomain> 内に作成されるためです。  ただし、アプリケーションの実行時には、<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> は意図したとおりに動作します。  
  
### obj フォルダーが削除されると表示されるデザイン時エラー一覧  
 obj フォルダーが削除されると、デザイン時エラー一覧が表示されます。  
  
 <xref:System.Windows.Forms.Integration.ElementHost> を使用してデザインを行うとき、Windows フォーム デザイナーは、プロジェクトの obj フォルダー内の Debug フォルダーまたは Release フォルダーに生成されるファイルを使用します。  これらのファイルを削除すると、デザイン時エラー一覧が表示されます。  この問題を解決するには、プロジェクトをリビルドします。  詳細については、「[Windows フォーム デザイナーでのデザイン時エラー](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)」を参照してください。  
  
<a name="elementhost_and_ime"></a>   
## ElementHost と IME  
 <xref:System.Windows.Forms.Integration.ElementHost> でホストされる WPF コントロールは、現在、<xref:System.Windows.Forms.Control.ImeMode%2A> プロパティをサポートしていません。  <xref:System.Windows.Forms.Control.ImeMode%2A> を変更しても、ホストされているコントロールでは無視されます。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF デザイナーの相互運用性](http://msdn.microsoft.com/ja-jp/2cb7c1ca-2a75-463b-8801-fba81e2b7042)   
 [Windows フォームと WPF の相互運用性入力アーキテクチャ](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)   
 [方法 : ハイブリッド アプリケーションで視覚スタイルを有効にする](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)   
 [WindowsFormsHost 要素のレイアウトに関する考慮事項](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)   
 [Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)   
 [Windows フォーム デザイナーでのデザイン時エラー](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)   
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)