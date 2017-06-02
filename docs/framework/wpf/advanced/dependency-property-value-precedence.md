---
title: "依存関係プロパティ値の優先順位 | Microsoft Docs"
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
  - "クラス, 所有者 (依存関係プロパティの)"
  - "依存関係プロパティ, クラス (所有者としての)"
  - "依存関係プロパティ, メタデータ"
  - "メタデータ, 依存関係プロパティ"
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# 依存関係プロパティ値の優先順位
<a name="introduction"></a> ここでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プロパティ システムの機能が[依存関係プロパティ](GTMT)の値にどのように影響する可能性があるかについて説明し、プロパティ システムの側面がプロパティの有効値に適用される際の優先順位を示します。  
  
   
  
<a name="prerequisites"></a>   
## 必要条件  
 このトピックでは、ユーザーが [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスの既存の依存関係プロパティの使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」トピックを通読していることを前提としています。  このトピックの例を実行するには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] について理解し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの記述に精通している必要があります。  
  
<a name="intro"></a>   
## WPF プロパティ システム  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムは、依存関係プロパティの値をさまざまな要素に基づいて決定するための強力な方法を提供し、リアルタイムのプロパティ検証や遅延バイディングなどの機能を実現すると共に、関連するプロパティに他のプロパティの値の変更について通知します。  依存関係プロパティの値を決定するために使用される厳密な順序とロジックは、かなり複雑です。  この順序を理解することにより、不必要なプロパティ設定を回避できると同時に、依存関係プロパティ値を変更または取得する操作を行ったにもかかわらず最終的に想定どおりの値が設定されなかった場合、その原因を究明できます。  
  
