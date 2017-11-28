---
title: "XAML リソース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1f9d0ff535d0784343b36d0b2df48b123ff3beef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-resources"></a>XAML リソース
リソースは、アプリケーションで別の場所で再利用可能なオブジェクトです。 リソースの例には、ブラシとスタイルが含まれます。 この概要は、リソースを使用する方法を説明[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。 作成してコードを使用して、またはコードの間で同じ意味でリソースにアクセスし、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。 詳細については、次を参照してください。[リソースやコード](../../../../docs/framework/wpf/advanced/resources-and-code.md)です。  
  
> [!NOTE]
>  このトピックで説明されているリソース ファイルは、リソース ファイルの記載と異なる[WPF アプリケーションのリソース、コンテンツ、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)しで説明されている埋め込みまたはリンクされたリソースとは異なる[アプリケーションのリソース (.NET) の管理](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e)です。  
  
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>XAML でリソースの使用  
 次の例では定義、<xref:System.Windows.Media.SolidColorBrush>ページのルート要素は、上のリソースとして。 例では、リソースを参照しなどいくつかの子要素のプロパティを設定するため、 <xref:System.Windows.Shapes.Ellipse>、 <xref:System.Windows.Controls.TextBlock>、および<xref:System.Windows.Controls.Button>です。  
  
 [!code-xaml[FEResourceSH_snip#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 フレームワーク レベルのすべての要素 (<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>) が、<xref:System.Windows.FrameworkElement.Resources%2A>リソースを含むプロパティのプロパティ (として、 <xref:System.Windows.ResourceDictionary>) リソースを定義します。 任意の要素では、リソースを定義できます。 ただし、リソースがであるルート要素で定義された最もよく<xref:System.Windows.Controls.Page>の例です。  
  
 リソース ディクショナリ内の各リソースは、一意キーを持つ必要があります。 を通じて一意のキーを割り当てるマークアップでリソースを定義するときに、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)です。 通常、キーは、文字列です。ただし、設定することできますも他のオブジェクトの種類に適切なマークアップ拡張機能を使用して、します。 リソースの文字列以外のキーがで特定の機能領域で使用される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]スタイル、コンポーネントのリソース、およびデータのスタイル処理のです。  
  
 リソースを定義した後は、たとえば、キー名を指定するリソースのマークアップ拡張構文を使用してプロパティ値を使用するリソースを参照できます。  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 前の例では、ときに、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローダーが、値を処理`{StaticResource MyBrush}`の<xref:System.Windows.Controls.Control.Background%2A>プロパティを<xref:System.Windows.Controls.Button>、リソースの検索ロジックをリソース ディクショナリでチェック最初、<xref:System.Windows.Controls.Button>要素。 場合<xref:System.Windows.Controls.Button>リソース キーの定義がない`MyBrush`(そうでない以外の場合は、リソース コレクションが空)、参照は、次の親要素をチェック<xref:System.Windows.Controls.Button>、これは<xref:System.Windows.Controls.Page>します。 したがってでリソースを定義するときに、 <xref:System.Windows.Controls.Page> 、ルート要素の論理ツリー内のすべての要素、<xref:System.Windows.Controls.Page>アクセスでき、および任意のプロパティの値の設定を受け入れるため、同じリソースを再利用することができます、<xref:System.Type>をリソース表します。 前の例で、同じ`MyBrush`リソースは、2 つの異なるプロパティを設定:<xref:System.Windows.Controls.Control.Background%2A>の<xref:System.Windows.Controls.Button>、および<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>です。  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>静的および動的なリソース  
 リソースは、静的リソースまたは動的なリソースのいずれかとして参照することができます。 これは、いずれかを使用することで、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)または[DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)します。 マークアップ拡張機能の機能は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性の文字列を処理し、対象のオブジェクトを返すマークアップ拡張機能のことでオブジェクト参照を指定するという、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローダー。 マークアップ拡張機能の動作の詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
 マークアップ拡張機能を使用する場合は、その特定のマークアップ拡張機能で処理される文字列形式の 1 つまたは複数のパラメーターではなく、設定されるプロパティのコンテキストで評価される通常提供します。 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)すべての利用可能なリソース ディクショナリ内でそのキーの値の検索キーを処理します。 これは、読み込みプロセスを静的リソース参照を受け取るプロパティの値を割り当てる必要がある場合に、ポイントの読み込み中に発生します。 [DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)代わりにプロセス式、およびその式を作成して、キーが評価されていないアプリケーションが実際に実行されるまで、どの時に式が評価され、値を提供します。  
  
 次の考慮事項のリソースを参照するときに、静的リソース参照または動的リソース参照を使用するかどうかに影響を与えます。  
  
