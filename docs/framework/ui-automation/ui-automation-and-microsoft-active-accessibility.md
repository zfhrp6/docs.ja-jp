---
title: "UI Automation and Microsoft Active Accessibility | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Active Accessibility"
  - "UI Automation, Active Accessibility compared to"
  - "UI Automation, Microsoft Active Accessibility"
  - "Active Accessibility, UI Automation compared to"
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
caps.latest.revision: 24
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 23
---
# UI Automation and Microsoft Active Accessibility
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の最新情報については、「[Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」をご覧ください。  
  
 アプリケーションをアクセス可能にするための以前のソリューションは [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] です。[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] は [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] の新しいユーザー補助モデルであり、その目的は支援技術製品と自動テスト ツールのニーズを解決することです。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は多くの点で [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] よりも強化されています。  
  
 このトピックでは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の主な機能を紹介し、[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] との違いについて説明します。  
  
<a name="Programming_Languages_compare"></a>   
## プログラミング言語  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] は [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] をベースにしてデュアル インターフェイスをサポートしているため、C\/C\+\+、[!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]、およびスクリプト言語でプログラムすることができます。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] \(標準コントロールのクライアント側プロバイダー ライブラリを含む\) はマネージ コードで記述されており、[!INCLUDE[TLA#tla_vcshrp](../../../includes/tlasharptla-vcshrp-md.md)] または [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)] を使用して UI オートメーション クライアント アプリケーションを実に簡単にプログラムすることができます。 インターフェイスを実装する UI オートメーション プロバイダーは、マネージ コードまたは C\/C\+\+ で記述できます。  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## Windows Presentation Foundation におけるサポート  
 [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] はユーザー インターフェイスを作成するための新しいモデルです。[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] の要素には [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] のネイティブ サポート機能はありませんが、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] をサポートしており、これに [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] クライアントのためのブリッジ サポートが含まれています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 専用に作成されたクライアントだけが [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] のユーザー補助機能 \(テキストに関する豊富なサポートなど\) を最大限に利用できます。  
  
<a name="Servers_and_Clients_compare"></a>   
## サーバーとクライアント  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] では、サーバーとクライアントは、主にサーバーによる `IAccessible` の実装を介して直接通信します。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、サーバー \(プロバイダー\) とクライアントの間にコア サービスが存在します。 このコア サービスは、プロバイダーによって実装されたインターフェイスを呼び出して、追加のサービス \(要素の一意のランタイム識別子の生成など\) を提供します。 クライアント アプリケーションはライブラリ関数を使用して [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] サービスを呼び出します。  
  
 UI オートメーション プロバイダーは [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] クライアントに情報を提供でき、[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] サーバーは UI オートメーション クライアント アプリケーションに情報を提供できます。 ただし、[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] は [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ほど多くの情報を公開しないため、この 2 つのモデルには完全な互換性がありません。  
  
<a name="UI_Elements_compare"></a>   
## UI 要素  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] では [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素を `IAccessible` インターフェイスまたは子識別子として表現します。 2 つの `IAccessible` ポインターを比較してそれらが同じ要素を参照しているかどうかを判断するのは困難です。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、すべての要素が <xref:System.Windows.Automation.AutomationElement> オブジェクトとして表現されます。 比較は等値演算子または <xref:System.Windows.Automation.AutomationElement.Equals%2A> メソッドを使用して行われますが、どちらの方法でも、要素の一意のランタイム識別子が比較されます。  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## ツリー ビューとナビゲーション  
 画面上の [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 要素は、ツリー構造で表すことができます。デスクトップがルートで、その直接の子としてアプリケーション ウィンドウがあり、アプリケーション内の要素がその子孫となります。  
  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] では、エンドユーザーには無関係なオートメーション要素も多数、ツリー内に公開されます。 クライアント アプリケーションは、すべての要素の中から意味のあるものを特定する必要があります。  
  
 UI オートメーション クライアント アプリケーションは、フィルタリングしたビューを使用して [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] を確認します。 このビューには、必要な要素 \(ユーザーに情報を提供したり、対話を可能にしたりする要素\) のみが表示されます。 コントロール要素だけが含まれるビューや、コンテンツ要素だけが含まれるビューがあらかじめ定義されています。さらに、アプリケーションでカスタム ビューを定義することもできます。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、ユーザーに対して [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] を簡単に表せるようにして、ユーザーとアプリケーションの対話を支援します。  
  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] における要素間ナビゲーションは、空間的 \(画面上で左にある要素に移動するなど\)、論理的 \(次のメニュー項目に移動する、ダイアログ ボックスのタブ オーダー内で次の項目に移動するなど\)、階層的 \(コンテナー内の最初の子に移動する、子からその親に移動するなど\) のいずれかです。 子要素が `IAccessible` を実装しているオブジェクトであるとは限らないため、階層的ナビゲーションは複雑です。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、すべての [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素は、同じ基本機能をサポートする <xref:System.Windows.Automation.AutomationElement> オブジェクトです  \(プロバイダーの観点では、<xref:System.Windows.Automation.Provider.IRawElementProviderSimple> から継承されたインターフェイスを実装するオブジェクトです\)。 ナビゲーションは主に階層的 \(親から子、兄弟から次の兄弟\) です  \(兄弟間のナビゲーションは、タブ オーダーに従う場合があるため、論理的要素も持っています\)。 フィルタリングされたツリー ビューで <xref:System.Windows.Automation.TreeWalker> クラスを使用して、任意の場所からナビゲーションを開始できます。<xref:System.Windows.Automation.AutomationElement.FindFirst%2A> と <xref:System.Windows.Automation.AutomationElement.FindAll%2A> を使用して、特定の子または子孫に移動することもできます。たとえば、指定したコントロール パターンがサポートされるダイアログ ボックス内のすべての要素を非常に簡単に取得できます。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] におけるナビゲーションは [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] におけるナビゲーションより一貫性があります。 ドロップダウン リストやポップアップ ウィンドウなど、[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] ツリーに 2 回表示される要素がありますが、このような要素からナビゲーションすると、予期しない結果が生じる可能性があります。 実際には、rebar コントロールに対して [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] を正しく実装することは不可能です。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では親の再指定や位置の変更が可能なため、ウィンドウの所有関係による階層にかかわらず、要素をツリー内の任意の場所に配置できます。  
  