<a name="multiple_sets"></a>   
## 複数の場所に "設定" 可能な依存関係プロパティ  
 1 つのプロパティ \(<xref:System.Windows.Controls.Control.Background%2A>\) に、値に影響を与える可能性がある 3 つの異なる "設定" 操作がある場合の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 例を次に示します。  
  
 [!code-xml[PropertiesOvwSupport#DPPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 ここでは、赤色、緑色、青色のうち、どの色が適用されるかを考えます。  
  
 アニメーション化された値および強制を除き、ローカルのプロパティ セットが最も高い優先順位で設定されます。  任意のスタイルまたはコントロール テンプレートの上に設定した場合でも、ローカルに値を設定すると、この値が適用されると想定できます。  この例では、<xref:System.Windows.Controls.Control.Background%2A> が Red としてローカルに設定されています。  したがって、このスコープ内で定義されるスタイルは、これ以外の場合にはそのスコープ内のその型のすべての要素に適用される暗黙のスタイルであっても、<xref:System.Windows.Controls.Control.Background%2A> プロパティに値を指定する際には最高の優先順位を持ちません。  Button インスタンスから Red のローカル値を削除した場合は、スタイルが優先され、ボタンはスタイルから Background 値を取得します。  スタイル内ではトリガーが優先されるため、マウスが置かれるとボタンは青色になり、それ以外の場合は緑色になります。  
  
<a name="listing"></a>   
## 依存関係プロパティ設定の優先順位リスト  
 依存関係プロパティのランタイム値を割り当てる際に、最終的にプロパティ システムで使用される順序を次に示します。  優先順位の高いものから順に示します。  このリストは、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」で取り上げた一般化を一部拡張したものです。  
  
1.  **プロパティ システムの強制型変換。**強制型変換の詳細については、このトピックの「[強制型変換、アニメーション、および基本値](#animations)」を参照してください。  
  
2.  **アクティブなアニメーション、または Hold 動作を使用したアニメーション。**実際的な効果を持たせるためには、プロパティのアニメーションは値がローカルに設定されている場合でも、その基本 \(アニメーション化されていない\) 値よりも優先される必要があります。  詳細については、このトピックの「[強制型変換、アニメーション、および基本値](#animations)」を参照してください。  
  
3.  **ローカル値。**ローカル値は "ラッパー" プロパティの利点を利用して設定できます。これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]内で属性またはプロパティ要素として設定することと同じです。また、特定のインスタンスのプロパティを使用して <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] を呼び出すことによって設定することもできます。  バインディングまたはリソースを使用してローカル値を設定すると、優先順位に関しては値を直接設定した場合と同じように扱われます。  
  
4.  **TemplatedParent テンプレート プロパティ。**テンプレート \(<xref:System.Windows.Controls.ControlTemplate> または <xref:System.Windows.DataTemplate>\) の一部として作成された要素には、<xref:System.Windows.FrameworkElement.TemplatedParent%2A> が含まれます。  これが当てはまる状況については、このトピックの「[TemplatedParent](#templatedparent)」を参照してください。  テンプレート内では、次の優先順位が適用されます。  
  
    1.  <xref:System.Windows.FrameworkElement.TemplatedParent%2A> テンプレートからのトリガー。  
  
    2.  <xref:System.Windows.FrameworkElement.TemplatedParent%2A> テンプレート内のプロパティ セット \(通常は [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 属性によって提供される\)。  
  
5.  **暗黙のスタイル。** `Style` プロパティにだけ適用されます。  `Style` プロパティには、その要素の種類に一致するキーを持つスタイル リソースが設定されます。  このスタイル リソースは、ページまたはアプリケーション内に存在する必要があります。暗黙のスタイル リソースの検索はテーマまで進行しません。  
  
6.  **スタイルのトリガー。**ページまたはアプリケーションからのスタイル内トリガー \(スタイルは明示または暗黙のスタイルですが、優先順位の低い既定のスタイルではありません\)。  
  
7.  **テンプレートのトリガー。**スタイル内のテンプレートの任意のトリガー、または直接適用されたテンプレート。  
  
8.  **スタイルの setter。**ページまたはアプリケーションからのスタイル内 <xref:System.Windows.Setter> の値。  
  
9. **既定の \(テーマ\) スタイル。**これが適用される状況とテーマ スタイル内でのテーマ スタイルとテンプレートの関連付けの詳細については、このトピックの「[既定の \(テーマ\) スタイル](#themestyles)」を参照してください。  既定のスタイル内では、次の優先順位が適用されます。  
  
    1.  テーマ スタイル内のアクティブなトリガー。  
  
    2.  テーマ スタイル内の setter。  
  
10. **継承。**いくつかの依存関係プロパティは、アプリケーション全体で各要素に明確に設定しなくて済むように、親要素から子要素に値が継承されます。  詳細については、[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md) を参照してください。  
  
11. **依存関係プロパティのメタデータの既定値。**依存関係プロパティは、その特定のプロパティのプロパティ システム登録によって設定された既定値を持つ場合があります。  また、依存関係プロパティを継承する派生クラスは、型ごとにそのメタデータ \(既定値を含む\) をオーバーライドすることができます。  詳細については、「[依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)」を参照してください。  継承されたプロパティについては、既定値の前に継承がチェックされるため、親要素の既定値が子要素よりも優先されます。  このため、継承可能なプロパティがどこにも設定されていない場合は、子要素の既定値の代わりにルートまたは親に指定された既定値が使用されます。  
  
<a name="templatedparent"></a>   
## TemplatedParent  
 優先順位項目としての TemplatedParent は、標準のアプリケーション マークアップに直接宣言した要素のプロパティには適用されません。  TemplatedParent の概念は、テンプレートのアプリケーションを通じて成立するビジュアル ツリー内の下位項目に対してのみ存在します。  プロパティ システムが値の <xref:System.Windows.FrameworkElement.TemplatedParent%2A> テンプレートを検索する場合は、その要素を作成したテンプレートが検索されます。  一般に、<xref:System.Windows.FrameworkElement.TemplatedParent%2A> テンプレートのプロパティ値は、下位要素のローカル値として設定されている場合と同様に機能します。ただし、テンプレートは共有されている可能性があるため、優先順位はローカル値よりも下位である必要があります。  詳細については、「<xref:System.Windows.FrameworkElement.TemplatedParent%2A>」を参照してください。  
  
<a name="style_property"></a>   
## Style プロパティ  
 前に説明した検索の順序は、<xref:System.Windows.FrameworkElement.Style%2A> プロパティを除く、存在するすべての依存関係プロパティに適用されます。  <xref:System.Windows.FrameworkElement.Style%2A> プロパティは、それ自体のスタイルを設定できないという特異なプロパティであるため、優先順位の項目 5 ～ 8 は適用されません。  また、<xref:System.Windows.FrameworkElement.Style%2A> のアニメーションまたは強制型変換は推奨されません \(<xref:System.Windows.FrameworkElement.Style%2A> のアニメーションにはカスタムのアニメーション クラスが必要になります\)。  <xref:System.Windows.FrameworkElement.Style%2A> プロパティを設定する方法として、残されたのは次の 3 つです。  
  
-   **明示的なスタイル。** <xref:System.Windows.FrameworkElement.Style%2A> プロパティを直接設定します。  ほとんどのシナリオでは、スタイルをインラインで定義するのではなくリソースとして明示的なキーにより参照します。  この場合、Style プロパティ自体はローカル値であるかのように動作します \(優先順位の項目 3\)。  
  
-   **暗黙のスタイル。** <xref:System.Windows.FrameworkElement.Style%2A> プロパティを直接設定しません。  ただし、<xref:System.Windows.FrameworkElement.Style%2A> はリソース検索シーケンスのどれかのレベル \(ページ、アプリケーション\) に存在し、適用対象のスタイルの種類に一致するリソース キーによりキーが設定されます。  この場合、<xref:System.Windows.FrameworkElement.Style%2A> プロパティ自体はシーケンス内で優先順位の項目 5 となるように動作します。  この情報は、<xref:System.Windows.FrameworkElement.Style%2A> プロパティに <xref:System.Windows.DependencyPropertyHelper> を使用し、その結果で <xref:System.Windows.BaseValueSource> を検索することによって確認できます。  
  
-   **既定のスタイル** \(別名**テーマ スタイル**\)。<xref:System.Windows.FrameworkElement.Style%2A> プロパティは直接設定しません。実行時までは、プロパティを読み取ると `null` が返されます。  この方法では、スタイルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プレゼンテーション エンジンの一部である実行時テーマ評価処理によって生成されます。  
  
 テーマ内にない暗黙のスタイルの場合、型は正確に一致する必要があります。たとえば、`Button` 派生クラス `MyButton` では、`Button` のスタイルは暗黙的には使用されません。  
  
<a name="themestyles"></a>   
## 既定の \(テーマ\) スタイル。  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールには既定のスタイルがあります。  既定のスタイルはテーマによって異なる可能性があります。既定のスタイルがテーマ スタイルとも呼ばれるのは、このような理由があるためです。  
  
 コントロールの既定のスタイルに含まれる最も重要な情報は、コントロール テンプレートです。このテンプレートは、テーマ スタイルでは <xref:System.Windows.Controls.Control.Template%2A> プロパティの setter として存在します。  既定のスタイルにテンプレートがなかったとしたら、カスタム スタイルの一部としてカスタム テンプレートを持たないコントロールは、表示形式をまったく持たないことになります。  既定のスタイルのテンプレートによって、コントロールの表示形式に基本構造が与えられ、テンプレートのビジュアル ツリーに定義されたプロパティとそれに対応するコントロール クラスが適切に接続されます。  コントロールからは、テンプレートを完全に置き換えなくてもコントロールの表示形式を変更できる一連のプロパティが提供されます。  たとえば、<xref:System.Windows.Controls.Primitives.Thumb> コントロールの既定の表示形式を例として説明します。このコントロールは、<xref:System.Windows.Controls.Primitives.ScrollBar> のコンポーネントです。  
  
 <xref:System.Windows.Controls.Primitives.Thumb> は、特定のカスタマイズしたプロパティを持ちます。  <xref:System.Windows.Controls.Primitives.Thumb> の既定のテンプレートによって、傾斜して表示されるいくつかの入れ子になった <xref:System.Windows.Controls.Border> コンポーネントから成る基本構造とビジュアル ツリーが作成されます。  テンプレートの一部であるプロパティを <xref:System.Windows.Controls.Primitives.Thumb> クラスによってカスタマイズされることを意図して公開する場合は、テンプレート内で [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) を使用してそのプロパティを公開する必要があります。  <xref:System.Windows.Controls.Primitives.Thumb> では、これらの境界のさまざまなプロパティは <xref:System.Windows.Controls.Border.Background%2A> や <xref:System.Windows.Controls.Border.BorderThickness%2A> などのプロパティへのテンプレート バインディングを共有します。  しかし、他の特定のプロパティやビジュアル配置は、コントロール テンプレート内にハードコーディングされるかテーマに直接設定された値にバインドされており、テンプレート全体を置き換えるには不十分であるため変更できません。  一般にプロパティが、テンプレート化されている親に由来し、テンプレート バインディングから公開されない場合、対象をこのプロパティに設定する簡単な方法がないため、スタイルを使用して調整することはできません。  しかし、このプロパティも、適用されるテンプレートのプロパティ値継承による、または既定値による影響を受けます。  
  
 テーマ スタイルの定義では、データ型がキーとして使用されます。  ただし、テーマを特定の要素インスタンスに適用すると、この型に対するテーマの検索は、コントロールの <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> プロパティをチェックすることにより実行されます。  これは、暗黙のスタイルでリテラル型が使用されるのと対照的です。  <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> の値は、実装側で変更されない場合でも派生クラスに継承されます \(プロパティを変更する方法として意図されているのは、プロパティ レベルでオーバーライドすることではなく、既定値をプロパティ メタデータで変更することです\)。  このような間接的な方法を使うことにより、基本クラスでは、他の方法ではスタイルを持つことがない \(さらに重要なことには、そのスタイル内にテンプレートを持たないため既定の表示形式をまったく持つことがない\) 派生要素にテーマ スタイルを定義できます。  そのため、`MyButton` を <xref:System.Windows.Controls.Button> から派生でき、さらに <xref:System.Windows.Controls.Button> 既定テンプレートを取得できます。  `MyButton` コントロールの作成者が別の動作を必要とする場合は、別のキーを返すよう <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> の依存関係プロパティのメタデータを `MyButton` でオーバーライドし、`MyButton` コントロールにパッケージ化する必要がある `MyButton` 用テンプレートなどを関連テーマ スタイルに定義できます。  テーマ、スタイル、およびコントロールの作成の詳細については、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
<a name="resources"></a>   
## 動的リソース参照とバインディング  
 動的リソース参照とバインディング操作では、設定された場所の優先順位が優先されます。  たとえば、ローカル値に適用される動的リソースは優先順位の項目 3 に準拠し、テーマ スタイル内のプロパティ setter のバインディングは優先順位の項目 9 で適用されます。  動的リソース参照とバインディングはどちらも、アプリケーションの実行時の状態から値を取得できる必要があります。このため、指定された任意のプロパティに対してプロパティ値の優先順位を決定する実際のプロセスは、実行時まで拡張されます。  
  
 動的リソース参照は、厳密にはプロパティ システムの一部ではありませんが、前に述べた順序に関連する独自の検索順序を持ちます。  この優先順位の詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  この優先順位は、簡単に要約すると、ページ ルート、アプリケーション、テーマ、システムに対する要素です。  
  
 動的リソース参照とバインディング操作は設定された場所の優先順位を持ちますが、その値は遅延されます。  このため、動的リソースまたはバインディングをローカル値に設定した場合、このローカル値を変更すると動的バインディングまたはバインディング全体が完全に置き換えられます。  ローカルに設定された値を消去するために <xref:System.Windows.DependencyObject.ClearValue%2A> メソッドを呼び出した場合でも、動的リソースまたはバインディングは復元されません。  実際、動的リソースまたはバインディングが指定されたプロパティ \(リテラルのローカル値ではない\) で <xref:System.Windows.DependencyObject.ClearValue%2A> を呼び出した場合、これらもこの <xref:System.Windows.DependencyObject.ClearValue%2A> の呼び出しによって消去されます。  
  
<a name="setcurrentvalue"></a>   
## SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> メソッドはプロパティを設定するためのもう 1 つの方法ですが、プロパティの設定は優先順位の順に行われません。  <xref:System.Windows.DependencyObject.SetCurrentValue%2A> を使用すると、前の値のソースを上書きすることなくプロパティ値を変更できます。  <xref:System.Windows.DependencyObject.SetCurrentValue%2A> は、ローカル値の優先順位を与えずに値を設定する場合にいつでも使用できます。  たとえば、トリガーによってプロパティが設定され、<xref:System.Windows.DependencyObject.SetCurrentValue%2A> を介してこのプロパティに別の値が割り当てられた場合、プロパティ システムはトリガーを考慮するため、トリガーのアクションが発生するとプロパティは変更されます。  <xref:System.Windows.DependencyObject.SetCurrentValue%2A> を使用すると、高い優先順位を持つソースを与えることなくプロパティ値を変更できます。  同様に、<xref:System.Windows.DependencyObject.SetCurrentValue%2A> を使用すると、バインディングを上書きすることなくプロパティ値を変更できます。  
  
<a name="animations"></a>   
## 強制、アニメーション、および基本値  
 強制とアニメーションはどちらも、この [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 全体で "基本値" と呼ばれる値に基づいて機能します。  基本値は、項目 2 に達するまで項目を上方に評価することによって決定される値です。  
  
 アニメーションでは、特定の動作に "From" と "To" の両方を指定していない場合、またはアニメーションが完了すると基本値に戻るようにする場合に、基本値はアニメーション化される値に影響を与えます。  これを実際に確かめるには、[アニメーションのターゲット値 \(From、To、および By\) のサンプル](http://go.microsoft.com/fwlink/?LinkID=159988)を実行します。  ローカル値の初期値をアニメーション内の "From" とは異なる値にするために、例の中で四角形の高さを示すローカル値を設定してください。  アニメーションは "From" 値を使用して直ちに開始され、開始後にこの基本値を置き換えます。  アニメーションは、Stop <xref:System.Windows.Media.Animation.FillBehavior> を指定してアニメーションを完了した後、アニメーションの前に見つかった値に戻るように指定できます。  それ以降、基本値の決定には通常の優先順位が使用されます。  
  
 1 つのプロパティに複数のアニメーションが適用され、アニメーションごとに値の優先順位に関する定義が異なる場合が考えられます。  この場合は、単に優先順位が高いアニメーションを適用するのではなく、アニメーションでそれらの値を組み合わせることがあります。  これは、アニメーションが実際にどのように定義されているか、およびアニメーション化される値の型によって異なります。  プロパティのアニメーション化の詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
 強制は、最高レベルで適用されます。  既に実行中のアニメーションでも、値の強制に制約されます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内の既存の依存関係プロパティの中には、組み込みの強制を持つものがあります。  カスタム依存関係プロパティの場合は、プロパティの作成時に <xref:System.Windows.CoerceValueCallback> を記述し、メタデータの一部としてコールバックを渡すことにより、カスタム依存関係プロパティの強制動作を定義します。  また、派生クラス内のそのプロパティでメタデータをオーバーライドすることにより、既存のプロパティの強制動作をオーバーライドすることもできます。  強制の制約がその時点の制約として適用されるが基本値は引き続き保持されるという形で、強制は基本値と関係しています。  したがって、その後で強制の制約が解除されると、強制はその基本値に最も近い値を返し、制約がすべて解除された場合には、強制のプロパティへの影響は直ちになくなる可能性があります。  強制型変換の動作の詳細については、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」を参照してください。  
  
<a name="triggers"></a>   
## トリガー動作  
 多くの場合、コントロールは、トリガー動作をテーマ内の既定のスタイルの一部として定義します。  コントロールにローカル プロパティを設定すると、ユーザーによる表示上または動作上のイベントに対してトリガーが応答できなくなる場合があります。  プロパティ トリガーは、最も一般的には、コントロール プロパティや <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A> などの状態プロパティのために使用されます。  たとえば、既定で <xref:System.Windows.Controls.Button> が無効な場合 \(<xref:System.Windows.UIElement.IsEnabled%2A> のトリガーが `false` の場合\)、テーマ スタイル内の <xref:System.Windows.Controls.Control.Foreground%2A> 値によってコントロールは "灰色表示" されます。  ただし、ローカルの <xref:System.Windows.Controls.Control.Foreground%2A> 値を設定している場合は、プロパティがトリガーされるというこのシナリオでも、ローカル プロパティ セットが通常の灰色表示よりも優先されます。  テーマ レベルのトリガー動作が含まれるプロパティの値の設定は慎重に行い、そのコントロールで意図されるユーザー エクスペリエンスに過度に干渉しないようにしてください。  
  
<a name="clearvalue"></a>   
## ClearValue および値の優先順位  
 <xref:System.Windows.DependencyObject.ClearValue%2A> メソッドは、要素に設定される[依存関係プロパティ](GTMT)からローカルに適用された値を消去するのに役立つ方法を提供します。  ただし、<xref:System.Windows.DependencyObject.ClearValue%2A> を呼び出しても、プロパティの登録時にメタデータ内に設定された既定値が新しい有効値になることは保証されません。  値の優先順位に関係するその他すべての値は依然としてアクティブです。  ローカルに設定された値のみが、一連の優先順位から削除されています。  たとえば、テーマ スタイルによっても設定されているプロパティで <xref:System.Windows.DependencyObject.ClearValue%2A> を呼び出すと、テーマ値はメタデータに基づいた既定値ではなく新しい値として適用されます。  プロセスから関連するすべてのプロパティ値を取得して、登録されたメタデータの既定値に値を設定する場合は、依存関係プロパティのメタデータを照会することによって明確に既定値を取得でき、さらにこの既定値を使用し、<xref:System.Windows.DependencyObject.SetValue%2A> を呼び出してプロパティをローカルに設定できます。  
  
## 参照  
 <xref:System.Windows.DependencyObject>   
 <xref:System.Windows.DependencyProperty>   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)