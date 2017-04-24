---
title: "WPF と Windows フォームの相互運用性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ハイブリッド コントロール [WPF 相互運用性]"
  - "相互運用性 [WPF], Windows フォーム"
  - "入れ子になった相互運用 [WPF]"
  - "Windows フォーム [WPF], 相互運用性"
  - "Windows フォーム, WPF 相互運用"
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# WPF と Windows フォームの相互運用性
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]は、アプリケーション インターフェイスを作成するための 2 つの異なるアーキテクチャを提供します。  <xref:System.Windows.Forms.Integration?displayProperty=fullName> 名前空間は、共通の相互運用シナリオを可能にするクラスを提供します。  相互運用機能を実装する 2 つの主要クラスは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> と <xref:System.Windows.Forms.Integration.ElementHost> です。  ここでは、サポートされる相互運用シナリオと、サポートされないシナリオについて説明します。  
  
> [!NOTE]
>  *ハイブリッド コントロール* シナリオには特に注意する必要があります。  ハイブリッド コントロールは、あるテクノロジのコントロールの入れ子になっている別のテクノロジのコントロールです。  これは、*入れ子になった相互運用*とも呼ばれます。  *複数レベルのハイブリッド コントロール*には、複数のレベルで入れ子になっているハイブリッド コントロールが含まれます。  複数レベルの入れ子になった相互運用の例として、ある [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールに [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールが含まれ、さらにそのコントロールに [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールが含まれている場合があります。  複数レベルのハイブリッド コントロールはサポートされていません。  
  
   
  
<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## WPF での Windows フォーム コントロールのホスト  
 次の相互運用のシナリオは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールが [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] コントロールをホストする場合にサポートされます。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールは、XAML を使用して 1 つ以上の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールをホストできます。  
  
-   コードを使用して 1 つ以上の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールをホストできます。  
  
-   他の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを含む [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コンテナー コントロールをホストできます。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] マスターおよび [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 詳細を使用して、マスター\/詳細フォームをホストできます。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] マスターおよび [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 詳細を使用して、マスター\/詳細フォームをホストできます。  
  
-   1 つ以上の [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] コントロールをホストできます。  
  
-   1 つ以上の複合コントロールをホストできます。  
  
-   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用してハイブリッド コントロールをホストできます。  
  
-   コードを使用してハイブリッド コントロールをホストできます。  
  
### レイアウトのサポート  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素がホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のレイアウト システムに統合する際の既知の制限を次のリストに示します。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、サイズを変更できなかったり、特定のサイズにしか設定できない場合があります。  たとえば、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> コントロールは、コントロールのフォント サイズで定義されている 1 つの高さしかサポートしていません。  要素を垂直方向に伸縮できると想定される、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の動的レイアウトでは、ホストされている <xref:System.Windows.Forms.ComboBox> コントロールは同様には伸縮できません。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは回転または斜めにすることはできません。  たとえば、ユーザー インターフェイスを 90°回転した場合、ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールの垂直の位置は維持されます。  
  
-   ほとんどの場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、比率を保持したまま拡大縮小することはできません。  コントロール全体のサイズは拡大縮小されますが、コントロールの子コントロールやコンポーネント要素のサイズは希望どおりに変更できません。  この制限は、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] の各コントロールで拡大縮小をどの程度サポートしているかに依存します。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ユーザー インターフェイスでは、要素の z オーダーを変更して重複を制御できます。  ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは別の HWND で描画されるため、常に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素の一番上に描画されます。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、フォント サイズに基づく自動スケーリングをサポートします。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ユーザー インターフェイスでは、フォント サイズを変更しても、レイアウト全体のサイズは変わりません。ただし、個々の要素は動的にサイズを変更できます。  
  
### アンビエント プロパティ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの一部のアンビエント プロパティは、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] と同等の機能があります。  これらのアンビエント プロパティは、ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールに適用され、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールのパブリック プロパティとして公開されます。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールは、各 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アンビエント プロパティをその [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の等価プロパティに変換します。  
  
 詳細については、「[Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)」を参照してください。  
  
### \[動作\]  
 相互運用動作の説明を次の表に示します。  
  
|\[動作\]|サポート状況|Not supported|  
|------------|------------|-------------------|  
|透過性|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールのレンダリングは透過性をサポートします。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の親コントロールの背景を、ホストしている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールの背景にすることができます。|一部の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、透過性をサポートしません。  たとえば、<xref:System.Windows.Forms.TextBox> コントロールと <xref:System.Windows.Forms.ComboBox> コントロールは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でホストされている場合、透明になりません。|  
|Tab キーによる移動|ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールのタブ オーダーは、それらのコントロールが [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ベースのアプリケーションでホストされている場合と同じです。<br /><br /> Tab キーおよび Shift \+ Tab キーを使用した [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールから [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールへの Tab キーによる移動は、通常どおり動作します。<br /><br /> <xref:System.Windows.Forms.Control.TabStop%2A> プロパティの値が `false` になっている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、ユーザーがコントロール間を Tab キーで移動しても、フォーカスを受け取りません。<br /><br /> -   各 <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールは <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> 値を持ちます。この値は、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールがフォーカスを受け取るタイミングを決定します。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> コンテナー内に含まれている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、<xref:System.Windows.Forms.Control.TabIndex%2A> プロパティで指定されたタブ オーダーに従います。  最後のタブ インデックスで Tab キーを押すと、次の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール \(存在する場合\) にフォーカスが移ります。  他にフォーカスを取得できる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールが存在しない場合、Tab キーを押すと、タブ オーダーの最初の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールに移動します。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> 内のコントロールの <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> 値は、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールに含まれている兄弟 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを基準にします。<br />-   Tab キーによる移動は、コントロール固有の動作に従います。  たとえば、<xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> プロパティの値が `true` になっている <xref:System.Windows.Forms.TextBox> コントロールで Tab キーを押すと、フォーカスが移動するのではなく、テキスト ボックス内にタブが入力されます。|該当なし。|  
|方向キーによるナビゲーション|-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールでの方向キーによるナビゲーションは、通常の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コンテナー コントロールと同じです。上方向キーと左方向キーは前のコントロールを選択し、下方向キーと右方向キーは次のコントロールを選択します。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールに含まれている最初のコントロールで上方向キーと左方向キーを押すと、Shift \+ Tab キーボード ショートカットと同じアクションが実行されます。  フォーカスを取得できる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールが存在する場合は、フォーカスは <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロール外に移動します。  この動作は、最後のコントロールに折り返されないという点で、標準の <xref:System.Windows.Forms.ContainerControl> の動作とは異なります。  他にフォーカスを取得できる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールが存在しない場合、フォーカスはタブ オーダーの最後の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールに戻ります。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールに含まれている最後のコントロールで下方向キーと右方向キーを押すと、Tab キーと同じアクションが実行されます。  フォーカスを取得できる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールが存在する場合は、フォーカスは <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロール外に移動します。  この動作は、最初のコントロールに折り返されないという点で、標準の <xref:System.Windows.Forms.ContainerControl> の動作とは異なります。  他にフォーカスを取得できる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールが存在しない場合、フォーカスはタブ オーダーの最初の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールに戻ります。|該当なし。|  
|アクセラレータ|アクセラレータは、"サポートなし" 列に示されている場合を除き、通常どおり動作します。|テクノロジ間で重複するアクセラレータは、通常の重複するアクセラレータのようには動作しません。  アクセラレータがテクノロジ間で重複する場合、つまり、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールに 1 つ以上、および [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールにも他のアクセラレータがある場合は、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールはアクセラレータを常に受け取ります。  重複するアクセラレータ キーが押された場合、フォーカスはコントロール間で切り替わりません。|  
|ショートカット キー|ショートカット キーは、"サポートなし" 列に示されている場合を除き、通常どおり動作します。|-   事前処理段階で処理される [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ショートカット キーは常に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ショートカット キーよりも優先されます。  たとえば、Ctrl \+ S ショートカット キーが定義されている <xref:System.Windows.Forms.ToolStrip> コントロールがあり、CTRL \+ S にバインドされている [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コマンドがある場合、フォーカスに関係なく、<xref:System.Windows.Forms.ToolStrip> コントロール ハンドラーが常に最初に呼び出されます。<br />-   <xref:System.Windows.Forms.Control.KeyDown> イベントで処理される [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ショートカット キーは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で最後に処理されます。  この動作を回避するには、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールの <xref:System.Windows.Forms.Control.IsInputKey%2A> メソッドをオーバーライドするか、<xref:System.Windows.Forms.Control.PreviewKeyDown> イベントを処理します。  <xref:System.Windows.Forms.Control.IsInputKey%2A> メソッドから `true` を返すか、<xref:System.Windows.Forms.Control.PreviewKeyDown> イベント ハンドラーで <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=fullName> プロパティの値を `true` に設定します。|  
|AcceptsReturn、AcceptsTab、およびその他のコントロール固有の動作|既定のキーボードの動作を変更するプロパティは、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールが <xref:System.Windows.Forms.Control.IsInputKey%2A> メソッドをオーバーライドして `true` を返す場合、通常どおり動作します。|<xref:System.Windows.Forms.Control.KeyDown> イベントで既定のキーボードの動作を変更する [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、ホストの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールで最後に処理されます。  これらのコントロールは最後に処理されるため、予期しない動作が発生する場合があります。|  
|Enter イベントと Leave イベント|含まれている <xref:System.Windows.Forms.Integration.ElementHost> コントロールにフォーカスが移動しない場合に、フォーカスが 1 つの <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールで変更されると、Enter イベントと Leave イベントは通常どおり発生します。|Enter イベントと Leave イベントは、次のフォーカスの変更が行われるまで発生しません。<br /><br /> -   <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールの内部から外部への変更。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールの外部から内部への変更。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールの外部での変更。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールでホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールから、同じ <xref:System.Windows.Forms.Integration.WindowsFormsHost> 内でホストされている <xref:System.Windows.Forms.Integration.ElementHost> コントロールへの変更。|  
|マルチスレッド|あらゆる種類のマルチスレッドがサポートされます。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] と [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の両方のテクノロジでは、シングルスレッドの同時実行モデルを前提にしています。  デバッグ中は、他のスレッドからフレームワーク オブジェクトを呼び出すと例外が発生し、この要件が強制されます。|  
|セキュリティ|すべての相互運用シナリオには完全な信頼が必要です。|相互運用シナリオは、部分的な信頼ではサポートされません。|  
|アクセシビリティ|すべてのアクセシビリティ シナリオがサポートされます。  支援技術製品は、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] と [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の両方のコントロールを含むハイブリッド アプリケーションで使用すると正しく動作します。|該当なし。|  
|クリップボード|すべてのクリップボードは通常どおり操作できます。  これには、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールと [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール間の切り取りと貼り付けも含まれます。|該当なし。|  
|ドラッグ アンド ドロップ機能|すべてのドラッグ アンド ドロップは通常どおり操作できます。  これには、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールと [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール間の操作も含まれます。|該当なし。|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## Windows フォームでの WPF コントロールのホスト  
 次の相互運用のシナリオは、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] コントロールが [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールをホストする場合にサポートされます。  
  
-   コードを使用して 1 つ以上の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールをホストする。  
  
-   プロパティ シートを 1 つ以上のホストされている [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールに関連付ける。  
  
-   フォームで 1 つ以上の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページをホストする。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ウィンドウを起動する。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] マスターおよび [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 詳細を使用したマスター\/詳細フォームのホスト。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] マスターおよび [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 詳細を使用したマスター\/詳細フォームのホスト。  
  
-   カスタム [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールをホストする。  
  
-   ハイブリッド コントロールをホストする。  
  
### アンビエント プロパティ  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールの一部のアンビエント プロパティは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と同等の機能があります。  これらのアンビエント プロパティは、ホストされている [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールに適用され、<xref:System.Windows.Forms.Integration.ElementHost> コントロールのパブリック プロパティとして公開されます。  <xref:System.Windows.Forms.Integration.ElementHost> コントロールは、各 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アンビエント プロパティをその [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の等価プロパティに変換します。  
  
 詳細については、「[Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)」を参照してください。  
  
### \[動作\]  
 相互運用動作の説明を次の表に示します。  
  
|\[動作\]|サポート状況|Not supported|  
|------------|------------|-------------------|  
|透過性|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールのレンダリングは透過性をサポートします。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] の親コントロールの背景を、ホストしている [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの背景にすることができます。|該当なし。|  
|マルチスレッド|あらゆる種類のマルチスレッドがサポートされます。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] と [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の両方のテクノロジでは、シングルスレッドの同時実行モデルを前提にしています。  デバッグ中は、他のスレッドからフレームワーク オブジェクトを呼び出すと例外が発生し、この要件が強制されます。|  
|セキュリティ|すべての相互運用シナリオには完全な信頼が必要です。|相互運用シナリオは、部分的な信頼ではサポートされません。|  
|アクセシビリティ|すべてのアクセシビリティ シナリオがサポートされます。  支援技術製品は、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] と [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の両方のコントロールを含むハイブリッド アプリケーションで使用すると正しく動作します。|該当なし。|  
|クリップボード|すべてのクリップボードは通常どおり操作できます。  これには、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールと [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール間の切り取りと貼り付けも含まれます。|該当なし。|  
|ドラッグ アンド ドロップ機能|すべてのドラッグ アンド ドロップは通常どおり操作できます。  これには、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールと [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール間の操作も含まれます。|該当なし。|  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [チュートリアル: WPF での Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)   
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [Windows フォームと WPF プロパティの割り当て](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)