<a name="Roles_and_Control_Types"></a>   
## 役割とコントロール型  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] は、`accRole` プロパティ \(`IAccessible::get_actRole`\) を使用して、ROLE\_SYSTEM\_SLIDER や ROLE\_SYSTEM\_MENUITEM などの [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 内の要素のｙｗの記述を取得します。 要素の役割は、要素の機能を表す主要な鍵になります。 コントロールとの対話は、`IAccessible::accSelect` や `IAccessible::accDoDefaultAction` などの固定のメソッドを使用して実現されます。 クライアント アプリケーションと [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] の間の対話は、`IAccessible` を通して実行できる範囲に限定されます。  
  
 これに対して、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、要素のコントロール型 \(<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> プロパティで記述\) と、その要素に期待される機能とが大きく分離されています。 機能は、特殊なインターフェイスの実装を通じてプロバイダーによってサポートされる、コントロール パターンによって決定されます。 複数のコントロール パターンを組み合わせると、特定の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素がサポートする機能をすべて記述することができます。 プロバイダーによっては、ある 1 つの特定のコントロール パターンをサポートしなければならないものがあります。たとえば、チェック ボックスのプロバイダーは Toggle コントロール パターンをサポートする必要があります。 また、コントロール パターンのセットを 1 つ以上サポートしなければならないものもあります。たとえば、ボタンは、Toggle と Invoke のいずれかをサポートする必要があります。 さらに、コントロール パターンをまったくサポートしないものもあります。たとえば、移動もサイズ変更もドッキングもできないペインには、コントロール パターンはありません。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、<xref:System.Windows.Automation.ControlType.Custom> プロパティによって識別され、<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> プロパティによって記述可能なカスタム コントロールをサポートします。  
  
 次の表に、[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] の役割と [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のコントロール型のマッピングを示します。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] の役割|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のコントロール型|  
