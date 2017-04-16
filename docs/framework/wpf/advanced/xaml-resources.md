---
title: "XAML リソース | Microsoft Docs"
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
  - "再利用 (リソースを)"
  - "リソースを再利用します。"
  - "再利用 (一般的に定義されるオブジェクトを)"
  - "XAML では、リソースの再利用"
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# XAML リソース
リソースは、アプリケーションでさまざまな場所で再利用可能なオブジェクトです。 リソースの例には、ブラシやスタイルが含まれます。 この概要でのリソースを使用する方法を説明する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。 作成、または同じ意味で、コードを使用して、コードの間でリソースにアクセスして、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。 詳細については、次を参照してください。[リソースとコード](../../../../docs/framework/wpf/advanced/resources-and-code.md)します。  
  
> [!NOTE]
>  このトピックで説明されているリソース ファイルとリソース ファイルに記載するものと異なる場合は[WPF アプリケーションのリソース、コンテンツ、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)で記述されている埋め込みまたはリンクされたリソースとは異なると[を管理するアプリケーションのリソース (.NET)](../Topic/Managing%20Application%20Resources%20\(.NET\).md)します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>XAML でリソースを使用します。  
 次の例、 <xref:System.Windows.Media.SolidColorBrush>ページのルート要素上のリソースとして。 例では、リソースを参照しなどいくつかの子要素のプロパティを設定するため、<xref:System.Windows.Shapes.Ellipse>、 <xref:System.Windows.Controls.TextBlock>、および<xref:System.Windows.Controls.Button>します。  
  
 [!code-xml[FEResourceSH_snip#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 フレームワーク レベルのすべての要素 ( <xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>) が、<xref:System.Windows.FrameworkElement.Resources%2A>リソースを含むプロパティであるプロパティ (として、 <xref:System.Windows.ResourceDictionary>) リソースを定義します。 任意の要素でリソースを定義することができます。 ただし、リソースは、これはルート要素で定義された最も多くの場合、<xref:System.Windows.Controls.Page>の例です。  
  
 リソース ディクショナリ内の各リソースは、一意キーを持つ必要があります。 使って一意のキーを割り当てるマークアップでリソースを定義すると、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)します。 通常、キーは、文字列です。ただしも設定できます、その他のオブジェクトの種類に適切なマークアップ拡張機能を使用しています。 リソースの文字列ではないキーが特定の機能領域内で使用される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]スタイル、コンポーネントのリソース、およびデータのスタイル処理の代表的なものです。  
  
 リソースを定義した後は、たとえば、キー名を指定するリソースのマークアップ拡張構文を使用して、プロパティ値を使用するリソースを参照できます。  
  
 [!code-xml[FEResourceSH_snip#KeyNameUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 前の例でときに、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローダーは、値を処理`{StaticResource MyBrush}`の<xref:System.Windows.Controls.Control.Background%2A>プロパティを<xref:System.Windows.Controls.Button>、リソースの検索ロジック最初をリソース ディクショナリでチェック、 <xref:System.Windows.Controls.Button>要素。 場合<xref:System.Windows.Controls.Button>リソース キーの定義がない`MyBrush`(そうでない、つまり、リソースのコレクションが空)、ルックアップの親要素を次にチェックする<xref:System.Windows.Controls.Button>、これは<xref:System.Windows.Controls.Page>します。 したがってのリソースを定義するとき、<xref:System.Windows.Controls.Page>ルート要素での論理ツリー内のすべての要素、<xref:System.Windows.Controls.Page>アクセスでき、および任意のプロパティの値の設定を受け入れるため、同じリソースを再利用することができます、<xref:System.Type>リソースが表す。 同じ前の例で`MyBrush`リソースは、2 つの異なるプロパティを設定:<xref:System.Windows.Controls.Control.Background%2A>の<xref:System.Windows.Controls.Button>、および<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>します。  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>静的および動的なリソース  
 リソースは、静的リソースまたは動的なリソースのいずれかとして参照することができます。 いずれかを使用して、これは、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)または[DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)です。 マークアップ拡張機能の機能である[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]オブジェクト参照を指定するには、マークアップ拡張が設定されている属性の文字列を処理し、対象のオブジェクトを返すには、機能を持つことでこれによって、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローダー。 マークアップ拡張機能の動作の詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)します。  
  
 マークアップ拡張機能を使用する場合は、その特定のマークアップ拡張機能で処理される文字列形式の&1; つ以上のパラメーターではなく、設定されるプロパティのコンテキストで評価される通常提供します。 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)すべての利用可能なリソース ディクショナリ内でそのキーの値を参照して、キーを処理します。 これは、読み込みプロセスを静的リソース参照を受け取るプロパティの値を割り当てる必要がある場合に、ポイントの読み込み中に発生します。 [DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)代わりにプロセス、式とその式を作成して、キーは残ります評価されていないアプリケーションが実際に実行されるまで、れた時点で、式が評価され、値を提供します。  
  
 リソースを参照するときに次の考慮事項は、静的リソース参照または動的リソース参照を使用するかどうかに影響します。  
  
