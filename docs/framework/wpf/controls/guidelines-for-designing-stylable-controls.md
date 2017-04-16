---
title: "スタイルの設定が可能なコントロールを設計するためのガイドライン | Microsoft Docs"
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
  - "コントロール, スタイル設定 (デザインの)"
  - "スタイル設定 (コントロールのデザインの)"
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# スタイルの設定が可能なコントロールを設計するためのガイドライン
このドキュメントでは、スタイルおよびテンプレートを容易に設定できるコントロールを設計する際に考慮する一連のベスト プラクティスについて説明します。  このベスト プラクティスは、組み込みの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール セット用のテーマ コントロール スタイルでの作業の際に、多くの試行錯誤を通じて得られたものです。  スタイルの設定の成功には、スタイルそのものと同様に、優れた設計のオブジェクト モデルの機能が重要であることがわかりました。  このドキュメントは、スタイルの作成者ではなくコントロールの作成者を対象読者として想定しています。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Terminology"></a>   
## 用語  
 "スタイルとテンプレート" では、コントロールの作成者が、コントロールの視覚的な側面をコントロールのスタイルとテンプレートに任せるためのテクノロジ スイートについて説明しています。  このテクノロジ スイートには次のものが含まれます。  
  
-   スタイル \(プロパティの setter、トリガー、およびストーリーボードを含む\)。  
  
-   リソース。  
  
-   コントロール テンプレート。  
  
-   データ テンプレート。  
  
 スタイルとテンプレートの概要については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## 開始する前に : コントロールの理解  
 ガイドラインに進む前に、コントロールの一般的な使用方法を把握し、定義しておくことが重要です。  スタイル設定の一連の方法は、統制がとれていない状態で公開されていることがよくあります。  多くのアプリケーションや開発者に広く使用される目的で作成されるコントロールでは、スタイルの使用によってコントロールの外観が大きく変更される可能性があるという問題が生じます。  実際に、スタイルの設定されたコントロールが、コントロールの作成者の意図したものと少しも似ていない場合があります。  スタイルがもたらす柔軟性は基本的に制限がないため、一般的な使用方法という概念を使用して、決定の際に役立てることができます。  
  
 コントロールの一般的な使用方法を理解するためには、コントロールの価値命題について考えることをお勧めします。  つまり、テーブルに対して自分のコントロールが提供できて他のコントロールには提供できない機能を明らかにします。  一般的な使用方法に含まれるのは、特定の外観ではなく、コントロールの原理と、その使用に関する妥当な期待です。  これを理解することで、一般的な事例におけるコントロールの構成モデルおよびスタイルで定義される動作をある程度仮定できるようになります。  たとえば <xref:System.Windows.Controls.ComboBox> の場合は、一般的な使用方法を理解することで、特定の <xref:System.Windows.Controls.ComboBox> の角が丸いかどうかはわからなくても、<xref:System.Windows.Controls.ComboBox> におそらくポップアップ ウィンドウやその開閉を切り替える方法が必要になることはわかります。  
  
<a name="General_Guidelines"></a>   
## 一般的なガイドライン  
  
-   **テンプレート コントラクトは厳密に適用しないようにします。**コントロールのテンプレート コントラクトは、コントロールが正しく機能するために必要とされる、または期待される要素、コマンド、バインディング、トリガー、あるいはプロパティ設定で構成されます。  
  
    -   コントラクトはできる限り最小化してください。  
  
    -   デザインを行うときは、デザイン時 \(つまりデザイン ツールを使用するとき\) のコントロール テンプレートの状態は一般に不完全であることを予期しておいてください。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は "作成中" の状態のインフラストラクチャを提供しないため、そのような状態になり得るという予測の下にコントロールをビルドする必要があります。  
  
    -   テンプレート コントラクトの側面に従っていなくても、例外はスローしないでください。  これに従って、パネルの子が多すぎたり少なすぎたりしても、そのパネルから例外をスローしないようにする必要があります。  
  