|---------------------------------------------------------------------|------------------------------------------------------------------------------------|  
|ROLE\_SYSTEM\_PUSHBUTTON|ボタン|  
|ROLE\_SYSTEM\_CLIENT|予定表|  
|ROLE\_SYSTEM\_CHECKBUTTON|チェック ボックス|  
|ROLE\_SYSTEM\_COMBOBOX|コンボ ボックス|  
|ROLE\_SYSTEM\_CLIENT|カスタム|  
|ROLE\_SYSTEM\_LIST|データ グリッド|  
|ROLE\_SYSTEM\_LISTITEM|データ項目|  
|ROLE\_SYSTEM\_DOCUMENT|ドキュメント|  
|ROLE\_SYSTEM\_TEXT|編集|  
|ROLE\_SYSTEM\_GROUPING|グループ化|  
|ROLE\_SYSTEM\_LIST|ヘッダー|  
|ROLE\_SYSTEM\_COLUMNHEADER|ヘッダー項目|  
|ROLE\_SYSTEM\_LINK|ハイパーリンク|  
|ROLE\_SYSTEM\_GRAPHIC|イメージ|  
|ROLE\_SYSTEM\_LIST|リスト|  
|ROLE\_SYSTEM\_LISTITEM|リスト項目|  
|ROLE\_SYSTEM\_MENUPOPUP|メニュー|  
|ROLE\_SYSTEM\_MENUBAR|メニュー バー|  
|ROLE\_SYSTEM\_MENUITEM|メニュー項目|  
|ROLE\_SYSTEM\_PANE|ペイン|  
|ROLE\_SYSTEM\_PROGRESSBAR|進行状況バー|  
|ROLE\_SYSTEM\_RADIOBUTTON|オプション ボタン|  
|ROLE\_SYSTEM\_SCROLLBAR|スクロール バー|  
|ROLE\_SYSTEM\_SEPARATOR|区切り記号|  
|ROLE\_SYSTEM\_SLIDER|スライダー|  
|ROLE\_SYSTEM\_SPINBUTTON|Spinner|  
|ROLE\_SYSTEM\_SPLITBUTTON|分割ボタン|  
|ROLE\_SYSTEM\_STATUSBAR|ステータス バー|  
|ROLE\_SYSTEM\_PAGETABLIST|タブ|  
|ROLE\_SYSTEM\_PAGETAB|タブ項目|  
|ROLE\_SYSTEM\_TABLE|テーブル|  
|ROLE\_SYSTEM\_STATICTEXT|テキスト|  
|ROLE\_SYSTEM\_INDICATOR|つまみ|  
|ROLE\_SYSTEM\_TITLEBAR|タイトル バー|  
|ROLE\_SYSTEM\_TOOLBAR|ツール バー|  
|ROLE\_SYSTEM\_TOOLTIP|ヒント|  
|ROLE\_SYSTEM\_OUTLINE|ツリー|  
|ROLE\_SYSTEM\_OUTLINEITEM|ツリー項目|  
|ROLE\_SYSTEM\_WINDOW|\[Window\]|  
  
 さまざまなコントロール型の詳細については、「[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)」を参照してください。  
  
<a name="States_and_Properties"></a>   
## 状態とプロパティ  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] では、要素は一般的なプロパティのセットをサポートします。一部のプロパティ \(`accState` など\) は、要素の役割に応じてまったく異なる内容を記述する必要があります。 サーバーは、プロパティを返す `IAccessible` のメソッドをすべて \(要素に無関係なものも含む\) 実装する必要があります。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、さらに多くのプロパティが定義されており、その一部は [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] での状態に対応します。 すべての要素に共通するものもあれば、コントロール型とコントロール パターンに固有のものもあります。 プロパティは一意の識別子によって識別され、ほとんどのプロパティは単一のメソッド \(<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> または <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>\) を使用して取得できます。 多くのプロパティは、<xref:System.Windows.Automation.AutomationElement.Current%2A> プロパティ アクセサーおよび <xref:System.Windows.Automation.AutomationElement.Cached%2A> プロパティ アクセサーからも容易に取得できます。  
  
 UI オートメーション プロバイダーは、無関係なプロパティを実装する必要はなく、サポートしていないプロパティに対しては単に `null` 値を返すことができます。 また、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のコア サービスは、一部のプロパティを既定のウィンドウ プロバイダーから取得できます。これらのプロパティは、プロバイダーによって明示的に実装されたプロパティと 1 つにまとめられます。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、多くのプロパティをサポートすることに加えて、単一のプロセス間呼び出しで複数のプロパティを取得できるので、パフォーマンスが向上します。  
  
 次の表に、2 つのモデルのプロパティ間の対応を示します。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] のプロパティ アクセサー|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のプロパティ ID|解説|  
