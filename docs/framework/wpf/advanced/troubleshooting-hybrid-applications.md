---
title: "ハイブリッド アプリケーションのトラブルシューティング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da0fed9a491c91881a9e0296e2c849d8430bb954
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-hybrid-applications"></a>ハイブリッド アプリケーションのトラブルシューティング
<a name="introduction"></a>このトピックは、両方を使用するハイブリッド アプリケーションを作成するときに発生する可能性がある一般的な問題を一覧表示[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]テクノロジです。  
  

  
<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>コントロールの重複  
 予想できるように、コントロールは重複できません可能性があります。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]各コントロールの個別の HWND を使用します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ上のすべてのコンテンツを 1 つの HWND を使用します。 この実装の相違では、予期しない重複した動作が原因です。  
  
 A[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールでホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の上に常に表示される、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストされているコンテンツ、<xref:System.Windows.Forms.Integration.ElementHost>の z オーダーでコントロールが表示されます、<xref:System.Windows.Forms.Integration.ElementHost>コントロール。 重複することは<xref:System.Windows.Forms.Integration.ElementHost>、コントロールが、ホストされている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツが結合または対話していません。  
  
<a name="child_property"></a>   
## <a name="child-property"></a>子プロパティ  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>クラスは、1 つの子コントロールまたは要素のみをホストできます。 1 つ以上のコントロールまたは要素をホストするには、子コンテンツとしてコンテナーを使用する必要があります。 たとえば、追加する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ボタンとチェック ボックス コントロールを<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>を制御して、パネルを割り当てる、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールの<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>プロパティです。 ただし、追加できません、ボタンとチェック ボックス コントロールとは別に同じ<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。  
  
<a name="scaling"></a>   
## <a name="scaling"></a>スケーリング  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]および[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]別のスケーリング モデルがあります。 いくつか[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]拡大縮小変換が有意義に[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが、他のユーザーはいません。 たとえば、スケーリング、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールを 0 に機能しますが、0 以外の値に同じコントロールのスケール設定しようとすると、コントロールのサイズは 0 のままです。 詳細については、次を参照してください。 [WindowsFormsHost 要素のレイアウトに関する考慮事項](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)です。  
  
<a name="adapter"></a>   
## <a name="adapter"></a>アダプター  
 使用する場合、混乱にすることがあります、<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>クラスを非表示コンテナーが含まれるためです。 両方の<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>クラスと呼ばれる非表示のコンテナーがある、*アダプター*コンテンツをホストするために使用します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>から派生した要素のアダプター、<xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>クラスです。 <xref:System.Windows.Forms.Integration.ElementHost>から派生したコントロールのアダプター、<xref:System.Windows.Controls.DockPanel>要素。 アダプターは、その他の相互運用のトピックへの参照が表示されたら、このコンテナーは、新機能について説明されています。  
  
<a name="nesting"></a>   
## <a name="nesting"></a>入れ子  
 入れ子、<xref:System.Windows.Forms.Integration.WindowsFormsHost>内の要素、<xref:System.Windows.Forms.Integration.ElementHost>コントロールはサポートされていません。 入れ子、<xref:System.Windows.Forms.Integration.ElementHost>内の制御、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素もサポートされていません。  
  
<a name="focus"></a>   
## <a name="focus"></a>フォーカス  
 フォーカスが異なる方法で動作[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]、ハイブリッド アプリケーションで発生する可能性の問題を集中ことを意味します。 内のフォーカスがある場合など、<xref:System.Windows.Forms.Integration.WindowsFormsHost>を最小限に抑えると、ページを復元またはモーダル ダイアログ ボックスを表示する、内部注意いずれかを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が失われる可能性があります。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素にはまだ、フォーカスがその内部コントロールがない場合があります。  
  
 データの検証は、フォーカスの影響を受けます。 検証の動作、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が機能しないのタブ、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素、または 2 つの異なる間<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>プロパティ マッピング  
 一部のプロパティ マッピングの間で複数の異なる実装をブリッジする広範な解釈が必要に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]テクノロジです。 プロパティ マッピングには、フォント、色、およびその他のプロパティの変更に対応するようにコードが有効にします。 一般に、プロパティのマッピングがリッスンするかによって機能*プロパティ*変更イベントまたは*プロパティ*呼び出し、および子コントロールまたはそのアダプターのいずれかの適切なプロパティの設定を変更します。 詳細については、次を参照してください。 [Windows フォームと WPF プロパティ マッピング](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)です。  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>ホストされているコンテンツのレイアウトに関連するプロパティ  
 ときに、<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType>または<xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType>プロパティが割り当てられている、いくつかのレイアウトに関連するプロパティをホストするコンテンツが自動的に設定されます。 これらのコンテンツ プロパティを変更すると、レイアウトが予期しない動作が発生することができます。  
  
 ホストされているコンテンツがいっぱいにドッキングされている、<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>親。 この動作を行うには、いくつかのプロパティは、子プロパティを設定するときに設定されます。 次の表でコンテンツのプロパティが設定される、<xref:System.Windows.Forms.Integration.ElementHost>と<xref:System.Windows.Forms.Integration.WindowsFormsHost>クラスです。  
  