-   **周辺機能はテンプレート ヘルパー要素に組み入れます。**各コントロールは、そのコア機能と真の価値命題に的を絞り、コントロールの一般的な使用方法によって定義する必要があります。  そのためには、テンプレート内のコンポジション要素とヘルパー要素を使用して、周辺動作と視覚化、つまりコントロールのコア機能に影響しない動作と視覚化を実現します。  ヘルパー要素は、3 つのカテゴリに分類されます。  
  
    -   **Standalone** ヘルパー要素は、パブリックで再利用可能なコントロールまたはプリミティブで、テンプレート内では "匿名で" 使用されます。つまり、ヘルパー要素とスタイルが設定されたコントロールは、相手を認識しません。  技術的には、どの要素も匿名型にすることができますが、この文脈でのこの用語は、対象のシナリオを可能にする特殊な機能をカプセル化する型を表しています。  
  
    -   **Type\-based** ヘルパー要素は、特殊な機能をカプセル化する新しい型です。  通常この要素は、一般的なコントロールやプリミティブよりも狭い範囲の機能で設計されます。  Standalone ヘルパー要素とは異なり、Type\-based ヘルパー要素は、使用されているコンテキストを認識し、通常は、それらの要素が属しているテンプレートを持つコントロールとデータを共有する必要があります。  
  
    -   **Named** ヘルパー要素は、コントロールがそのテンプレート内で名前で検出する一般的なコントロールまたはプリミティブです。これらの要素にはテンプレート内で既知の名前が割り当てられるため、コントロールはその要素を検出し、プログラムを通じて対話できます。  特定の名前を持つ要素はテンプレート内に 1 つだけ存在できます。  
  
     現在コントロール スタイルが採用しているヘルパー要素を次の表に示します \(これはすべてを網羅した一覧ではありません\)。  
  
    |要素|種類|使用するコントロール|  
    |--------|--------|----------------|  
    |<xref:System.Windows.Controls.ContentPresenter>|Type\-based|<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.CheckBox>、<xref:System.Windows.Controls.RadioButton>、<xref:System.Windows.Controls.Frame> など \(いずれも <xref:System.Windows.Controls.ContentControl> 型\)|  
    |<xref:System.Windows.Controls.ItemsPresenter>|Type\-based|<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.Menu> など \(いずれも <xref:System.Windows.Controls.ItemsControl> 型\)|  
    |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Named|<xref:System.Windows.Controls.ToolBar>|  
    |<xref:System.Windows.Controls.Primitives.Popup>|Standalone|<xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ToolBar>、<xref:System.Windows.Controls.Menu>、<xref:System.Windows.Controls.ToolTip> など|  
    |<xref:System.Windows.Controls.Primitives.RepeatButton>|Named|<xref:System.Windows.Controls.Slider>、<xref:System.Windows.Controls.Primitives.ScrollBar> など|  
    |<xref:System.Windows.Controls.Primitives.ScrollBar>|Named|<xref:System.Windows.Controls.ScrollViewer>|  
    |<xref:System.Windows.Controls.ScrollViewer>|Standalone|<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.Menu>、<xref:System.Windows.Controls.Frame> など|  
    |<xref:System.Windows.Controls.Primitives.TabPanel>|Standalone|<xref:System.Windows.Controls.TabControl>|  
    |<xref:System.Windows.Controls.TextBox>|Named|<xref:System.Windows.Controls.ComboBox>|  
    |<xref:System.Windows.Controls.Primitives.TickBar>|Type\-based|<xref:System.Windows.Controls.Slider>|  
  
