---
title: WPF における XAML とカスタム クラス
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7aa7ffe38f1fbd7de71dbc95ae12b8faca6e356
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="xaml-and-custom-classes-for-wpf"></a>WPF における XAML とカスタム クラス
実装されている XAML[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]フレームワークは、いずれかでカスタムのクラスまたは構造体を定義する機能をサポートしている[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]言語、およびしアクセス クラスの XAML マークアップを使用しています。 組み合わせを使用できる[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の XAML 名前空間プレフィックスをカスタムの型をマップして、通常の型と同じマークアップ ファイル内でカスタム型を定義します。 このトピックでは、カスタムのクラスは、XAML 要素として使用できるように満たす必要がある要件について説明します。  
  
 
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>アプリケーションまたはアセンブリのカスタム クラス  
 2 つの方法で XAML で使用されるカスタム クラスを定義することができます。 分離コードまたはその他のプライマリを生成するコード内で[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーション、または実行可能ファイルなどの別のアセンブリ内のクラスまたはクラス ライブラリとして使用される DLL として。 これらの方法は、特定の長所と短所がします。  
  
-   クラス ライブラリを作成する利点は、このようなカスタム クラスを異なる多くのアプリケーション間で共有できることです。 別のライブラリもとしてアプリケーションのバージョン管理の問題を簡単にコントロールをここで、目的のクラスの使用状況は、XAML ページ上のルート要素としては、クラスの作成を簡略化します。  
  
-   アプリケーションでカスタム クラスを定義する利点は、この手法は比較的軽量され、展開とメインのアプリケーション実行可能ファイルを超える個別のアセンブリを導入するときに発生するテストの問題を最小限に抑えられます。  
  
-   同じまたは別のアセンブリで定義されているかどうか、カスタム クラスを XAML では要素として使用するために CLR 名前空間と XML 名前空間の間でマップする必要があります。 参照してください[XAML 名前空間と WPF XAML 向け Namespace マッピング](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)です。  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>XAML 要素としてカスタム クラスの要件  
 オブジェクト要素としてインスタンス化できるようにするには、ために、クラスは、次の要件を満たす必要があります。  
  
-   カスタム クラスは、パブリックおよび既定 (パラメーターなし) のコンス トラクターをサポートする必要があります。 (次の構造に関する注意事項のセクションを参照してください)。  
  
-   カスタム クラスでは、入れ子になったクラスをすることはできません。 入れ子になったクラスおよびその一般的な CLR 使用法の構文で「ドット」が他の干渉[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]やアタッチされるプロパティなどの XAML 機能します。  
  
 オブジェクトの定義はオブジェクト要素の構文を有効にするだけでなく、そのオブジェクトの値の型として取得するその他のパブリック プロパティのプロパティ要素構文も可能です。 これは、オブジェクトがオブジェクト要素としてインスタンス化するようになりましたことができます、このようなプロパティのプロパティ要素の値を入力することもできるためです。  
  
### <a name="structures"></a>構造体  
 カスタムの型がで XAML で構築することが常として定義する構造体[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。これは、ため、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]コンパイラが暗黙的にすべてのプロパティ値を既定値を初期化する構造体の既定のコンス トラクターを作成します。 場合によっては、既定の構築動作やオブジェクト要素の使用法、構造体は望ましくありません。 構造体では、値と関数を概念的には、共用体、含まれる値は相互に排他的な解釈が可能性があります、そのため、プロパティのいずれも、設定可能な可能性があります。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]このような構造の例は、<xref:System.Windows.GridLength>です。 一般に、このような構造は、値は、さまざまな解釈や構造体の値のモードを作成する文字列の規則を使用して、属性の形式で表現できるように、型コンバーターを実装する必要があります。 構造体には、既定以外のコンス トラクターを使用してコード構築の同様の動作も公開する必要があります。  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>XAML 属性としてカスタム クラスのプロパティの要件  
 プロパティは、(プリミティブ) など、値の型を参照または既定のコンス トラクターまたは、XAML プロセッサがアクセスできる専用の型コンバーターのいずれかを持つ型にクラスを使用する必要があります。 CLR の XAML 実装で XAML プロセッサか見つける言語プリミティブのネイティブ サポート、またはアプリケーションの使用は、このようなコンバーター<xref:System.ComponentModel.TypeConverterAttribute>型またはメンバーの種類の定義をバックアップする  
  
 または、参照することも、抽象クラス型またはインターフェイス。 抽象クラスまたはインターフェイスは、XAML 解析時に、予想インターフェイスを実装する実際的なクラスのインスタンスまたは抽象クラスから派生した型のインスタンスでプロパティの値を入力する必要があります。  
  
 プロパティは、抽象クラスで宣言することができますが、抽象クラスから派生するクラスでのみ設定できます。 これは、クラスにパブリックの既定のコンス トラクターが必要なすべてのクラスのオブジェクトの要素を作成するためです。  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>TypeConverter 属性構文は有効になっています。  
 クラス レベルで、属性付きの専用の型コンバーターを提供する場合、適用される型変換はその型のインスタンスを作成する必要がある任意のプロパティの属性の構文を使用できます。 型コンバーターは、型のオブジェクト要素の使用を有効にしません。その型の既定のコンス トラクターが存在するだけでは、オブジェクト要素の使用方法を使用できます。 そのため、型コンバーターによって有効になっているプロパティは、その型自体では、オブジェクトの要素の構文もサポートしていない限り一般にプロパティの構文では使用できません。 この例外は、プロパティ要素構文では、指定しますが、プロパティ要素に文字列を含めることができますです。 使用状況は、属性の構文の使用方法に非常に基本的に相当し、属性の値のより堅牢な空白の処理の必要性がない限りは一般的ではありません。 たとえば、次に示しますプロパティ要素の使用、文字列を受け取ると、属性の使用方法と同じ。  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 属性の構文が許可されているオブジェクトの要素を含むプロパティ要素構文が XAML で許可されていないプロパティの例としては、さまざまなプロパティを<xref:System.Windows.Input.Cursor>型です。 <xref:System.Windows.Input.Cursor>クラスには専用の型コンバーター <xref:System.Windows.Input.CursorConverter>、既定のコンス トラクターを公開しないため、<xref:System.Windows.FrameworkElement.Cursor%2A>プロパティのみ設定できます属性構文でも、実際<xref:System.Windows.Input.Cursor>型は参照型です。  
  
### <a name="per-property-type-converters"></a>プロパティごとに型コンバーター  
 代わりに、プロパティ自体は、プロパティ レベルで実行する型コンバーターを宣言する場合があります。 これにより、入力として受信する属性の文字列値を処理することでプロパティ インラインの型のオブジェクトをインスタンス化"ミニ language"、<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>操作、適切な型に基づきます。 便利なアクセサーを提供するこれは、通常 XAML でのプロパティ設定を有効にする唯一の手段としてにないとします。 ただし、既存を使用する属性の型コンバーターを使用することはも[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]既定のコンス トラクターまたは属性付く型コンバーターのいずれかを指定しない型です。 例を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API は、特定のプロパティを<xref:System.Globalization.CultureInfo>型です。 この場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]既存の Microsoft .NET Framework を使用する<xref:System.Globalization.CultureInfo>より以前のバージョンのフレームワークを使用した互換性と移行のシナリオに対応する型が、<xref:System.Globalization.CultureInfo>型では、必要なはサポートされていませんでしたコンス トラクターまたは使用できるように、XAML のプロパティの値として直接型レベルの型変換。  
  
 XAML の使用方法のプロパティを公開するときにコントロール作成者の場合に特にする必要があります強く依存関係プロパティを使用してそのプロパティをバックアップします。 既存の使用する場合に特に[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、XAML プロセッサの実装を使用してパフォーマンスを向上させることができますので<xref:System.Windows.DependencyProperty>バックアップを作成します。 依存関係プロパティには、XAML のアクセス可能なプロパティの予想される、プロパティのプロパティ システムの機能が公開されます。 これには、アニメーション、データ バインディング、およびスタイルのサポートなどの機能が含まれます。 詳細については、次を参照してください。[依存関係プロパティのカスタム](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)と[XAML 読み込みと依存関係プロパティ](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)です。  
  
### <a name="writing-and-attributing-a-type-converter"></a>作成と実行する型コンバーターを割り当て  
 場合によっては、書き込む必要があるカスタム<xref:System.ComponentModel.TypeConverter>プロパティの型の型の変換を提供するクラスを派生します。 派生し、XAML の使用をサポートする型コンバーターを作成する方法および適用する方法について、<xref:System.ComponentModel.TypeConverterAttribute>を参照してください[TypeConverters と XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)です。  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>カスタム クラスのイベントで XAML のイベント ハンドラー属性の構文の要件  
 として使用できるように、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]イベント、イベントは既定のコンス トラクターをサポートするクラスでイベントをパブリックとして公開する必要がありますか、イベントを派生クラスでアクセスできるクラスを抽象にします。 ルーティングされたイベントで簡単に使用するために、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]イベントを明示的に実装する必要があります`add`と`remove`を追加および用のハンドラーを削除する方法、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]イベントのシグネチャ、にこれらのハンドラーを前後<xref:System.Windows.UIElement.AddHandler%2A>と<xref:System.Windows.UIElement.RemoveHandler%2A>メソッドです。 これらのメソッドを追加またはにイベントが関連付けられているインスタンスにルーティング イベント ハンドラーのストアには、ハンドラーを削除します。  
  
