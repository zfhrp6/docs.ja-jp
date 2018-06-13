---
title: WPF と Windows フォームの相互運用性
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 7090a557a0493825e44985b15e065803ee3d48a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549231"
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF と Windows フォームの相互運用性
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーション インターフェイスを作成するための 2 つの異なるアーキテクチャを提供します。 <xref:System.Windows.Forms.Integration?displayProperty=nameWithType>名前空間は、一般的な相互運用シナリオを有効にするクラスを提供します。 相互運用機能を実装する 2 つのキー クラス<xref:System.Windows.Forms.Integration.WindowsFormsHost>と<xref:System.Windows.Forms.Integration.ElementHost>です。 このトピックには、相互運用シナリオがサポートされているし、するシナリオはサポートされていませんがについて説明します。  
  
> [!NOTE]
>  特別な考慮する、*ハイブリッド コントロール*シナリオです。 ハイブリッド コントロールには、その他のテクノロジからのコントロールで入れ子にされた 1 つのテクノロジからのコントロールがあります。 これとも呼ばれます、*入れ子になったの相互運用*です。 A*マルチレベル ハイブリッド コントロール*ハイブリッドの複数のレベルは入れ子を制御します。 複数レベルの入れ子になった相互運用の例は、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]が含まれるコントロール、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールで、含まれる別[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。 複数レベルのハイブリッド コントロールはサポートされていません。  
  
  
<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>WPF でのフォーム コントロールの Windows をホストしています。  
 次の相互運用シナリオがサポートされているときに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールは、Windows フォーム コントロールをホストします。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールは、1 つまたは複数をホストできます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]XAML の使用を制御します。  
  
-   1 つまたは複数をホストできます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コードの使用を制御します。  
  
-   ホストできます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]を含むその他のコンテナー コントロール[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
-   マスター/詳細フォームをホストできます、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マスターと[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]詳細です。  
  
-   マスター/詳細フォームをホストできます、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]マスターと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]詳細です。  
  
-   1 つまたは複数をホストできます[!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)]コントロール。  
  
-   1 つまたは複数の複合コントロールをホストできます。  
  