|ホスト クラス|コンテンツのプロパティ|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 ホストされているコンテンツに直接これらのプロパティを設定しません。 詳細については、次を参照してください。 [WindowsFormsHost 要素のレイアウトに関する考慮事項](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)です。  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>ナビゲーション アプリケーション  
 ナビゲーション アプリケーションは、ユーザー状態を保持しない可能性があります。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>ナビゲーション アプリケーションで使用されているときに、要素がそのコントロールを再作成します。 ユーザーがホストしているページから移動したときに発生した子コントロールを再作成する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素とを返します。 ユーザーが型指定されたコンテンツはすべて失われます。  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>メッセージ ループの相互運用  
 使用するときに[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]期待どおりにメッセージ ループ、メッセージは処理されません。 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>メソッドによって呼び出されます、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コンス トラクターです。 このメソッドをメッセージ フィルターを追加、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]メッセージ ループします。 このフィルターを呼び出す、<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>メソッド場合、<xref:System.Windows.Forms.Control?displayProperty=nameWithType>メッセージの対象となったとメッセージの変換/ディスパッチします。  
  
 表示する場合、<xref:System.Windows.Window>で、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]とメッセージ ループ<xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>、ない限り、何も入力することはできません、<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>メソッドです。 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>メソッドは、<xref:System.Windows.Window>を追加し、 <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>、キーに関連するメッセージの経路を変更する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]メッセージ ループします。 詳細については、次を参照してください。 [Windows フォームと WPF の相互運用性入力アーキテクチャ](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)です。  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>不透明度およびレイヤー  
 <xref:System.Windows.Interop.HwndHost>クラスが重ね順をサポートしていません。 つまり、その設定、<xref:System.Windows.UIElement.Opacity%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素も何も起こりません、および他のブレンドは発生しません[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウがあり、 <xref:System.Windows.Window.AllowsTransparency%2A> 'éý'`true`です。  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Dispose  
 クラスが正しく破棄しないと、リソースがリークすることができます。 アプリケーションでは、ハイブリッド、ことを確認、<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>クラスが破棄されると、またはリソース リークが発生する可能性があります。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]破棄する<xref:System.Windows.Forms.Integration.ElementHost>タイミングを制御、非モーダル<xref:System.Windows.Forms.Form>親が終了します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]破棄する<xref:System.Windows.Forms.Integration.WindowsFormsHost>アプリケーションのシャット ダウン時の要素。 表示することは、<xref:System.Windows.Forms.Integration.WindowsFormsHost>内の要素、<xref:System.Windows.Window>で、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]メッセージ ループします。 ここでは、コードは、アプリケーションがシャット ダウンしている通知を受け取りません可能性があります。  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>視覚スタイルを有効にする  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]上の visual スタイル、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]制御が有効にできません。 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>のテンプレートにメソッドが呼び出されます、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーションです。 使用する場合、既定では、このメソッドが呼び出されませんが[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]プロジェクトを作成、表示される[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]Comctl32.dll のバージョン 6.0 が使用可能な場合に、コントロール、visual スタイルします。 呼び出す必要があります、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッド ハンドルは、スレッドで作成する前にします。 詳細については、次を参照してください。[する方法: ハイブリッド アプリケーションで Visual スタイルを有効にする](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)です。  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>ライセンスされたコントロール  
 ライセンス[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]をユーザーにメッセージ ボックスにライセンス情報を表示するコントロールをハイブリッド アプリケーションで予期しない動作が発生する可能性があります。 一部のライセンスされたコントロールは、ハンドルの作成に応答 ダイアログ ボックスを表示します。 たとえば、ライセンスが必要ですが、またはユーザーにある 3 つのコントロールの残りの試用、ライセンスされたコントロールはユーザーに通知可能性があります。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>から派生した要素、<xref:System.Windows.Interop.HwndHost>内でクラス、および子コントロールのハンドルが作成された、<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>メソッドです。 <xref:System.Windows.Interop.HwndHost>クラスでは、メッセージの処理をすることはできません、<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>メソッド、ダイアログ ボックスの表示の指定によってメッセージが送信されます。 このライセンスのシナリオを有効にするを呼び出して、<xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType>としてに割り当てる前にコントロールのメソッド、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の子です。  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF デザイナー  
 使用して、WPF コンテンツをデザインすることができます、[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]です。 次のセクションでは、ハイブリッド アプリケーションを作成するときに発生する可能性がある一般的な問題を一覧表示、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent はデザイン時に無視されます。  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>デザイン時に正常に、プロパティが動作しない可能性があります。  
  
 WPF コントロールに表示される親なっていない場合、WPF ランタイムが無視されます、<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>値。 理由を<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>無視される場合はため<xref:System.Windows.Forms.Integration.ElementHost>別個のオブジェクトが作成される<xref:System.AppDomain>。 ただし、アプリケーションを実行する<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>が期待どおりに機能します。  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Obj フォルダーを削除すると、デザイン時のエラーの一覧が表示されます。  
 Obj フォルダーを削除すると、デザイン時のエラーの一覧が表示されます。  
  
 使用してデザインするときに<xref:System.Windows.Forms.Integration.ElementHost>、Windows フォーム デザイナーは、プロジェクトの obj フォルダー内のデバッグまたはリリース フォルダーに生成されたファイルを使用します。 これらのファイルを削除すると、デザイン時のエラーの一覧が表示されます。 この問題を解決するには、プロジェクトをリビルドします。 詳細については、次を参照してください。 [Windows フォーム デザイナーでデザイン時エラー](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)です。  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost と IME  
 ホストされている WPF コントロール、<xref:System.Windows.Forms.Integration.ElementHost>はサポートされていません、<xref:System.Windows.Forms.Control.ImeMode%2A>プロパティです。 変更<xref:System.Windows.Forms.Control.ImeMode%2A>ホストされるコントロールでは無視されます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF デザイナーでの相互運用性](http://msdn.microsoft.com/en-us/2cb7c1ca-2a75-463b-8801-fba81e2b7042)  
 [Windows フォームと WPF の相互運用性入力アーキテクチャ](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)  
 [方法: ハイブリッド アプリケーションで視覚スタイルを有効にする](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)  
 [WindowsFormsHost 要素のレイアウトに関する考慮事項](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Windows フォーム デザイナーでのデザイン時エラー](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