|------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|--------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> または <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|両方とも存在する場合は `AccessKeyProperty` が優先されます。|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>|``|  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|役割とコントロール型のマッピングについては、前の表を参照してください。|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=fullName><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=fullName>|ValuePattern または RangeValuePattern をサポートするコントロール型でのみ有効です。 MSAA 動作との一貫性を保つために、RangeValue 値は 0 ～ 100 に正規化されます。 Value 項目は文字列を使用します。|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ではサポートされていません。|`accDescription` に関する明確な仕様が MSAA 内に存在しなかったので、このプロパティに格納される情報はプロバイダーによって異なります。|  
|`get_accHelpTopic`|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ではサポートされていません。||  
  
 次の表に、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティと [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] の状態定数との対応を示します。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] の状態|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティ|状態の変更をトリガーする|  
|---------------------------------------------------------------------|---------------------------------------------------------------------------------|------------------|  
|STATE\_SYSTEM\_CHECKED|チェック ボックスの場合、<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> オプション ボタンの場合、<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Y|  
|STATE\_SYSTEM\_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> \= <xref:System.Windows.Automation.ExpandCollapseState>|Y|  
|STATE\_SYSTEM\_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> \= <xref:System.Windows.Automation.ExpandCollapseState> または <xref:System.Windows.Automation.ExpandCollapseState>|Y|  
|STATE\_SYSTEM\_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE\_SYSTEM\_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE\_SYSTEM\_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> \(メニュー項目の場合\)|N|  
|STATE\_SYSTEM\_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> \= True かつ <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> の場合に <xref:System.Windows.Automation.NoClickablePointException> が発生|N|  
|STATE\_SYSTEM\_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> \=<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE\_SYSTEM\_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> \= <xref:System.Windows.Automation.ToggleState>|N|  
|STATE\_SYSTEM\_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE\_SYSTEM\_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE\_SYSTEM\_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> \= True|N|  
|STATE\_SYSTEM\_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE\_SYSTEM\_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=fullName> および <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=fullName>|N|  
|STATE\_SYSTEM\_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> がサポートされています|N|  
|STATE\_SYSTEM\_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE\_SYSTEM\_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE\_SYSTEM\_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Y|  
  
 次は、ほとんどの [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] コントロール サーバーで実装されていなかったか、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] に対応するものがない状態を示します。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] の状態|コメント|  
|---------------------------------------------------------------------|----------|  
|STATE\_SYSTEM\_BUSY|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では使用できません|  
|STATE\_SYSTEM\_DEFAULT|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では使用できません|  
|STATE\_SYSTEM\_ANIMATED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では使用できません|  
|STATE\_SYSTEM\_EXTSELECTABLE|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] サーバーで広範に実装されていません|  
|STATE\_SYSTEM\_MARQUEED|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] サーバーで広範に実装されていません|  
|STATE\_SYSTEM\_SELFVOICING|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] サーバーで広範に実装されていません|  
|STATE\_SYSTEM\_TRAVERSED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では使用できません|  
|STATE\_SYSTEM\_ALERT\_HIGH|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] サーバーで広範に実装されていません|  
|STATE\_SYSTEM\_ALERT\_MEDIUM|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] サーバーで広範に実装されていません|  
|STATE\_SYSTEM\_ALERT\_LOW|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] サーバーで広範に実装されていません|  
|STATE\_SYSTEM\_FLOATING|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] サーバーで広範に実装されていません|  
|STATE\_SYSTEM\_HOTTRACKED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では使用できません|  
|STATE\_SYSTEM\_PRESSED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では使用できません|  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のプロパティ識別子の完全な一覧については、「[UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)」を参照してください。  
  