> [!NOTE]
>  ハンドラーを使用して、ルーティングされたイベントを直接登録することは<xref:System.Windows.UIElement.AddHandler%2A>は意図的に定義して、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]ルーティング イベントを公開するイベントです。 これは通常、しないでイベントは、ハンドラーをアタッチするため、XAML 属性の構文を有効にしないと、結果として得られるクラスが提供される型の機能の透明度が減少 XAML ビュー。  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>コレクション プロパティの作成  
 コレクションの種類を取得するプロパティには、コレクションに追加されるオブジェクトを指定することができます XAML 構文があります。 この構文では、2 つの主な機能があります。  
  
-   コレクション オブジェクトであるオブジェクトは、オブジェクトの要素の構文で指定する必要はありません。 コレクション型を受け取る XAML のプロパティを指定するには、そのコレクションの種類の存在は暗黙の型です。  
  
-   マークアップでコレクション プロパティの子要素は、コレクションのメンバーに処理されます。 通常は、コレクションのメンバーにコード アクセスは、リストのディクショナリ/メソッドを介して実行など`Add`、またはインデクサーを使用します。 メソッドまたはインデクサーは、XAML 構文でサポートされていません (例外: を参照してください。 XAML 2009 は、メソッドをサポートできますが、XAML 2009 を使用可能な WPF の使用法を制限[XAML 2009 言語機能](../../../../docs/framework/xaml-services/xaml-2009-language-features.md))。 コレクションは、要素のツリーを構築するため、非常に一般的な要件と、何らかの方法を宣言型の XAML でこれらのコレクションを設定する必要があります。 そのため、コレクション プロパティの子要素は、コレクション プロパティの型の値であるコレクションに追加して処理されます。  
  
 .NET Framework XAML サービス実装であるため、WPF XAML プロセッサは、コレクション プロパティの構成内容を次の定義を使用します。 プロパティのプロパティの型は、次のいずれかで実装する必要があります。  
  