-   **ヘルパー要素で必要となるユーザー指定のバインディングまたはプロパティ設定は最小限に抑えます。** 一般に、ヘルパー要素がコントロール テンプレート内で正しく機能するためには、一定のバインディングまたはプロパティ設定が必要となります。  これらの設定は、できる限りヘルパー要素と template 宣言されたコントロールで設定する必要があります。  プロパティの設定やバインディングの確立の際には、ユーザーが設定した値をオーバーライドしないように注意してください。  具体的なベスト プラクティスは次のとおりです。  
  
    -   Named ヘルパー要素は親によって識別されるようにします。また、親がこのヘルパー要素に対して必要なすべての設定を設定するようにします。  
  
    -   Type\-based ヘルパー要素は、必要なすべての設定を直接それ自身に対して設定するようにします。  そのためには、ヘルパー要素が、その要素が使用されている情報コンテキストを照会する必要があります。これには、その `TemplatedParent` \(ヘルパー要素が使用されているテンプレートのコントロール型\) も含まれます。  たとえば、<xref:System.Windows.Controls.ContentPresenter> は、<xref:System.Windows.Controls.ContentControl> 派生型で使用されるときに、自動的にその `TemplatedParent` の `Content` プロパティをその <xref:System.Windows.Controls.ContentPresenter.Content%2A> プロパティにバインドします。  
  
    -   Standalone ヘルパー要素は上記の方法で最適化できません。これは、本質的にヘルパー要素と親が互いを認識しないためです。  
  
-   **Name プロパティを使用してテンプレート内の要素にフラグを設定します。** プログラムから要素にアクセスするためにスタイル内で要素を検索する必要のあるコントロールは、`Name` プロパティと `FindName` パラダイムを使用してその処理を行う必要があります。  要素が見つからなかった場合、コントロールは例外をスローするのではなく、その要素を必要としていた機能を通知することなく正常に無効にする必要があります。  
  
-   **スタイルでコントロールの状態と動作を表すためのベスト プラクティスに従います。**次に示すのは、スタイルでコントロールの状態の変更と動作を表すためのベスト プラクティスを順序付けた一覧です。  自分のシナリオに合うリスト内の最初の項目を使用してください。  
  
    1.  プロパティのバインディング。  たとえば、<xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=fullName> と <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=fullName> のバインディングがあります。  
  
    2.  トリガーされるプロパティの変更またはプロパティ アニメーション。  たとえば、<xref:System.Windows.Controls.Button> のホバー状態があります。  
  
    3.  コマンド。  たとえば、<xref:System.Windows.Controls.Primitives.ScrollBar> の <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand> や <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> があります。  
  
    4.  Standalone ヘルパー要素。  たとえば、<xref:System.Windows.Controls.TabControl> の <xref:System.Windows.Controls.Primitives.TabPanel> があります。  
  
    5.  Type\-based ヘルパー要素。  たとえば、<xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.ContentPresenter> や <xref:System.Windows.Controls.Slider> の <xref:System.Windows.Controls.Primitives.TickBar> があります。  
  
    6.  Named ヘルパー要素。  たとえば、<xref:System.Windows.Controls.ComboBox> の <xref:System.Windows.Controls.TextBox> があります。  
  
    7.  Named ヘルパー要素からバブリングされるイベント。  スタイル要素からバブリングされたイベントをリッスンする場合は、イベントを生成する要素を一意に識別できる必要があります。  たとえば、<xref:System.Windows.Controls.ToolBar> の <xref:System.Windows.Controls.Primitives.Thumb> があります。  
  
    8.  カスタムの `OnRender` 動作。  たとえば、<xref:System.Windows.Controls.Button> の <xref:Microsoft.Windows.Themes.ButtonChrome> があります。  
  
-   **スタイル トリガー \(テンプレート トリガーとは対照的に\) を多用しないようにします。** テンプレート内の要素のプロパティに影響するトリガーは、テンプレート内で宣言する必要があります。  コントロールのプロパティに影響するトリガー \(`TargetName` なし\) は、テンプレート変更時にトリガーの破棄も必要である場合を除いて、スタイルで宣言できます。  
  