<a name="uiautomation_events_compare"></a>   
## イベント  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のイベント機構は、[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] とは異なり、Windows のイベント ルーティング \(ウィンドウ ハンドルと密接に関連する\) に依存せず、クライアント アプリケーションでフックを設定する必要もありません。 イベントのサブスクリプションは、特定のイベントに対してだけでなく、ツリーの特定の部分を対象とするように細かく調整できます。 プロバイダーも、リッスンされているイベントを追跡して、イベントの生成を細かく調整できます。  
  
 イベントを生成した要素をクライアントで取得することも簡単です。このような要素は、イベント コールバックに直接渡されるからです。 クライアントがイベントをサブスクライブしているときにキャッシュ要求がアクティブであった場合は、自動的に要素のプロパティがプリフェッチされます。  
  
 次の表に、[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] の WinEvent と [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のイベントとの対応を示します。  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のイベント識別子|  
|--------------|------------------------------------------------------------------------------------|  
|EVENT\_OBJECT\_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> プロパティの変更|  
|EVENT\_OBJECT\_CONTENTSCROLLED|関連付けられたスクロール バーにおける <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> または <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> プロパティの変更|  
|EVENT\_OBJECT\_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_DEFACTIONCHANGE|同等の機能がありません|  
|EVENT\_OBJECT\_DESCRIPTIONCHANGE|まったく同等の項目はありません \(おそらく <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> または <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> プロパティの変更\)|  
|EVENT\_OBJECT\_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT\_OBJECT\_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> の変更|  
|EVENT\_OBJECT\_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> プロパティの変更|  
|EVENT\_OBJECT\_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> プロパティの変更|  
|EVENT\_OBJECT\_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_REORDER|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] での使用は一貫していません。 直接対応するイベントが [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では定義されていません。|  
|EVENT\_OBJECT\_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT\_OBJECT\_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT\_OBJECT\_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT\_OBJECT\_SELECTIONWITHIN|同等の機能がありません|  
|EVENT\_OBJECT\_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_STATECHANGE|さまざまなプロパティ変更イベント|  
|EVENT\_OBJECT\_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=fullName> および <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=fullName> の変更|  
|EVENT\_SYSTEM\_ALERT|同等の機能がありません|  
|EVENT\_SYSTEM\_CAPTUREEND|同等の機能がありません|  
|EVENT\_SYSTEM\_CAPTURESTART|同等の機能がありません|  
|EVENT\_SYSTEM\_CONTEXTHELPEND|同等の機能がありません|  
|EVENT\_SYSTEM\_CONTEXTHELPSTART|同等の機能がありません|  
|EVENT\_SYSTEM\_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT\_SYSTEM\_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT\_SYSTEM\_DRAGDROPEND|同等の機能がありません|  
|EVENT\_SYSTEM\_DRAGDROPSTART|同等の機能がありません|  
|EVENT\_SYSTEM\_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT\_SYSTEM\_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT\_SYSTEM\_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT\_SYSTEM\_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT\_SYSTEM\_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT\_SYSTEM\_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> プロパティの変更|  
|EVENT\_SYSTEM\_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> プロパティの変更|  
|EVENT\_SYSTEM\_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> プロパティの変更|  
|EVENT\_SYSTEM\_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> プロパティの変更|  
|EVENT\_SYSTEM\_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> または <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> プロパティの変更|  
|EVENT\_SYSTEM\_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> または <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> プロパティの変更|  
|EVENT\_SYSTEM\_SOUND|同等の機能がありません|  
|EVENT\_SYSTEM\_SWITCHEND|同等の項目はありませんが、新しいアプリケーションがフォーカスを受け取ったことは <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> イベントによって通知されます。|  
|EVENT\_SYSTEM\_SWITCHSTART|同等の機能がありません|  
|同等の機能がありません|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty> プロパティの変更|  
|同等の機能がありません|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty> プロパティの変更|  
|同等の機能がありません|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty> プロパティの変更|  
|同等の機能がありません|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> プロパティの変更|  
|同等の機能がありません|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> プロパティの変更|  
|同等の機能がありません|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty> プロパティの変更|  
|同等の機能がありません|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty> プロパティの変更|  
|同等の機能がありません|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty> プロパティの変更|  
|同等の機能がありません|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> プロパティの変更|  
|同等の機能がありません|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent> イベント|  
|同等の機能がありません|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## セキュリティ  
 `IAccessible` をカスタマイズするシナリオでは、基本 `IAccessible` をラップしてからこれに対する呼び出しを行うという要件が生じることがあります。 このことは、セキュリティに影響を及ぼします。部分信頼コンポーネントにコード パスを中継させてはならないからです。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] モデルでは、プロバイダーが他のプロバイダー コードを呼び出す必要がありません。 必要な集約はすべて [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コア サービスが行います。  
  
## 参照  
 [UI Automation Fundamentals](../../../docs/framework/ui-automation/index.md)