---
title: "依存関係プロパティ値の優先順位"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d95cd0545fa4800f159f4e5e0f661cf7bddc6548
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="dependency-property-value-precedence"></a>依存関係プロパティ値の優先順位
<a name="introduction"></a>このトピックでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プロパティ システムの動作が依存関係プロパティの値に与える影響と、システムのさまざまな部分がプロパティの有効な値に適用する優先順位について説明します。  
    
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスの既存の依存関係プロパティのコンシューマーの観点から依存関係プロパティを理解しており、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を読んでいることを前提としています。 このトピックの例について理解するには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] および [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの記述方法について知っておく必要もあります。  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>WPF プロパティ システム  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムは、依存関係プロパティの値をさまざまな要因によって決定し、リアルタイム プロパティの検証や遅延バインディングなどの機能を有効にし、他のプロパティの値の変更を関連プロパティに通知する、強力な手段を提供します。 依存関係プロパティの値の決定に使われる正確な順序とロジックはかなり複雑です。 この順序を知っておくと、不要なプロパティの設定を避けることができ、依存関係プロパティの値を設定または予測しようとしても期待通りにならない正確な理由についての混乱も解決される可能性があります。  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>依存関係プロパティは複数の場所で "設定" される可能性がある  
 例を次に示します[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]で同じプロパティ (<xref:System.Windows.Controls.Control.Background%2A>) が 3 つの異なる「設定」操作の値に影響を与える可能性があります。  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 さて、赤、緑、青のどの色になるでしょうか。  
  
 アニメーション化された値および強制型変換の場合を除き、ローカル プロパティ セットは最高の優先順位で設定されます。 ローカルに値を設定する場合は、スタイルまたはコントロール テンプレートであっても、その値が採用されるものと期待できます。 例では、ここで<xref:System.Windows.Controls.Control.Background%2A>赤にローカルに設定されています。 したがって、それ以外の場合、そのスコープ内でその型のすべての要素に適用される暗黙的なスタイルである場合でも、このスコープで定義されているスタイルは最高の優先順位を与えるため、<xref:System.Windows.Controls.Control.Background%2A>プロパティの値。  Button インスタンスからローカル値の Red を削除すると、スタイルが優先されるようになり、ボタンの Background の値はスタイルから取得されます。  スタイル内ではトリガーが優先されるので、ボタンはマウスでポイントすると青になり、それ以外の場合は緑になります。  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>依存関係プロパティの設定の優先順位一覧  
 次に示すのは、依存関係プロパティの実行時の値を割り当てるときにプロパティ システムが使う明確な順序です。 優先順位が高いものから順に示されています。 この一覧では、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」で一般化されていたものを拡張してあります。  
  
1.  **プロパティ システムの強制型変換。** 強制型変換について詳しくは、後の「[強制型変換、アニメーション、基本値](#animations)」をご覧ください。  
  
2.  **アクティブなアニメーション、または保留動作のアニメーション。** 実際的な効果を得るためには、プロパティのアニメーションは、基本 (アニメーション化されていない) 値 (ローカルに設定された値であっても) より高い優先順位を持つことができる必要があります。 詳しくは、後の「[強制型変換、アニメーション、基本値](#animations)」をご覧ください。  
  
3.  **ローカル値。** 内の属性またはプロパティ要素として設定することに相当な「ラッパー」プロパティの利便性をローカルの値を設定する場合も[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、またはへの呼び出しによって、 <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]特定のインスタンスのプロパティを使用します。 バインドまたはリソースを使ってローカル値を設定する場合、これらは直接値が設定された場合のように優先されます。  
  
4.  **TemplatedParent テンプレート プロパティ。** 要素が、<xref:System.Windows.FrameworkElement.TemplatedParent%2A>テンプレートの一部として作成された場合 (、<xref:System.Windows.Controls.ControlTemplate>または<xref:System.Windows.DataTemplate>)。 これが適用されるケースについて詳しくは、後の「[TemplatedParent](#templatedparent)」をご覧ください。 テンプレート内では、次の優先順位が適用されます。  
  
    1.  [トリガー]、<xref:System.Windows.FrameworkElement.TemplatedParent%2A>テンプレート。  
  
    2.  プロパティ セット (通常を通じて[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性) で、<xref:System.Windows.FrameworkElement.TemplatedParent%2A>テンプレート。  
  
5.  **暗黙的スタイル。** `Style` プロパティのみに適用されます。 `Style` プロパティは、その要素の型と一致するキーを持つスタイル リソースによって設定されます。 そのスタイル リソースは、ページまたはアプリケーション内に存在する必要があります。暗黙的スタイル リソースの参照はテーマまでは及びません。  
  
6.  **スタイルのトリガー。** ページまたはアプリケーションに含まれるスタイル内のトリガー (これらのスタイルは、明示的スタイルまたは暗黙的スタイルどちらの場合もありますが、優先順位の低い既定スタイルではありません)。  
  
7.  **テンプレートのトリガー。** スタイル内のテンプレートまたは直接適用されたテンプレートからのトリガーです。  
  
8.  **スタイルのセッター。** 値から、<xref:System.Windows.Setter>ページまたはアプリケーションからのスタイル内です。  
  
9. **既定 (テーマ) のスタイル。** これが適用される場合、およびテーマ スタイルとテーマ スタイル内のテンプレートの関係について詳しくは、後の「[既定 (テーマ) のスタイル](#themestyles)」をご覧ください。 既定のスタイル内では、次の優先順位が適用されます。  
  
    1.  テーマ スタイル内のアクティブなトリガー。  
  
    2.  テーマ スタイル内のセッター。  
  
10. **継承。** いくつかの依存関係プロパティは親要素から子要素に値を継承するので、アプリケーション全体で各要素に値を明示的に設定する必要はありません。 詳しくは、「[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)」をご覧ください。  
  
11. **依存関係プロパティのメタデータの既定値。** どの依存関係プロパティも、その特定のプロパティがプロパティ システムに登録されるときに設定される既定値を持つことができます。 また、依存関係プロパティを継承する派生クラスには、型ごとにそのメタデータ (既定値を含む) をオーバーライドするオプションがあります。 詳しくは、「[依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)」をご覧ください。 継承は既定値の前にチェックされるため、継承されるプロパティの場合、親要素の既定値の方が子要素より優先されます。  その結果、継承可能なプロパティがどこでも設定されていない場合は、ルートまたは親で指定されている既定値が、子要素の既定値の代わりに使われます。  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 優先順位の項目としての TemplatedParent は、標準アプリケーション マークアップで直接宣言された要素のプロパティには適用されません。 TemplatedParent の概念は、テンプレートの適用によって作成されるビジュアル ツリー内の子項目に対してのみ存在します。 プロパティ システムを検索すると、<xref:System.Windows.FrameworkElement.TemplatedParent%2A>値用のテンプレート、その要素を作成したテンプレートが検索されます。 プロパティの値から、<xref:System.Windows.FrameworkElement.TemplatedParent%2A>テンプレートは、一般に設定されているものをローカルの値として、子要素には、テンプレートが共有される可能性があるために、このいずれか小さいほうの優先順位とローカルの値が存在するかのように動作します。 詳細については、「<xref:System.Windows.FrameworkElement.TemplatedParent%2A>」を参照してください。  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>スタイル プロパティ  
 1 つを除くすべての可能な依存関係プロパティに適用される前に説明した参照の順序:<xref:System.Windows.FrameworkElement.Style%2A>プロパティです。 <xref:System.Windows.FrameworkElement.Style%2A>プロパティは一意にできない自体スタイル設定することが優先順位の項目 5. ~ 8. は適用されません。 また、アニメーション化するか、強制型変換<xref:System.Windows.FrameworkElement.Style%2A>はお勧めしません (アニメーション化して<xref:System.Windows.FrameworkElement.Style%2A>アニメーション クラスが必要になります)。 これにより、3 つの方法を<xref:System.Windows.FrameworkElement.Style%2A>プロパティを設定することがあります。  
  
-   **明示的スタイル。** <xref:System.Windows.FrameworkElement.Style%2A>プロパティが直接設定します。 ほとんどの場合、スタイルはインラインでは定義されず、代わりにリソースとして明示的なキーにより参照されます。 この場合、スタイル プロパティ自体は、ローカル値と同じように扱われます (優先順位の項目 3)。  
  
-   **暗黙的スタイル。** <xref:System.Windows.FrameworkElement.Style%2A>プロパティが直接設定されていません。 ただし、<xref:System.Windows.FrameworkElement.Style%2A>リソース ルックアップ シーケンス (ページ、アプリケーション) の特定のレベルに存在してに適用されるスタイルは、型と一致するリソース キーを使用してが付いています。 ここで、<xref:System.Windows.FrameworkElement.Style%2A>プロパティ自体は、項目 5 シーケンス内の特定の優先順位によって動作します。 使用してこのような状況を検出できる<xref:System.Windows.DependencyPropertyHelper>に対して、<xref:System.Windows.FrameworkElement.Style%2A>プロパティおよび探して<xref:System.Windows.BaseValueSource.ImplicitStyleReference>結果にします。  
  
-   **既定のスタイル** (別称**テーマ スタイル**)。 <xref:System.Windows.FrameworkElement.Style%2A>プロパティを直接設定されていないととして実際に読み取られます`null`実行時までです。 この場合、スタイルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プレゼンテーション エンジンの一部である実行時テーマ評価によって決定されます。  
  
 テーマに含まれない暗黙的スタイルの場合は、型が厳密に一致する必要があります。`MyButton``Button` の派生クラスでは、`Button` のスタイルは暗黙的に使われません。  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>既定 (テーマ) のスタイル  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するすべてのコントロールには、既定のスタイルがあります。 既定のスタイルはテーマによって異なる場合があり、そのため、この既定のスタイルはテーマのスタイルとも呼ばれます。  
  
 最も重要な情報が見つかりました。 既定のスタイル内でコントロールは、コントロール テンプレート、テーマのスタイルにに対して set アクセス操作子として存在しているその<xref:System.Windows.Controls.Control.Template%2A>プロパティです。 既定のスタイルにテンプレートがない場合、カスタム スタイルの一部としてカスタム テンプレートがないコントロールは、まったく表示されません。 既定のスタイルのテンプレートは、各コントロールの外観に基本的な構造を提供し、テンプレートのビジュアル ツリーで定義されているプロパティと、対応するコントロール クラスの間の接続を定義します。 各コントロールでは、テンプレートを完全に置き換えることなくコントロールの外観に影響を与えることができる、一連のプロパティが公開されています。 たとえば、既定の外観、<xref:System.Windows.Controls.Primitives.Thumb>コンポーネントにあるコントロールの<xref:System.Windows.Controls.Primitives.ScrollBar>です。  
  
 A<xref:System.Windows.Controls.Primitives.Thumb>は特定のカスタマイズ可能なプロパティがあります。 既定のテンプレート、<xref:System.Windows.Controls.Primitives.Thumb>基本的な構造を作成するいくつかのビジュアル ツリーの入れ子になった/<xref:System.Windows.Controls.Border>傾斜の外観を作成するにはコンポーネントです。 テンプレートの一部であるプロパティによるカスタマイズを公開する場合は、<xref:System.Windows.Controls.Primitives.Thumb>クラス、によってそのプロパティを公開する必要があり、 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)テンプレート内で。 場合、 <xref:System.Windows.Controls.Primitives.Thumb>、これらの罫線のさまざまなプロパティなどのプロパティにテンプレート バインディングを共有<xref:System.Windows.Controls.Border.Background%2A>または<xref:System.Windows.Controls.Border.BorderThickness%2A>です。 しかし、他の特定のプロパティや視覚的な配置は、コントロール テンプレートにハードコードされているか、またはテーマから直接取得される値にバインドされており、テンプレート全体を置き換えない限り変更できません。 一般に、プロパティがテンプレート化された親から取得され、テンプレートのバインドによって公開されない場合は、それをターゲットにする簡単な方法がないため、そのプロパティをスタイルによって調整することはできません。 ただし、適用されるテンプレートのプロパティ値継承または既定値によって、そのプロパティに影響を与えることはできます。  
  
 テーマのスタイルでは、定義のキーとして型を使います。 ただし、テーマが指定された要素のインスタンスに適用されると、この種類の参照にテーマが実行をチェックして、<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>コントロールのプロパティです。 これは、暗黙的スタイルで行われるリテラル型の使用とは対照的です。 値<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>実行者変更していない (目的のプロパティを変更する方法では、このメソッドをオーバーライドするが、プロパティ レベルに代わりに既定値をプロパティのメタデータの変更が) 場合でもは、派生クラスに継承します。 この間接参照により、基底クラスは、他の方法ではスタイルを持たない派生要素に対してテーマのスタイルを定義できます (または、さらに重要なのは、スタイル内にテンプレートを持たず、既定の外観がないということです)。 したがって、派生させることができます`MyButton`から<xref:System.Windows.Controls.Button>でもと、<xref:System.Windows.Controls.Button>既定のテンプレートです。 場合は、コントロールの作成者の`MyButton`とは異なる動作が必要なの依存関係プロパティのメタデータをオーバーライドする可能性があります<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>で`MyButton`別のキーを返し、テンプレートを含む関連のテーマのスタイルを定義するには`MyButton`と共にパッケージ化する必要がある、`MyButton`コントロール。 テーマ、スタイル、コントロールの作成について詳しくは、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」をご覧ください。  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>動的リソース参照とバインド  
 動的リソース参照とバインド操作には、それらが設定される場所での優先順位が適用されます。 たとえば、ローカル値に適用される動的リソースは優先順位の項目 3 に準拠し、テーマ スタイル内のプロパティ セッターに対するバインドには優先順位の項目 9 が適用されます。 動的リソース参照とバインドはどちらもアプリケーションの実行時状態から値を取得できる必要があるので、特定のプロパティに対するプロパティ値の優先順位を決定する実際のプロセスは、実行時まで拡張されます。  
  
 厳密に言うと、動的リソース参照はプロパティ システムの一部ではありませんが、上で示したシーケンスに対応する独自の参照順序を持ちます。 その優先順位について詳しくは、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」をご覧ください。 基本的な優先順位をまとめると、ページ ルートの要素、アプリケーション、テーマ、システムになります。  
  
 動的リソースとバインドには設定された場所での優先順位がありますが、値は遅延されます。 その 1 つの帰結として、ローカル値に動的リソースまたはバインドを設定した場合、ローカル値を変更すると動的リソースまたはバインドが完全に置き換えられます。 呼び出す場合でも、<xref:System.Windows.DependencyObject.ClearValue%2A>ローカルに設定を消去するメソッドの値では、動的なリソースまたはバインドは復元されません。 実際には、呼び出した場合<xref:System.Windows.DependencyObject.ClearValue%2A>をインプレース (でリテラル ローカル値はありません)、動的なリソースまたはバインディングを持つプロパティをオフにしたによって、<xref:System.Windows.DependencyObject.ClearValue%2A>すぎますを呼び出します。  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A>メソッドは、プロパティを設定する別の方法が、優先順位の順序ではありません。 代わりに、<xref:System.Windows.DependencyObject.SetCurrentValue%2A>前の値のソースを上書きすることがなく、プロパティの値を変更することができます。 使用することができます<xref:System.Windows.DependencyObject.SetCurrentValue%2A>いつでもローカル値の優先順位をその値に与えることがなく、値を設定します。 たとえば、プロパティは、トリガーによって設定され、経由で別の値を代入して<xref:System.Windows.DependencyObject.SetCurrentValue%2A>プロパティ システムは引き続き、トリガーを尊重、およびトリガーのアクションが発生した場合、プロパティが変更されます。 <xref:System.Windows.DependencyObject.SetCurrentValue%2A>優先順位の高い、ソースを指定せず、プロパティの値を変更できます。 同様に、使用することができます<xref:System.Windows.DependencyObject.SetCurrentValue%2A>バインドを上書きすることがなく、プロパティの値を変更します。  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>強制型変換、アニメーション、基本値  
 強制型変換とアニメーションはどちらも、この [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] で "基本値" と呼ぶ値に対して作用します。 したがって、基本値とは、項目 2 に達するまで項目をさかのぼって評価されることにより決定される値です。  
  
 アニメーションの場合、アニメーションで特定の動作に対して "From" と "To" の両方が指定されていない場合、またはアニメーションが完了すると基本値に意図的に戻る場合は、基本値を使ってアニメーション化される値に影響を及ぼすことができます。 実際にどうなるのかを見るには、「[From, To, and By Animation Target Values Sample](http://go.microsoft.com/fwlink/?LinkID=159988)」(アニメーション ターゲット値 From、To、By のサンプル) をご覧ください。 この例で、四角形の高さのローカル値を、初期ローカル値がアニメーションの "From" と異なるように設定してみます。 アニメーションが "From" の値を使ってすぐに開始し、開始すると基本値を置き換えることがわかります。 アニメーションをアニメーションする前に、停止を指定することによって完了に検索された値に戻るには指定可能性があります<xref:System.Windows.Media.Animation.FillBehavior>です。 その後は、通常の優先順位が基本値の決定に使用されます。  
  
 1 つのプロパティに複数のアニメーションが適用され、各アニメーションが値の優先順位の異なるポイントから定義されている場合があります。 ただし、これらのアニメーションは、優先順位の高いアニメーションから単純に適用されるのではなく、値が合成される可能性があります。 これは、アニメーションの定義方法と、アニメーション化される値の型に依存します。 プロパティのアニメーション化について詳しくは、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」をご覧ください。  
  
 強制型変換は、すべての最高レベルで適用されます。 既に実行されているアニメーションであっても値の強制型変換が適用されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の特定の既存の依存関係プロパティには、組み込みの強制型変換があります。 カスタム依存関係プロパティを記述してカスタム依存関係プロパティの強制型変換動作を定義する、<xref:System.Windows.CoerceValueCallback>プロパティを作成するときに、メタデータの一部としてコールバックを渡します。 派生クラスでプロパティのメタデータをオーバーライドすることにより、既存のプロパティの強制型変換の動作をオーバーライドすることもできます。 強制型変換と基本値の相互作用は、その時点で強制型変換に対する制約が存在するものとして適用されるように行われますが、基本値はそれでも保持されます。 したがって、強制型変換の制約が後で無効になった場合、強制型変換はその基本値に可能な最も近い値を返し、プロパティに対する強制型変換の影響はすべての制約が無効になるとすぐに終了する可能性があります。 強制型変換の動作について詳しくは、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」をご覧ください。  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>トリガー動作  
 コントロールでは、テーマの既定のスタイルの一部としてトリガー動作が定義されていることがよくあります。 コントロールにローカル プロパティを設定すると、ユーザー駆動のイベントに対してトリガーが視覚的または動作的に応答できなくなる可能性があります。 プロパティ トリガーの最も一般的な使用などのコントロールまたは状態のプロパティが<xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>です。 たとえば、既定でときに、<xref:System.Windows.Controls.Button>は無効になります (のトリガーに<xref:System.Windows.UIElement.IsEnabled%2A>は`false`)、<xref:System.Windows.Controls.Control.Foreground%2A>テーマ スタイルの値は、「グレー」表示するコントロールが原因です。 ローカルを設定している場合は<xref:System.Windows.Controls.Control.Foreground%2A>値、このプロパティによってトリガーされるシナリオであっても、ローカル プロパティ セットによって、優先順位で正常の灰色アウト色を無視できますされます。 テーマ レベルのトリガー動作があるプロパティの値を設定するときは注意し、そのコントロールの目的のユーザー エクスペリエンスに過度に干渉していないことを確認する必要があります。  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue と値の優先順位  
 <xref:System.Windows.DependencyObject.ClearValue%2A>メソッドには任意のローカルに適用されている要素に設定されている依存関係プロパティ値をクリアする、便利なことを意味します。 ただし、呼び出し<xref:System.Windows.DependencyObject.ClearValue%2A>プロパティの登録中に、メタデータで確立された既定値は、新しい有効な値である保証はありません。 値の優先順位に関係する他のすべての要因はアクティブなままです。 ローカルで設定された値が優先順位のシーケンスから削除されるだけです。 呼び出す場合など、<xref:System.Windows.DependencyObject.ClearValue%2A>どこでも、そのプロパティが、テーマのスタイルで設定し、テーマの値がメタデータに基づく既定ではなく、新しい値として適用されるプロパティです。 依存関係プロパティのメタデータと、クエリと明確にして既定値が既定値をローカルで使用できることを取得するには、プロセス外のすべてのプロパティ値の参加者を行い、登録されているメタデータの既定値を設定する場合は、呼び出しを使用してプロパティを設定<xref:System.Windows.DependencyObject.SetValue%2A>です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.DependencyObject>  
 <xref:System.Windows.DependencyProperty>  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)