-   アプリケーションのリソースを作成する方法の全体的なデザイン (アプリケーションでは、ページごとに失われた[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、リソースのみのアセンブリで)。  
  
-   アプリケーションの機能: アプリケーションの要件の一部をリアルタイムでリソースを更新しますか?  
  
-   リソース参照の種類のそれぞれの検索動作します。  
  
-   特定のプロパティまたはリソースの種類、およびそれらの型のネイティブの動作です。  
  
### <a name="static-resources"></a>静的なリソース  
 静的リソースは、次の状況に最適な作業を参照します。  
  
-   アプリケーションの設計は、辞書で集中そのページにリソースやアプリケーション レベルのリソースのほぼすべてします。 静的リソース参照は、ページの再読み込みなどの実行時の動作に基づいて再評価されないでき、したがってがありますのでは、リソースごとに必要ない場合は、多数の動的リソース参照を回避するパフォーマンスが向上し、アプリケーションの設計。  
  
-   含まれていないプロパティの値を設定する、<xref:System.Windows.DependencyObject>または<xref:System.Windows.Freezable>です。  
  
-   DLL にコンパイルし、アプリケーションの一部としてパッケージ化またはアプリケーション間で共有されるリソース ディクショナリを作成します。  
  
-   カスタム コントロール用のテーマを作成して、テーマ内で使用されているリソースを定義します。 この場合、通常しないようにする動的リソース参照の検索動作を代わりに、静的リソース参照動作検索結果は予測可能で自己完結型のテーマにできるようにします。 動的リソース参照、でもはテーマでの参照のままが、実行時まで評価し、テーマが適用されている、いくつかのローカルの要素を参照すると、テーマ、キーを再定義し、ローカルの要素を前に分類されます可能性があります。されたテーマへ自体の参照にします。 その場合は、テーマに期待どおりに動作しません。  
  
-   リソースを使用すると、多数の依存関係プロパティを設定しています。 依存関係プロパティでは、有効な値キャッシュをプロパティ システムで有効であるため、依存関係プロパティが reevaluated 式を確認する必要はありませんし、返すことができますの読み込み時に評価される依存関係プロパティの値を指定する場合、最後の有効な値です。 この方法は、パフォーマンスが向上します。  
  
-   すべてのコンシューマーの基になるリソースを変更するかを使用して、各コンシューマーの書き込み可能な個別のインスタンスを管理する、 [x: 共有属性](../../../../docs/framework/xaml-services/x-shared-attribute.md)です。  
  
#### <a name="static-resource-lookup-behavior"></a>静的リソースの検索の動作  
  
1.  照合プロセスでは、プロパティを設定する要素で定義されているリソース ディクショナリ内で要求されたキーを確認します。  
  
2.  照合プロセスは、親要素とそのリソース ディクショナリにし、論理ツリーを上方向を走査します。 これは、ルート要素に到達するまでは続行されます。  
  
3.  次に、アプリケーションのリソースがチェックされます。 アプリケーション リソースによって定義されているリソース ディクショナリ内では、<xref:System.Windows.Application>オブジェクトに対して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。  
  
 リソース ディクショナリ内から静的リソース参照では、既に定義されている構文的にリソース参照の前にリソースを参照する必要があります。 静的リソース参照では、前方参照を解決できません。 このため、静的リソース参照を使用する場合は、する必要があります構造を設計する、リソース ディクショナリ各リソース ディクショナリの先頭に近いリソースによって使用される予定のリソースを定義するようです。  
  
 静的リソース参照は、テーマ、またはシステム リソースを拡張できますが、ためにのみ、これはサポート、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローダーによって要求が遅延します。 ページの読み込み時に実行時のテーマは、アプリケーションに正しく適用できるように、遅延する必要があります。 ただし、静的リソースにのみ存在テーマまたはリソースが推奨されないシステムとして認識されているキーへの参照します。 これは、テーマがリアルタイムでユーザーが変更された場合、このような参照が再評価されないためです。 テーマまたはシステム リソースを要求するときに、動的なリソースの参照はより信頼性の高いです。 テーマ要素自体は、別のリソースを要求するときは例外です。 これらの参照は、前述の理由で静的リソース参照をする必要があります。  
  
 静的リソース参照が見つからない場合は、例外動作によって異なります。 リソースが延期された場合は、実行時に例外が発生します。 リソースが遅延されなかった場合は、読み込み時に例外が発生します。  
  
### <a name="dynamic-resources"></a>動的リソース  
 次の状況に最適な動的なリソース。  
  
-   リソースの値は、実行時まで不明な条件によって異なります。 これには、システム リソース、または他のユーザー設定可能なリソースが含まれます。 によって公開されていると、システムのプロパティを参照する setter 値を作成するなど、 <xref:System.Windows.SystemColors>、 <xref:System.Windows.SystemFonts>、または<xref:System.Windows.SystemParameters>です。 ユーザーとオペレーティング システムのランタイム環境から最終的にくるために、これらの値は動的です。 ページ レベル リソースへのアクセス、変更のキャプチャをする必要がありますも、変更可能なアプリケーション レベルのテーマを設定することもできます。  
  
-   作成またはカスタム コントロール用のテーマのスタイルを参照しています。  
  
-   内容を調整する場合、<xref:System.Windows.ResourceDictionary>アプリケーションの有効期間中にします。  
  
-   前方参照が必要ありますの相互依存性を持つ構造の複雑なリソースがあります。 静的リソース参照は前方参照をサポートしていませんが、動的リソース参照をサポートしてそれらのリソースが、実行時まで評価する必要がないため、前方参照されないため、関連する概念です。  
  
-   コンパイルまたはワーキング セットの観点から大規模なであるリソースを参照しているし、ページが読み込まれるときにすぐに、リソースを使用しない可能性があります。 静的リソース参照は常にから読み込む[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページが読み込まれた場合です。 ただし、動的なリソースの参照まで読み込まれませんが、実際に使用します。  
  
-   Set アクセス操作子の値が元の場所のテーマや他のユーザー設定の影響を受けるその他の値、スタイルを作成します。  
  
-   リソースを適用する場合がある親を再指定論理ツリーのアプリケーションの有効期間中に要素。 可能性がある親を変更すると、リソースの検索スコープを変更、ようにする場合は、リソースが再評価されますこの要素の新しいスコープに基づいて、常に使用して動的リソース参照します。  
  
#### <a name="dynamic-resource-lookup-behavior"></a>動的なリソースの検索の動作  
 呼び出す場合は動的なリソースの参照用リソースの検索の動作は、コード内の検索の動作に対応して<xref:System.Windows.FrameworkElement.FindResource%2A>または<xref:System.Windows.FrameworkElement.SetResourceReference%2A>です。  
  
1.  照合プロセスでは、プロパティを設定する要素で定義されているリソース ディクショナリ内で要求されたキーを確認します。  
  
    -   要素が定義されている場合、<xref:System.Windows.FrameworkElement.Style%2A>プロパティ、<xref:System.Windows.Style.Resources%2A>ディクショナリ内で、<xref:System.Windows.Style>がオンになっています。  
  
    -   要素が定義されている場合、<xref:System.Windows.Controls.Control.Template%2A>プロパティ、<xref:System.Windows.FrameworkTemplate.Resources%2A>ディクショナリ内で、<xref:System.Windows.FrameworkTemplate>がオンになっています。  
  
2.  照合プロセスは、親要素とそのリソース ディクショナリにし、論理ツリーを上方向を走査します。 これは、ルート要素に到達するまでは続行されます。  
  
3.  次に、アプリケーションのリソースがチェックされます。 アプリケーション リソースによって定義されているリソース ディクショナリ内では、<xref:System.Windows.Application>オブジェクトに対して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。  
  
4.  現在アクティブなテーマのテーマ リソース ディクショナリがチェックされます。 実行時に、テーマが変更された場合、値が再評価されます。  
  
5.  システム リソースがチェックされます。  
  
 (存在する場合)、例外の動作が異なります。  
  
-   リソースが要求した場合、<xref:System.Windows.FrameworkElement.FindResource%2A>呼び出す、または見つかりませんでした、例外が発生します。  
  
-   リソースが要求した場合、<xref:System.Windows.FrameworkElement.TryFindResource%2A>呼び出す、または見つかりませんでした、例外は発生しませんが、返される値は`null`します。 設定されるプロパティを受け付けない場合`null`、詳細な例外が発生することも可能にし、(これは設定されている個々 のプロパティに依存)。  
  
-   動的なリソースの参照がリソースを要求したかどうかは[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、およびでしたが見つかりません。 し、動作は、[全般] プロパティ システムによって異なりますが、全般的な動作はようプロパティの設定の操作が発生していないリソースが存在するレベル。 インスタンスに背景を設定しようとする場合を評価できませんでしたリソースを使用して、個々 のボタン要素値の設定はありません、結果が、プロパティのシステムと値の優先順位の他の参加者から有効な値が決まることができます。 たとえば、バック グラウンド値が、ローカルに定義されたボタンのスタイルとテーマ スタイルから決まる場合があります。 テーマ スタイルで定義されていないプロパティの場合は、障害が発生したリソースの評価後に有効な値は、プロパティ メタデータの既定値から取得可能性があります。  
  
#### <a name="restrictions"></a>制約  
 動的リソース参照では、いくつか重要な制限があります。 次の少なくとも 1 つがあります。  
  
-   設定されているプロパティのプロパティである必要があります、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>です。 プロパティをバックアップする必要があります、<xref:System.Windows.DependencyProperty>です。  
  
-   内の値は、参照、 <xref:System.Windows.Style><xref:System.Windows.Setter>です。  
  
-   設定されているプロパティのプロパティである必要があります、<xref:System.Windows.Freezable>は、いずれかの値として提供される、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>プロパティ、または<xref:System.Windows.Setter>値。  
  
 プロパティが設定されている必要がありますので、<xref:System.Windows.DependencyProperty>または<xref:System.Windows.Freezable>プロパティ、ほとんどのプロパティの変更に伝達される、UI プロパティ システム プロパティの変更 (動的なリソースが変更された値) が確認されているためです。 ほとんどのコントロールを含める場合は、コントロールの別のレイアウトを強制するロジックを<xref:System.Windows.DependencyProperty>変更とプロパティがレイアウトに影響を与えます。 ただし、必ずしもすべてのプロパティがある、 [DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)それらの値として、UI にリアルタイムで更新するように値を提供する保証はします。 機能を引き続き異なりますだけでなく、プロパティ、またはアプリケーションの論理構造を所有する型によって、プロパティによって異なります。  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>スタイル、Datatemplate、および暗黙的なキー  
 以前が示されているすべての項目、<xref:System.Windows.ResourceDictionary>キーを持っている必要があります。 ただし、必ずしもすべてのリソースが必要となる、明示的な`x:Key`します。 いくつかのオブジェクト型では、別のプロパティの値をキーの値が関連付けられている、リソースとして定義されている場合に暗黙のキーをサポートします。 これは暗黙のキーと呼びます、`x:Key`属性は明示的なキーです。 明示的なキーを指定することによって、暗黙のキーを上書きできます。  
  
 リソースの 1 つの非常に重要なシナリオは、定義する場合、<xref:System.Windows.Style>です。 実際には、<xref:System.Windows.Style>スタイル本質的には、再利用するために、リソース ディクショナリのエントリとしてほぼ常に定義されています。 スタイルの詳細については、次を参照してください。[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)です。  
  
 コントロールのスタイル両方で作成して暗黙のキーで参照します。 コントロールの既定の外観を定義するテーマ スタイルは、この暗黙のキーに依存します。 要求の観点からは、暗黙のキーは、<xref:System.Type>コントロール自体のです。 リソースの定義の観点からは、暗黙のキーは、<xref:System.Windows.Style.TargetType%2A>のスタイル。 そのため場合カスタム コントロールのテーマを作成するには、既存のテーマ スタイルを使用して対話するスタイルを作成するは必要ありませんを指定する、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)を<xref:System.Windows.Style>です。 テーマとスタイルを使用する場合は、スタイルをまったく指定する必要はありません。 たとえば、次のスタイル定義の動作、いなくても、<xref:System.Windows.Style>キーが存在するリソースは表示されません。  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 あるスタイル実際には、キーが: 暗黙のキー `typeof(` <xref:System.Windows.Controls.Button>`)`です。 マークアップを指定できます、<xref:System.Windows.Style.TargetType%2A>という名前の型として直接 (必要に応じて使用することができますか[{X:type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md) 返す、<xref:System.Type>です。  
  
 によって使用される既定のテーマ スタイル メカニズムを通じて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のランタイム スタイルとしてスタイルが適用される、 <xref:System.Windows.Controls.Button>  ページで、場合でも、<xref:System.Windows.Controls.Button>自体は行われませんを指定するその<xref:System.Windows.FrameworkElement.Style%2A>プロパティまたは特定のリソーススタイルへの参照します。 ページで定義されたスタイルがある検索シーケンスで先にテーマのテーマ ディクショナリ スタイルには、同じキーを使用してディクショナリ スタイルよりも前です。 指定することだけ`<Button>Hello</Button>`任意の場所で、ページで定義されたスタイル<xref:System.Windows.Style.TargetType%2A>の`Button`はそのボタンに適用します。 型値と同じスタイルが明示的を入力する場合は、 <xref:System.Windows.Style.TargetType%2A>、わかりやすくするため、マークアップでです省略可能です。  
  
 場合、スタイルの暗黙的なキーは、コントロールに適用されません<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>は`true`(もなお<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>コントロール クラスではなく、明示的に、コントロールのインスタンスのネイティブの動作の一部として設定することがあります)。 また、暗黙的なキーの派生クラスのシナリオをサポートするために、制御する必要がありますオーバーライド<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>(の一部として提供されるすべての既存のコントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]この)。 スタイル、テーマ、およびコントロールのデザインの詳細については、次を参照してください。[のスタイル設定可能なコントロールのデザイン ガイドライン](../../../../docs/framework/wpf/controls/guidelines-for-designing-stylable-controls.md)です。  
  
 <xref:System.Windows.DataTemplate>暗黙のキーがあります。 暗黙のキーを<xref:System.Windows.DataTemplate>は、<xref:System.Windows.DataTemplate.DataType%2A>プロパティの値。 <xref:System.Windows.DataTemplate.DataType%2A>明示的に使用するのではなく、型の名前として指定することも[{X:type…}](../../../../docs/framework/xaml-services/x-type-markup-extension.md). 詳細については、「[データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.ResourceDictionary>  
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [リソースとコード](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [リソースを定義および参照する](../../../../docs/framework/wpf/advanced/how-to-define-and-reference-a-resource.md)  
 [アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [x:Type マークアップ拡張機能](../../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [DynamicResource マークアップ拡張](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