-   実装して<xref:System.Collections.IList>です。  
  
-   実装して<xref:System.Collections.IDictionary>または同等のジェネリック (<xref:System.Collections.Generic.IDictionary%602>)。  
  
-   派生した<xref:System.Array>(XAML での配列の詳細については、次を参照してください[X:array のマークアップ拡張機能](../../../../docs/framework/xaml-services/x-array-markup-extension.md)。)。  
  
-   実装して<xref:System.Windows.Markup.IAddChild>(インターフェイスによって定義された[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)])。  
  
 CLR でこれらの型のそれぞれが、`Add`メソッドで、XAML プロセッサによって、オブジェクト グラフを作成するときに、基になるコレクションに項目を追加するために使用します。  
  
> [!NOTE]
>  ジェネリック`List`と`Dictionary`インターフェイス (<xref:System.Collections.Generic.IList%601>と<xref:System.Collections.Generic.IDictionary%602>) によってコレクションの検出はサポートされていません、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサ。 ただし、使用することができます、<xref:System.Collections.Generic.List%601>を基底クラスとしてクラスを実装するため<xref:System.Collections.IList>直接、または<xref:System.Collections.Generic.Dictionary%602>を基底クラスとして実装するため<xref:System.Collections.IDictionary>直接です。  
  
 コレクションを受け取るプロパティを宣言する場合は、そのプロパティ値を型の新しいインスタンスを初期化する方法について注意します。 依存関係プロパティとしてプロパティを実装していない場合は、コレクション型のコンス トラクターを呼び出すバッキング フィールドを使用してプロパティを持つ十分です。 プロパティが依存関係プロパティの場合は、既定の型コンス トラクターの一部として、コレクション プロパティを初期化する必要があります。 これは依存関係プロパティのメタデータから既定値は、通常たくない、静的で共有のコレクションであるコレクション プロパティの初期値です。 包含型のインスタンスごとに、コレクション インスタンスを設定する必要があります。 詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
 コレクション プロパティにカスタム コレクション型を実装することができます。 暗黙的なコレクション プロパティの処理のため、カスタム コレクション型は XAML で暗黙的に使用するために既定のコンス トラクターを提供するには必要ありません。 ただし、コレクション型の既定のコンス トラクターを必要に応じて指定できます。 指定できます。 既定のコンス トラクターを用意する場合を除き、オブジェクト要素としてコレクションを明示的に宣言することはできません。 一部のマークアップの作成者たいマークアップ スタイルの問題として、明示的なコレクションを参照してください。 既定のコンス トラクターは、プロパティ値としてコレクション型の型を使用する新しいオブジェクトを作成するときに、初期化要件を簡略化できます。  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>XAML コンテンツ プロパティを宣言します。  
 XAML 言語の概念を定義する、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コンテンツ プロパティです。 オブジェクトの構文では使用する各クラスには、ただ 1 つの XAML コンテンツ プロパティを持つことができます。 クラスの XAML コンテンツ プロパティであるプロパティを宣言するには、適用、<xref:System.Windows.Markup.ContentPropertyAttribute>クラス定義の一部として。 としての目的の XAML コンテンツ プロパティの名前を指定、<xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A>属性にします。 プロパティは文字列として指定、名前でリフレクション コンストラクトではなくなど<xref:System.Reflection.PropertyInfo>です。  
  
 XAML コンテンツ プロパティであるコレクション プロパティを指定することができます。 これは、結果、オブジェクト要素が介在するコレクション オブジェクトの要素またはプロパティ要素タグを行わなくても、1 つまたは複数の子要素を持つ、そのプロパティの使用率。 これらの要素は、XAML コンテンツ プロパティの値として扱われます、バッキング コレクション インスタンスに追加します。  
  
 いくつかの既存の XAML コンテンツ プロパティのプロパティの型を使用して`Object`です。 これにより、XAML コンテンツなどのプリミティブが実行できるプロパティ値、<xref:System.String>だけでなく、1 つの参照オブジェクトの値を取得します。 このモデルを実行する場合、型は型の判定と使用可能な型の処理を担当になります。 一般的な理由、<xref:System.Object>コンテンツの型を文字列として (既定のプレゼンテーションの処理方法を受け取ります)、オブジェクトのコンテンツを追加する、両方の簡単な手段をサポートするか、または高度な手段を追加するオブジェクトの既定以外のプレゼンテーションを指定するコンテンツまたは追加のデータ。  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>XAML シリアル化します。  
 場合など、特定のシナリオをコントロールの作成者は、XAML でインスタンス化できる任意のオブジェクト表現は、同等の XAML マークアップにもシリアル化できるようにすることもできます。 シリアル化の要件は、このトピックでは説明しません。 参照してください[作成の概要を制御](../../../../docs/framework/wpf/controls/control-authoring-overview.md)と[要素ツリーおよびシリアル化](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md)です。  
  
## <a name="see-also"></a>関連項目  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [XAML 読み込みと依存関係プロパティ](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)