-   アプリケーションのリソースを作成する方法の全体的なデザイン (アプリケーションでは、ページごとに疎[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、リソースだけのアセンブリに)。  
  
-   アプリケーションの機能: アプリケーションの要件の一部をリアルタイムでリソースを更新中ですか?  
  
-   そのリソースの参照型のそれぞれの検索動作します。  
  
-   特定のプロパティまたはリソースの種類とそれらの型のネイティブの動作です。  
  
### <a name="static-resources"></a>静的リソース  
 静的リソースは、次の状況に最適な作業を参照します。  
  
-   アプリケーションの設計は集中ディクショナリでは、リソースのページへのまたはアプリケーション レベルのリソースのほぼすべてします。 静的リソース参照は、ページの再読み込みなどの実行時の動作に基づいて再評価されないと、したがってするはパフォーマンスが向上するには、リソースとアプリケーションを設計あたり不要と多数の動的リソース参照を回避します。  
  
-   含まれていないプロパティの値を設定する、 <xref:System.Windows.DependencyObject>または<xref:System.Windows.Freezable>します。  
  
-   DLL にコンパイルし、アプリケーションの一部としてパッケージ化またはアプリケーション間で共有されるリソース ディクショナリを作成します。  
  
-   カスタム コントロール用のテーマを作成し、テーマ内で使用されているリソースを定義します。 この場合は、通常たくない動的リソース参照の検索動作は、検索結果は予測可能で自己完結型のテーマにようにに代わりに、静的リソース参照動作が必要です。 動的リソース参照で、テーマでの参照のまま、偶数が、実行時まで評価して、テーマが適用されるときに、いくつかのローカル要素を参照すると、テーマ、キーを再定義し、ローカルの要素が参照では、それ自体は、テーマに以前分類可能性があります。 このような場合、テーマは期待どおりに動作しません。  
  
-   多数の依存関係プロパティを設定するのには、リソースを使用しています。 依存関係プロパティがある値のキャッシュ プロパティ システムで有効化されるので、可能な依存関係プロパティの値を指定する場合、読み込み時に評価される依存関係プロパティ reevaluated 式を確認する必要はありません、最後に有効な値を返すことができます。 この方法は、パフォーマンスが向上します。  
  
-   すべてのコンシューマーの基になるリソースを変更するかを使用して、各コンシューマーの書き込み可能な個別のインスタンスを管理する、 [x: 共有の属性](../../../../docs/framework/xaml-services/x-shared-attribute.md)します。  
  
#### <a name="static-resource-lookup-behavior"></a>静的リソースの検索動作  
  
1.  照合プロセスでは、プロパティを設定する要素によって定義されたリソース ディクショナリ内で要求されたキーを確認します。  
  
2.  検索プロセスは、親要素とそのリソース ディクショナリにし、論理ツリーを上を走査します。 ルート要素に到達するまで繰り返されます。  
  
3.  次に、アプリケーションのリソースがチェックされます。 アプリケーション リソースで定義されているリソース ディクショナリ内では、<xref:System.Windows.Application>のオブジェクト、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。  
  
 リソース ディクショナリ内の静的リソース参照が既に定義されている構文的にリソースの参照の前にリソースを参照する必要があります。 静的リソース参照では、前方参照を解決できません。 このため、静的リソース参照を使用する場合は、必要があります構造を設計する、リソース ディクショナリまたは各リソース ディクショナリの先頭付近にリソースを使用するためのリソースを定義するようです。  
  
 静的リソースの検索には、テーマ、またはシステム リソースを拡張できますが、ためにのみ、これはサポート、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローダーによって要求が遅延します。 ページの読み込み時にランタイムのテーマは、アプリケーションに適切に適用されるよう、遅延する必要があります。 ただし、静的リソース参照にのみ存在テーマまたはシステム リソースをお勧めできないとしているキーです。 これは、テーマがリアルタイムでユーザーが変更された場合、このような参照が再評価されないためです。 テーマやシステム リソースを要求すると、動的リソース参照はより信頼性の高いです。 例外は、テーマ要素自体が他のリソースを要求したときです。 これらの参照は、前述の理由で静的リソース参照をする必要があります。  
  
 静的リソース参照が見つからない場合は、例外動作が異なります。 リソースが延期された場合は、実行時に例外が発生します。 リソースを遅延していない場合は、読み込み時に例外が発生します。  
  
### <a name="dynamic-resources"></a>動的リソース  
 次の状況に最適な動的リソース。  
  
-   リソースの値は、実行時まで不明な条件によって異なります。 これには、システム リソース、または他のユーザー設定可能なリソースが含まれます。 によって公開されていると、システムのプロパティを参照する set アクセス操作子の値を作成するなどの<xref:System.Windows.SystemColors>、 <xref:System.Windows.SystemFonts>、または<xref:System.Windows.SystemParameters>します。 これらの値は、最終的には、ユーザーとオペレーティング システムのランタイム環境から取得されるために本当に動的です。 ページ レベル リソースへのアクセスの変更のキャプチャをする必要がありますも、変更可能なアプリケーション レベルのテーマもあります。  
  
-   作成するか、カスタム コントロールのテーマ スタイルを参照します。  
  
-   内容を調整する、 <xref:System.Windows.ResourceDictionary>アプリケーションの有効期間中にします。  
  
-   前方参照が必要なありますの相互依存性を持つ構造の複雑なリソースがあります。 静的リソース参照は前方参照をサポートしていませんが、動的リソース参照をサポートしてそれらのリソースが実行時まで評価する必要がないのでおり前方参照できないためです、関連する概念です。  
  
-   大規模なコンパイルまたはワーキング セットの観点からは、リソースを参照しているし、ページが読み込まれるときにすぐに、リソースを使用しない可能性があります。 静的リソース参照を常に読み込む[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページが読み込まれたときに、ただし、動的リソース参照まで読み込まれませんが、実際に使用します。  
  
-   Set アクセス操作子の値が元の場所のテーマや他のユーザー設定の影響を受けるその他の値のスタイルを作成します。  
  
-   する親を再指定論理ツリーでアプリケーションの有効期間中に要素には、リソースを適用します。 可能性のあるも、親を変更すると、リソースの検索スコープを変更ので、する場合は、リソースが再評価されますこの要素の新しいスコープに基づいて、常に使用して動的リソース参照します。  
  
#### <a name="dynamic-resource-lookup-behavior"></a>動的リソースの検索動作  
 呼び出した場合動的リソース参照用リソースの検索の動作は、コード内の検索の動作に対応して<xref:System.Windows.FrameworkElement.FindResource%2A>または<xref:System.Windows.FrameworkElement.SetResourceReference%2A>します。  
  
1.  照合プロセスでは、プロパティを設定する要素によって定義されたリソース ディクショナリ内で要求されたキーを確認します。  
  
    -   要素が定義されている場合、<xref:System.Windows.FrameworkElement.Style%2A>プロパティには、<xref:System.Windows.Style.Resources%2A>ディクショナリ内で、<xref:System.Windows.Style>がオンになっています。  
  
    -   要素が定義されている場合、<xref:System.Windows.Controls.Control.Template%2A>プロパティには、<xref:System.Windows.FrameworkTemplate.Resources%2A>ディクショナリ内で、 <xref:System.Windows.FrameworkTemplate>がオンになっています。  
  
2.  検索プロセスは、親要素とそのリソース ディクショナリにし、論理ツリーを上を走査します。 ルート要素に到達するまで繰り返されます。  
  
3.  次に、アプリケーションのリソースがチェックされます。 アプリケーション リソースで定義されているリソース ディクショナリ内では、<xref:System.Windows.Application>のオブジェクト、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。  
  
4.  現在アクティブなテーマのテーマ リソース ディクショナリがチェックされます。 実行時に、テーマが変更された場合、値が再評価されます。  
  
5.  システム リソースがチェックされます。  
  
 (もしあれば) の例外の動作が異なります。  
  
-   リソースが要求した場合、 <xref:System.Windows.FrameworkElement.FindResource%2A>を呼び出すとが見つかりませんでした、例外が発生します。  
  
-   リソースが要求した場合、 <xref:System.Windows.FrameworkElement.TryFindResource%2A>を呼び出すと、され、例外が発生しなかったが、返される値を検出されませんでした`null`します。 設定されるプロパティが受け付けない場合`null`、詳細な例外が発生することも、(これは設定されている個々 のプロパティに依存)。  
  
-   リソースが要求で動的リソース参照したかどうかは[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、およびは見つかりませんでしたし、動作は、[全般] プロパティ システムによって異なりますが、通常の動作は、レベル、リソースが存在するプロパティ設定操作実行されなかったかのようです。 たとえばに背景を設定しようとする場合、評価されないリソースを使用して、各ボタン要素値の設定はありません、結果が、プロパティ システムと値の優先順位の他の参加者から有効な値が決まることができます。 たとえば、バック グラウンドの値がローカルに定義されたボタンのスタイルとテーマ スタイルから決まる場合があります。 テーマ スタイルで定義されていないプロパティの場合は、障害が発生したリソースの評価後に有効な値は、プロパティのメタデータの既定値から取得可能性があります。  
  
#### <a name="restrictions"></a>制限事項  
 動的リソース参照では、いくつか注目すべき制限があります。 次の少なくとも&1; つがあります。  
  
-   設定されるプロパティは、プロパティ、 <xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。 プロパティをバックアップする必要がある、 <xref:System.Windows.DependencyProperty>します。  
  
-   内の値を参照先は、<xref:System.Windows.Style><xref:System.Windows.Setter>します。  
  
-   設定されるプロパティは、プロパティ、 <xref:System.Windows.Freezable>いずれかの値として提供される、 <xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>プロパティ、または<xref:System.Windows.Setter>値。  
  
 プロパティが設定されている必要がありますので、 <xref:System.Windows.DependencyProperty>または<xref:System.Windows.Freezable>プロパティには、ほとんどのプロパティの変更からに伝達する UI プロパティのシステム プロパティの変更 (動的なリソースが変更された値) が確認されているためです。 ほとんどのコントロールが場合に、コントロールの別のレイアウトを強制するロジックを含む、 <xref:System.Windows.DependencyProperty>変更し、プロパティがレイアウトに影響を与えます。 ただし、すべてのプロパティがある、 [DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)値としては、UI にリアルタイムで更新するように値を提供する保証されています。 機能をまだ異なりますによっては、プロパティ、またはアプリケーションの論理構造を所有する型だけでなく、プロパティによって異なります。  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>スタイル、Datatemplate、および暗黙的なキー  
 前に説明したように、すべての項目、 <xref:System.Windows.ResourceDictionary>キーを持っている必要があります。 ただし、いないわけでは、明示的なすべてのリソースがある必要があります`x:Key`します。 いくつかのオブジェクト型では、別のプロパティの値に関連付けられた、キー値をリソースとして定義されている場合、暗黙のキーをサポートします。 一方、暗黙のキーと呼ばれるは、この、`x:Key`属性は、明示的なキーです。 明示的なキーを指定することによって、暗黙のキーを上書きできます。  
  
 リソースの&1; つの非常に重要なシナリオは、定義する場合、<xref:System.Windows.Style>します。 実際には、<xref:System.Windows.Style>スタイルは本質的に再利用するためのものであるため、リソース ディクショナリのエントリとしてはほぼ常に定義します。 スタイルの詳細については、次を参照してください。[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)します。  
  
 コントロールのスタイル両方で作成して、暗黙のキーを使用して参照します。 コントロールの既定の外観を定義するテーマ スタイルは、この暗黙のキーに依存します。 それを要求の観点からは、暗黙のキーは、<xref:System.Type>コントロール自体のです。 リソースを定義するという観点から、暗黙のキーは、 <xref:System.Windows.Style.TargetType%2A>スタイルのです。 そのため、カスタム コントロール用のテーマを作成する場合、既存のテーマ スタイルを使用して対話するスタイルの作成する必要はありませんを指定する、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)その<xref:System.Windows.Style>します。 テーマが適用されたスタイルを使用する場合は任意のスタイルを指定する必要はありません。 たとえば、次のスタイル定義の動作、にもかかわらず、<xref:System.Windows.Style>キーが存在するリソースは表示されません。  
  
 [!code-xml[FEResourceSH_snip#ImplicitStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 あるスタイル実際には、キーが: 暗黙のキー `typeof(`<xref:System.Windows.Controls.Button>`)`します。 マークアップでは、指定することができます、 <xref:System.Windows.Style.TargetType%2A>の種類として直接という名前を (必要に応じて使用することができますか[{X:type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md) 返す、<xref:System.Type>します。  
  
 使用される既定のテーマ スタイルのメカニズムを通じて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、ランタイム スタイルのスタイルを適用する、 <xref:System.Windows.Controls.Button> ページで、場合でも、<xref:System.Windows.Controls.Button>自体を指定しません、<xref:System.Windows.FrameworkElement.Style%2A>プロパティまたはスタイルへの参照を特定のリソースです。 ページで定義されたスタイルについては、テーマ ディクショナリ スタイルには、同じキーを使用してテーマ ディクショナリのスタイルよりも前参照シーケンスの前にあります。 指定することだけ`<Button>Hello</Button>`任意の場所で、ページで定義されているスタイル<xref:System.Windows.Style.TargetType%2A>の`Button`はそのボタンに適用します。 同じ型の値を持つスタイルをキーできますも明示的にする場合は、 <xref:System.Windows.Style.TargetType%2A>、わかりやすくするため、マークアップでは省略可能です。  
  
 場合、スタイルの暗黙的なキーは、コントロールに適用されません<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>は`true`(もなお<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>コントロール クラスではなく明示的に、コントロールのインスタンスのネイティブの動作の一部として設定することがあります)。 また、暗黙的なキーの派生クラスのシナリオをサポートするためにコントロールする必要がありますオーバーライド<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (の一部として提供されるすべての既存のコントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]こう)。 スタイル、テーマ、およびコントロールのデザインの詳細については、次を参照してください。[スタイル設定可能なコントロールをデザインするためのガイドライン](../../../../docs/framework/wpf/controls/guidelines-for-designing-stylable-controls.md)します。  
  
 <xref:System.Windows.DataTemplate>暗黙のキーもあります。 に対して暗黙のキー、 <xref:System.Windows.DataTemplate>は、 <xref:System.Windows.DataTemplate.DataType%2A>プロパティの値。                  <xref:System.Windows.DataTemplate.DataType%2A>が明示的に使用するのではなく、型の名前として指定することも[{X:type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md). 詳細については、「[データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.ResourceDictionary>   
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [リソースとコード](../../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [定義し、リソースを参照](../../../../docs/framework/wpf/advanced/how-to-define-and-reference-a-resource.md)   
 [アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)   
 [X:type マークアップ拡張機能](../../../../docs/framework/xaml-services/x-type-markup-extension.md)   
 [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)   
 [DynamicResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)