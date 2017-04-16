---
title: "WPF における XAML とカスタム クラス | Microsoft Docs"
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
  - "クラス, カスタム クラス (XAML)"
  - "カスタム クラス (XAML)"
  - "XAML, カスタム クラス"
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# WPF における XAML とカスタム クラス
[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] のフレームワークで実装される XAML は [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] の言語のカスタム クラスまたは構造体を定義してXAML マークアップを使用してアクセスすることができます。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] で定義されている型とカスタム型は、通常はカスタム型を XAML 名前空間プレフィックスにマップすることで、同じマークアップ ファイルで使用することができます。  このトピックでは満たすカスタム クラスが XAML 要素として使用する必要があるという要件について説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## アプリケーション内のカスタム クラスとアセンブリ内のカスタム クラス  
 XAML で使用するカスタム クラスは 2 種類の形でも定義できます : コードとしてビハインドかの主要なアプリケーションを作成 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 他のコード内またはクラス ライブラリとして使用されている実行可能ファイルまたは DLL などの別のアセンブリのクラス。  これらの方法には、それぞれ利点と欠点があります。  
  
-   クラス ライブラリを作成する場合の利点は、それらのカスタム クラスを異なる多くのアプリケーションの間で共有できることです。  別のライブラリはアプリケーションのバージョン管理の問題に制御しやすくなります。の使用を目的の XAML ページ ルート要素として持つクラスの作成が簡単になります。  
  
-   カスタム クラスをアプリケーション内で定義する場合の利点は、比較的軽量であることです。メインのアプリケーションの実行可能ファイルとは別のアセンブリを導入する場合に生じる配置やテストの問題を最小限に抑えることができます。  
  
-   同じまたは別のアセンブリで定義されてカスタム クラスがCLR 名前空間と XML 名前空間の間の要素としての XAML で使用するために割り当てる必要があるかどうか。  「[XAML 名前空間および WPF XAML の名前空間の割り当て](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## XAML 要素としてのカスタム クラスの要件  
 カスタム クラスをオブジェクト要素としてインスタンス化できるようにするには、次の要件が満たされている必要があります。  
  
-   カスタム クラスがパブリックであり、既定の \(パラメーターなしの\) パブリック コンストラクターがサポートされている   \(構造体に関する説明は次のセクションを参照してください\)。  
  
-   カスタム クラスが入れ子になっていない。  入れ子になったクラスや、そのクラスの一般的な CLR で使用される構文の "ドット" は、添付プロパティなどの他の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] または XAML の機能に干渉します。  
  
 オブジェクト要素構文を使用できるようになると、オブジェクト定義でそのオブジェクトを値の型とする他のパブリック プロパティでプロパティ要素構文を使用できるようにもなります。  これは、オブジェクト要素としてインスタンス化できるようになったオブジェクトは、そのプロパティのプロパティ要素値として設定できるためです。  
  
### 構造体  
 カスタム型を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の XAML で構築されるため常に定義する構造体。これは [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] コンパイラが暗黙的に既定ではすべてのプロパティ値を初期化する構造体の既定のコンストラクターが作成されるためです。  既定のコンストラクターの動作やある構造体におけるオブジェクト要素の使用が望ましくない場合もあります。  その理由は、構造体は値と関数を概念的に一体として入れることを意図しており、このため含まれた値が排他的な解釈を持つ可能性があり、その結果プロパティがまったく設定できない場合が生じるためです。  このような構造体の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の例は <xref:System.Windows.GridLength> です。  一般的にこのような構造体には、異なる解釈や構造体の値のモードを作成する文字列の規則を使って値を属性形式で表示できるようにする型コンバーターを実装します。  この構造体では、コード構築が既定以外のコンストラクターによって行われる場合にも、同じ動作が見られると考えられます。  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## カスタム クラスのプロパティの XAML 属性としての要件  
 プロパティでは、値の型 \(プリミティブなど\) を参照するか、既定のコンストラクターまたは XAML プロセッサからアクセスできる専用の型コンバーターを持つ型のクラスを使用する必要があります。  CLR における XAML の実装では、XAML プロセッサはそのようなコンバーターを、言語プリミティブのネイティブ サポートを通じて検索するか、またはバッキング型定義の型やメンバーに対する <xref:System.ComponentModel.TypeConverterAttribute> のアプリケーションを通じて検索します。  
  
 そのほか、抽象クラス型やインターフェイスを参照することもできます。  抽象クラスやインターフェイスの場合は、そのインターフェイスを実装する実用クラスのインスタンスや、その抽象クラスを派生する型のインスタンスによって、XAML 解析時にプロパティ値が設定されることが想定されます。  
  
 プロパティは抽象クラスで宣言できますが、その抽象クラスから派生する実用クラスでしか設定できません。  これは、クラスのオブジェクト要素を作成するには、クラスにパブリックな既定のコンストラクターが必要であるためです。  
  