-   使用してハイブリッド コントロールをホストできます[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。  
  
-   コードを使用してハイブリッド コントロールをホストできます。  
  
### <a name="layout-support"></a>レイアウトのサポート  
 次の一覧が既知の制限事項について説明しますと、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が、そのホストされている統合しようとしています。[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]にコントロールを、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト システムです。  
  
-   場合によっては、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールのサイズを変更することはできません、または特定のディメンションにのみサイズを変更できます。 たとえば、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox>コントロールにのみ、1 つの高さ、コントロールのフォント サイズで定義されているがサポートしています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素のホスト型が垂直方向にストレッチできることを前提としていますが、動的レイアウト<xref:System.Windows.Forms.ComboBox>期待どおりに、コントロールは伸縮しません。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、回転または傾斜ことはできません。 たとえば、ユーザー インターフェイスを 90 度回転するときにホストされている[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールの垂直位置が維持されます。  
  
-   ほとんどの場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは比例拡大/縮小をサポートしていません。 コントロール全体のサイズをスケールが子コントロールおよびコントロールのコンポーネント要素可能性がありますいないサイズを変更する期待どおりにします。 この制限はどの程度それぞれ異なります[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがスケーリングをサポートします。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ユーザー インターフェイス コントロールの動作の重複する要素の z オーダーを変更することができます。 ホストされた[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の上に常に描画されるように、別の HWND にコントロールが描画される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、フォント サイズに基づく自動スケーリングをサポートします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]個々 の要素が動的に変更が、フォント サイズを変更するユーザー インターフェイスは全体のレイアウトのサイズを変更できません。  
  
### <a name="ambient-properties"></a>アンビエント プロパティ  
 一部のアンビエント プロパティの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールがある[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]相当します。 これらのアンビエント プロパティが反映されますをホストする[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]を制御し、上のパブリック プロパティとして公開されている、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールにそれぞれ変換[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アンビエント プロパティにその[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と同等です。  
  
 詳細については、次を参照してください。 [Windows フォームと WPF プロパティ マッピング](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)です。  
  
### <a name="behavior"></a>動作  
 次の表では、相互運用の動作について説明します。  
  
|動作|サポート状況|サポートなし|  
|--------------|---------------|-------------------|  
|[透明度]|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールの描画には、透過性がサポートされています。 親の背景[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールの背景になるホステッド[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。|いくつか[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは透明度をサポートしていません。 たとえば、<xref:System.Windows.Forms.TextBox>と<xref:System.Windows.Forms.ComboBox>コントロールをによってホストされているときに、透明にすることはできません[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。|  
|タブ移動|タブ オーダーでホストされている[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールは、これらのコントロールがでホストされている場合と同じ、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-ベースのアプリケーションです。<br /><br /> Tab キー、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]通常どおりに動作を TAB キーと shift キーを押しながら TAB キーを制御します。<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 持つコントロール、<xref:System.Windows.Forms.Control.TabStop%2A>のプロパティの値`false`コントロールを通じて、ユーザーがタブ、フォーカスが返されません。<br /><br /> -各<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールが、<xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>タイミングを決定する値を<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールがフォーカスを受け取る。<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロール内に含まれる、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コンテナーで指定された順序に従う、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティです。 次のフォーカスをタブの最後のタブ インデックスから[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]が存在する場合は、制御します。 その他のフォーカス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールが存在する、最初に戻りますをタブ移動[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]タブ オーダーのコントロールです。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> コントロール内の値、<xref:System.Windows.Forms.Integration.WindowsFormsHost>兄弟に相対的[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールに含まれている、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。<br />のコントロール固有の動作は、タブ移動されます。 TAB キーを押した場合など、<xref:System.Windows.Forms.TextBox>を持つコントロールを<xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A>のプロパティの値`true`タブ、テキスト ボックスに入力フォーカスを移動する代わりにします。|該当なし。|  
|方向キーを使用したナビゲーション|矢印の付いたナビゲーション キーに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、通常と同じ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コンテナー コントロール:、上向き矢印と左方向キーは、前のコントロールを選択し、下向きの矢印キーと → キーは [次へ] のコントロールを選択します。<br />-最初のコントロールに含まれているからと左方向キーを<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、SHIFT キーを押しながら TAB キーのキーボード ショートカットと同じアクションを実行します。 ある場合、フォーカスを設定できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]外部コントロール、フォーカスの移動、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。 この動作は、標準<xref:System.Windows.Forms.ContainerControl>での動作は行われませんが最後にコントロールをラップします。 その他のフォーカス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールが存在すると、フォーカスが戻ります最後[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]タブ オーダーのコントロールです。<br />-最後のコントロールに含まれている、左右の矢印キーを<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、TAB キーと同じアクションを実行します。 ある場合、フォーカスを設定できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]外部コントロール、フォーカスの移動、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。 この動作は、標準<xref:System.Windows.Forms.ContainerControl>で動作最初のコントロールに折り返しは行われません。 その他のフォーカス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にフォーカスが戻りますコントロールが存在する最初の[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]タブ オーダーのコントロールです。|該当なし。|  
|アクセラレータ|アクセラレータは、「サポートされていません」の列に示されている場合を除き、通常どおり動作します。|テクノロジ アクセラレータが重複は通常のアクセラレータが重複と同様に機能しません。 上に少なくとも 1 つのテクノロジ アクセラレータが重複してとき、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールと別のコンピューター、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが常にアクセラレータを受け取ります。 重複するアクセラレータが押されたときに、コントロールの間でフォーカスが切り替わりません。|  
|ショートカット キー|ショートカット キーは、「サポートされていません」の列に示されている場合を除き、通常どおり動作します。|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 前処理段階で常に処理されるショートカット キーよりも優先[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ショートカット キー。 ある場合など、<xref:System.Windows.Forms.ToolStrip>で CTRL + S ショートカット キーが定義されている、制御し、は、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] CTRL + S にバインドされているコマンド、<xref:System.Windows.Forms.ToolStrip>フォーカスに関係なくコントロール ハンドラーが最初に、常に呼び出されます。<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ショートカット キーによって処理される、<xref:System.Windows.Forms.Control.KeyDown>イベントは最後に処理で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 この動作をオーバーライドすることで防ぐことができます、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールの<xref:System.Windows.Forms.Control.IsInputKey%2A>メソッドまたは処理、<xref:System.Windows.Forms.Control.PreviewKeyDown>イベント。 返す`true`から、<xref:System.Windows.Forms.Control.IsInputKey%2A>メソッド、またはの値の設定、<xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType>プロパティを`true`で、<xref:System.Windows.Forms.Control.PreviewKeyDown>イベント ハンドラー。|  
|AcceptsReturn、AcceptsTab、およびその他のコントロールに固有の動作|既定のキーボードの動作を変更するプロパティの動作を通常どおり、あると仮定して、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]オーバーライドを制御、<xref:System.Windows.Forms.Control.IsInputKey%2A>を返すメソッドを`true`です。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 既定値を変更するコントロールでは、動作をキーボード処理することにより、<xref:System.Windows.Forms.Control.KeyDown>イベントは、ホストで最後に処理[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。 これらのコントロールが最後に処理されるため、予期しない動作が生成されることができます。|  
|Enter および Leave イベント|フォーカスがないに含まれているとする場合<xref:System.Windows.Forms.Integration.ElementHost>コントロールが入力されのままにしてイベントが通常どおり、1 つにフォーカスが変更されたときに発生<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。|入力し、次のフォーカス変更が発生したときのままにしてイベントは発生しません。<br /><br /> 元の外側を inside、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。<br />外部の内、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。<br />外側、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロール。<br />[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]でホストされるコントロール、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールを<xref:System.Windows.Forms.Integration.ElementHost>同じ内部でホストされるコントロール<xref:System.Windows.Forms.Integration.WindowsFormsHost>です。|  
|マルチスレッド|マルチ スレッドのすべての種類がサポートされています。|両方の[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テクノロジには、シングル スレッドの同時実行モデルが前提としています。 デバッグ中に他のスレッドから framework オブジェクトへの呼び出しでこの要件を強制する例外が発生します。|  
|セキュリティ|すべての相互運用シナリオでは、完全な信頼が必要です。|部分信頼では、相互運用シナリオは許可されません。|  
|ユーザー補助|すべてのユーザー補助機能のシナリオはサポートされています。 両方を含むハイブリッド アプリケーションを使用している場合に、支援技術製品が正常に機能[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
|クリップボードのトピック|すべてのクリップボードは通常どおり操作できます。 これには、カット アンド ペースト間が含まれます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
|ドラッグ アンド ドロップ機能|すべてのドラッグ アンド ドロップ操作が通常どおりに動作します。 間での操作が含まれます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Windows フォームで WPF コントロールをホストしています。  
 Windows フォーム コントロールのホスト時に、次の相互運用シナリオはサポートされて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
-   1 つまたは複数のホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コードの使用を制御します。  
  
-   いずれかのシートまたは複数のホストのプロパティを関連付ける[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
-   1 つまたは複数のホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォーム内のページです。  
  
-   以降、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウです。  
  
-   マスター/詳細フォームをホストしている、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]マスターと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]詳細です。  
  
-   マスター/詳細フォームをホストしている、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マスターと[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]詳細です。  
  
-   ユーザー設定をホストしている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
-   ハイブリッド コントロールをホストします。  
  
### <a name="ambient-properties"></a>アンビエント プロパティ  
 一部のアンビエント プロパティの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがある[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]相当します。 これらのアンビエント プロパティが反映されますをホストする[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を制御し、上のパブリック プロパティとして公開されている、<xref:System.Windows.Forms.Integration.ElementHost>コントロール。 <xref:System.Windows.Forms.Integration.ElementHost>コントロールにそれぞれ変換[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アンビエント プロパティをその[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と同等です。  
  
 詳細については、次を参照してください。 [Windows フォームと WPF プロパティ マッピング](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)です。  
  
### <a name="behavior"></a>動作  
 次の表では、相互運用の動作について説明します。  
  
|動作|サポート状況|サポートなし|  
|--------------|---------------|-------------------|  
|[透明度]|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの描画には、透過性がサポートされています。 親の背景[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールの背景になるホステッド[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
|マルチスレッド|マルチ スレッドのすべての種類がサポートされています。|両方の[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テクノロジには、シングル スレッドの同時実行モデルが前提としています。 デバッグ中に他のスレッドから framework オブジェクトへの呼び出しでこの要件を強制する例外が発生します。|  
|セキュリティ|すべての相互運用シナリオでは、完全な信頼が必要です。|部分信頼では、相互運用シナリオは許可されません。|  
|ユーザー補助|すべてのユーザー補助機能のシナリオはサポートされています。 両方を含むハイブリッド アプリケーションを使用している場合に、支援技術製品が正常に機能[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
|クリップボードのトピック|すべてのクリップボードは通常どおり操作できます。 これには、カット アンド ペースト間が含まれます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
|ドラッグ アンド ドロップ機能|すべてのドラッグ アンド ドロップ操作が通常どおりに動作します。 間での操作が含まれます[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。|該当なし。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [チュートリアル: WPF での Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