-   **既存のスタイル パターンとの一貫性を維持します。**多くの場合、問題には複数の解決方法があります。  既存のコントロール スタイル パターンを認識し、できればそれらのパターンとの一貫性を維持してください。  特に、同じ基本型から派生したコントロールの場合 \(<xref:System.Windows.Controls.ContentControl>、<xref:System.Windows.Controls.ItemsControl>、<xref:System.Windows.Controls.Primitives.RangeBase> など\) はこれが重要になります。  
  
-   **プロパティを公開して、テンプレートを再設定しなくても一般的なカスタマイズ シナリオに対応できるようにします。** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ではプラグ可能なパーツやカスタマイズ可能なパーツがサポートされないため、コントロールのユーザーがカスタマイズを行うには、プロパティを直接設定するか、スタイルを使用してプロパティを設定するかという 2 つの方法しかありません。  この点を考慮すると、通常はテンプレートの再設定が必要になるようなカスタマイズ シナリオのうち、頻繁に使用される優先度の高いシナリオを対象として、限られた数のプロパティを公開するのが適切です。  カスタマイズ シナリオを有効にするタイミングと方法に関するベスト プラクティスを次に示します。  
  
    -   一般性が高いカスタマイズは、コントロールのプロパティとして公開し、テンプレートで使用されるようにします。  
  
    -   まれではないものの一般性が低いカスタマイズは、添付プロパティとして公開し、テンプレートで使用されるようにします。  
  
    -   認識されていてもまれにしか行われないカスタマイズは、テンプレートの再設定を必要としてもかまいません。  
  
<a name="Theme_Considerations"></a>   
## テーマに関する考慮事項  
  
-   **テーマ スタイルは、プロパティのセマンティクスをすべてのテーマで一貫させるようにする必要がありますが、それに対する保証は行わないようにします。** コントロールには、そのドキュメントの一部として、コントロールのプロパティ セマンティクス、つまりコントロールのプロパティの "意味" について説明したドキュメントが必要です。  たとえば、<xref:System.Windows.Controls.ComboBox> コントロールは、<xref:System.Windows.Controls.ComboBox> における <xref:System.Windows.Controls.Control.Background%2A> プロパティの意味を定義する必要があります。  コントロールの既定のスタイルは、このドキュメントに定義されているセマンティクスに、すべてのテーマで従うようにする必要があります。  これに対しコントロールのユーザーは、そのプロパティ セマンティクスがテーマごとに変わる可能性があるので注意する必要があります。  場合によっては、特定のテーマで要求される視覚上の制約によって、指定されたプロパティを表現できないこともあります   \(たとえば、クラシック テーマには、多くのコントロールで `Thickness` を適用できる一重罫線が使用されません\)。  
  
-   **テーマ スタイルのトリガー セマンティクスは、すべてのテーマで一貫させる必要はありません。** コントロール スタイルがトリガーまたはアニメーションを通して公開する動作は、テーマごとに異なっていてもかまいません。  コントロールのユーザーは、コントロールが特定の動作を実現するためにすべてのテーマで同じ機構を採用するとは限らないので注意をする必要があります。  たとえば、あるテーマがマウス ポインターを上に置いた場合の動作を表現するためにアニメーションを使用する一方で、別のテーマはトリガーを使用する可能性があります。  これにより、カスタマイズされたコントロールでの動作の保持に一貫性がなくなる場合があります   \(たとえば、コントロールの選択状態がトリガーを使用して表現されている場合は、Background プロパティを変更してもその状態には影響しません。  一方、選択状態がアニメーションを使用して実装されている場合に Background プロパティを変更すると、アニメーションが修復できないほど破壊され、状態の遷移が不可能になるおそれがあります\)。  
  
-   **テーマ スタイルでは、"レイアウト" セマンティクスをすべてのテーマで一貫させる必要はありません。** たとえば、コントロールの占有するサイズがすべてのテーマで同じになることを既定のスタイルで保証する必要はありません。あるいは、コントロールのコンテンツの余白やパディングがすべてのテーマで同じになることを保証する必要もありません。  
  
## 参照  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)