### 型コンバーターによって実現される属性構文  
 属性として割り当てられた専用の型コンバーターをクラス レベルで用意すると、適用される型変換によって、その型をインスタンス化する必要がある任意のプロパティで属性構文を使用できるようになります。  型コンバーターを用意しても、その型のオブジェクト要素の使用は有効になりません。オブジェクト要素の使用は、その型の既定のコンストラクターが存在する場合にのみ有効です。  したがって、型コンバーターによって実現されるプロパティは、その型自体でオブジェクト要素構文もサポートされていない限り、一般にプロパティ構文では使用できません。  例外として、プロパティ要素に文字列を含める場合には、プロパティ要素構文を指定できます。  この使用方法は、実際には属性構文の使用方法と本質的に変わらず、属性値で空白の堅牢な処理が必要な場合を除いては一般的ではありません。  文字列を受け取るプロパティ要素の使用方法と、それと同等な属性の使用方法を次の例に示します。  
  
 [!code-xml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 属性構文を使用できますがプロパティ要素構文です <xref:System.Windows.Input.Cursor> の型を使用するさまざまなプロパティ拒否されるオブジェクト要素を含むプロパティの例としてはXAML で。  <xref:System.Windows.Input.Cursor> クラスには専用の型コンバーター <xref:System.Windows.Input.CursorConverter> がありますが、既定のコンストラクターは公開されていません。このため、<xref:System.Windows.FrameworkElement.Cursor%2A> プロパティは、実際の <xref:System.Windows.Input.Cursor> 型は参照型であるにもかかわらず、属性構文でしか設定できません。  
  
### プロパティごとの型コンバーター  
 プロパティ レベルで型コンバーターを宣言することもできます。  これにより、プロパティの型のオブジェクトをインラインでインスタンス化する "ミニ言語" が実現されます。これは、渡される属性の文字列値を <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 操作の入力として適切な型に基づいて処理することによって行われます。  通常XAML でプロパティを設定できるようにするための唯一の手段として便宜上アクセサーを提供するようにします。  ただし、使用する既存の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 型に既定のコンストラクターも、属性として割り当てられた型コンバーターも用意されていない場合に、属性の型コンバーターを使用することもできます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API では <xref:System.Globalization.CultureInfo> の型を使用する特定のプロパティです。  この場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は.NET Framework の以前のバージョンで使用され<xref:System.Globalization.CultureInfo> の型はXAML のプロパティ値として使用するために必要なコンストラクターまたは型レベルの型変換を直接サポートされていませんでしたアドレスの互換性移行のシナリオを実現するために [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 既存の <xref:System.Globalization.CultureInfo> の型を使用しています。  
  
 XAML を使用するプロパティを公開するときには常に \(コントロールを作成する場合は特に\)、そのプロパティを依存関係プロパティで補足することを強くお勧めします。  これは <xref:System.Windows.DependencyProperty> のサポートを使用することでパフォーマンスを向上できるためXAML プロセッサの [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の既存の実装を使用する場合は特に当てはまります。  依存関係プロパティは、XAML でアクセス可能なプロパティに対して期待されるプロパティ システム機能をそのプロパティのために公開します。  これには、アニメーション、データ バインディング、スタイルのサポートなどの機能が含まれます。  詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」および「[XAML 読み込みと依存関係プロパティ](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)」を参照してください。  
  
### 型コンバーターの作成と割り当て  
 プロパティ型の型変換を提供するためにカスタム <xref:System.ComponentModel.TypeConverter> 派生クラスの作成が必要になることはあります。  XAML の使用をサポートする型コンバーターの派生および作成の手順や、<xref:System.ComponentModel.TypeConverterAttribute> の適用方法については、「[TypeConverters および XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)」を参照してください。  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## カスタム クラスのイベントの XAML イベント ハンドラー属性構文の要件  
 イベントを [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントとして使用できるようにするには、既定のコンストラクターをサポートするクラスか、派生クラスでイベントにアクセスできる抽象クラスで、パブリック イベントとして公開する必要があります。  [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントを[ルーティング イベント](GTMT)として便利に使用できるようにするには、明示的な `add` メソッドと `remove` メソッドを実装する必要があります。それらのメソッドは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベント シグネチャのハンドラーを追加および削除し、それらのハンドラーを <xref:System.Windows.UIElement.AddHandler%2A> メソッドと <xref:System.Windows.UIElement.RemoveHandler%2A> メソッドに転送します。  これらのメソッドは、イベントがアタッチされているインスタンスのルーティング イベント ハンドラー ストアのハンドラーを追加または削除します。  
  
> [!NOTE]
>  <xref:System.Windows.UIElement.AddHandler%2A> を使用して直接ルーティング イベントのハンドラーを登録し、[ルーティング イベント](GTMT)を公開する [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントを意図的に定義しないようにすることもできます。  これは通常イベントのハンドラーをアタッチする XAML 属性構文を有効にしてクラスがその型の機能は透過的な XAML ビューを提供するためにお勧めできません。  
  
<a name="Collection_Properties"></a>   
## コレクション プロパティの作成  
 コレクション型を受け取るプロパティには、コレクションに追加されるオブジェクトを指定できる XAML 構文があります。  この構文には注目すべき機能が 2 つあります。  
  
-   コレクション オブジェクトとなるオブジェクトをオブジェクト要素構文で指定する必要はありません。  コレクション型を受け取るプロパティを XAML で指定するたびに、そのコレクション型の存在が暗黙的に示されます。  
  
-   マークアップにおけるコレクション プロパティの子要素が処理されると、コレクションのメンバーになります。  通常は、コレクションのメンバーにコードでアクセスするには、`Add` などのリスト\/ディクショナリ メソッドを使用するか、インデクサーを使用します。  ただしXAML  構文はメソッドやインデクサー \(例外をサポートしていません : XAML 2009 はメソッドをサポートできますがXAML 2009 を使用する可能な WPF の使用を制限します ; [XAML 2009 言語機能](../../../../docs/framework/xaml-services/xaml-2009-language-features.md) を参照してください。  コレクションは要素ツリーの構築のためにごく一般的に必要になるため、それらのコレクションを宣言型の XAML で設定するための何らかの方法が必要です。  このため、コレクション プロパティの子要素は、コレクション プロパティ型の値であるコレクションに追加することによって処理されます。  
  
 .NET Framework XAML サービス実装しコレクション プロパティを構成します。がWPF XAML プロセッサは次のシグネチャを使用します。  プロパティのプロパティ型で次のいずれかを実装する必要があります。  
  
-   <xref:System.Collections.IList> を実装します。  
  
-   <xref:System.Collections.IDictionary>、またはこれと同等のジェネリック クラス \(<xref:System.Collections.Generic.IDictionary%602>\) を実装します。  
  
-   <xref:System.Array> から派生します \(XAML の配列に関する詳細については[x:Array のマークアップ拡張機能](../../../../docs/framework/xaml-services/x-array-markup-extension.md) を参照してください\)。  
  
-   <xref:System.Windows.Markup.IAddChild> \([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で定義されているインターフェイス\) を実装します。  
  
 これらの型はCLR がオブジェクト グラフを作成すると基になるコレクションに項目を追加するためにXAML プロセッサによって使用される `Add` のメソッドを入力します。  
  
> [!NOTE]
>  `Dictionary` の一般的な `List` とインターフェイスは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサによってコレクション検出では \(<xref:System.Collections.Generic.IList%601> と <xref:System.Collections.Generic.IDictionary%602> はサポートされていません。  一方、<xref:System.Collections.Generic.List%601> クラスおよび <xref:System.Collections.Generic.Dictionary%602> クラスを基本クラスとして使用することはできます。それぞれ、<xref:System.Collections.IList> と <xref:System.Collections.IDictionary> を直接実装しているためです。  
  
 コレクションを受け取るプロパティを宣言するときには、その型の新しいインスタンスでそのプロパティ値がどのように初期化されるかに注意する必要があります。  プロパティを依存関係プロパティとして実装しない場合は、コレクション型のコンストラクターを呼び出す補足フィールドを使用できます。  プロパティが依存関係プロパティの場合は、そのコレクション プロパティを既定の型コンストラクターの一部として初期化する必要がある可能性があります。  これは、依存関係プロパティはメタデータから既定値を受け取りますが、コレクション プロパティの初期値は、通常、共有された静的コレクションにはしないためです。  包含型のインスタンスごとにコレクション インスタンスが必要です。  詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
 コレクション プロパティにカスタム コレクション型を実装することもできます。  暗黙的なコレクション プロパティとして扱われるため、カスタム コレクション型では既定のコンストラクターを用意する必要はありません。既定のコンストラクターがなくても、XAML で暗黙的に使用できます。  ただし、コレクション型の既定のコンストラクターを用意することもできます。  これを実行することで、  既定のコンストラクターを用意しないと、そのコレクションをオブジェクト要素として明示的に宣言できない場合に役立てることができます。  マークアップ スタイルの問題から明示的なコレクションが好まれることもあります。  また、既定のコンストラクターを用意すると、そのコレクション型をプロパティ値として使用する新しいオブジェクトを作成するときの初期化要件が単純化されます。  
  
<a name="XAMLCONtent"></a>   
## XAML コンテンツ プロパティの宣言  
 XAML 言語で [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のコンテンツ プロパティの概念を定義します。  オブジェクト構文で使用できる各クラスは、XAML コンテンツ プロパティを 1 つだけ持つことができます。  プロパティをクラスの XAML コンテンツ プロパティとして宣言するには、クラス定義の一部として <xref:System.Windows.Markup.ContentPropertyAttribute> を適用し、  目的の XAML コンテンツ プロパティの名前をその属性の <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> として指定します。  プロパティは文字列でない <xref:System.Reflection.PropertyInfo> などのリフレクションの構造体として名前を指定します。  
  
 コレクション プロパティを XAML コンテンツ プロパティとして指定することもできます。  この結果、そのプロパティの使用方法で、コレクション オブジェクト要素やプロパティ要素のタグを間にはさまずに、オブジェクト要素に 1 つ以上の子要素を持たせることができます。  それらの要素は XAML コンテンツ プロパティの値として扱われ、対応するコレクション インスタンスに追加されます。  
  
 既存の XAML コンテンツ プロパティはプロパティ型を使用します `Object`。  この場合、XAML コンテンツ プロパティで、<xref:System.String> などのプリミティブ値も、1 つの参照オブジェクト値も受け取ることができます。  このモデルに従う場合は、型の判定や使用できる型の処理をその型で行う必要があります。  <xref:System.Object> コンテンツ タイプは一般に、オブジェクト コンテンツを文字列として追加する単純な手段と \(既定のプレゼンテーションが適用されます\)、既定以外のプレゼンテーションまたは追加データを指定するオブジェクト コンテンツを追加する高度な手段の両方をサポートする場合に使用されます。  
  
<a name="Serializing"></a>   
## XAML のシリアル化  
 一部のシナリオではなどのコントロールを作成する場合などXAML  でインスタンス化できるオブジェクト表現も同等の XAML マークアップによってシリアル化できるようにする必要があります。  シリアル化の要件については、ここでは説明しません。  詳細については、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」および「[要素のツリーおよびシリアル化](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md)」を参照してください。  
  
## 参照  
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [XAML 読み込みと依存関係プロパティ](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)