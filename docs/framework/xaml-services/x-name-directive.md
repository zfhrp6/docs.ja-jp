---
title: "x:Name Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "x:Name"
  - "xName"
  - "Name"
helpviewer_keywords: 
  - "x:Name attribute [XAML Services]"
  - "XAML [XAML Services], x:Name attribute"
  - "Name attribute in XAML [XAML Services]"
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
caps.latest.revision: 27
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 27
---
# x:Name Directive
XAML で定義された XAML 名前スコープ内の要素を一意に識別します。  XAML を基に作成されたオブジェクト グラフに対し実行時にアクセスする動作がフレームワークに実装されている場合、またはそのような API が存在する場合、XAML 名前スコープとその一意性モデルを、インスタンス化されたオブジェクトに適用することができます。  
  
## XAML 属性の使用方法  
  
```  
<object x:Name="XAMLNameValue".../>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`XAMLNameValue`|[XamlName の文法](../../../docs/framework/xaml-services/xamlname-grammar.md)の制限に準拠する文字列。|  
  
## 解説  
 フレームワークの基になるプログラミング モデルに適用後の `x:Name` は、コンストラクターによって返されるオブジェクト参照またはインスタンスを保持する変数と等価と見なすことができます。  
  
 `x:Name` ディレクティブの使用上、その値は、XAML 名前スコープ内で一意である必要があります。  既定では、.NET Framework XAML サービス API によって使用された場合、プライマリ XAML 名前スコープは、単一の XAML 稼動環境の XAML ルート要素で定義され、その XAML 稼動環境内の要素を含みます。  特定のシナリオに対応するために、フレームワークによって追加の個別の \(単一の XAML 稼動環境内に出現する\) XAML 名前スコープを定義できます。  たとえば、WPF では、新しい XAML 名前スコープも、その XAML 稼動環境で定義される任意のテンプレートによって定義および作成されます。  XAML 名前スコープの詳細 \(WPF に関して記述されていますが、多くの XAML 名前スコープの概念にも関連しています\) については、「[WPF XAML 名前スコープ](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)」を参照してください。  
  
 通常、`x:Name` は、`x:Key` も使用する状況には適用しないでください。  特定の既存フレームワークによる XAML 実装では、`x:Key` と `x:Name` の間に代替の概念を導入していますが、それは推奨されるプラクティスではありません。  .NET Framework XAML サービスでは、<xref:System.Windows.Markup.INameScope> や <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> などの名前\/キー情報を処理するときに、このような代替概念はサポートしていません。  
  
 `x:Name` の許可規則と名前の一意性の適用は、特定の実装フレームワークによって潜在的に定義されます。  ただし、.NET Framework XAML サービスと併用できるように、XAML 名前スコープの一意性に対するフレームワーク定義は、このドキュメントの <xref:System.Windows.Markup.INameScope> 情報の定義と整合性を維持し、その情報の適用先に関して同じ規則を使用する必要があります。  たとえば、[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 実装は、さまざまなマークアップ要素を個別の <xref:System.Windows.NameScope> 範囲 \(リソース ディクショナリ、ページ レベルの XAML によって作成された論理ツリー、テンプレート、その他の遅延コンテンツなど\) に分け、その後、各 XAML 名前スコープで XAML 名の一意性を適用します。  
  
 .NET Framework XAML サービス XAML オブジェクト ライターを使用するカスタム型の場合、型の `x:Name` にマッピングするプロパティを設定または変更できます。  この動作は、型定義コード内の <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> で、マッピングするプロパティの名前を参照することによって定義します。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> は型レベルの属性です。  
  
 .NET Framework XAML サービスを使用すると、<xref:System.Windows.Markup.INameScope> インターフェイスを実装することで、フレームワークに依存しない方法で、XAML 名前スコープをサポートするバッキング ロジックを定義できます。  
  
## WPF の使用上の注意  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの標準のビルド構成では、XAML、部分クラス、および分離コードを使用します。ここで指定した `x:Name` は、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] がマークアップ コンパイル ビルド タスクによって処理されるときに、基になるコードで生成されるフィールドの名前となり、そのフィールドはオブジェクトへの参照を保持します。作成されるフィールドは、既定では内部型です。  [x:FieldModifier 属性](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)を指定することによって、フィールド アクセスを変更できます。  WPF および Silverlight では、マークアップ コンパイルによって、まず部分クラスにフィールドが定義され、名前が付けられます。ただし、初期状態では値は空です。  次に、`InitializeComponent` という名前で生成されたメソッドがクラスのコンストラクター内から呼び出されます。  `InitializeComponent` は、一連の `FindName` 呼び出しで構成されます。このとき、部分クラスの XAML 定義部に存在する `x:Name` の値が、それぞれの呼び出しの入力文字列として使用されます。  その戻り値が同名のフィールド参照に代入され、XAML の解析に基づいて作成されたオブジェクトがフィールドの値として設定されます。  `InitializeComponent` が実行されることで、XAML で定義されたオブジェクトの参照が必要になったときに、`FindName` を明示的に呼び出さなくても、いつでも `x:Name`\/フィールド名を直接使用して、ランタイム オブジェクト グラフを参照できるようになります。  
  
 [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] のターゲットを使用し `Page` ビルド アクションを持つ XAML ファイルを含む WPF アプリケーションでは、個別の参照プロパティはコンパイル時に作成されます。このコンパイルでは、`x:Name` を持つすべての要素に `WithEvents` キーワードが追加され、イベント ハンドラー デリゲートの `Handles` 構文をサポートします。  このプロパティは常にパブリックです。  詳細については、「[Visual Basic と WPF のイベント処理](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)」を参照してください。  
  
 WPF XAML プロセッサは、`x:Name` を使用して、読み込み時に XAML 名前スコープに名前を登録します。これは、そのページが、ビルド アクションによってマークアップ コンパイルされない場合 \(たとえば、リソース ディクショナリの Loose XAML\) にも当てはまります。  このような動作になっているのは、<xref:System.Windows.Data.Binding.ElementName%2A> バインディングに `x:Name` が必要になる場合があるためです。  詳細については、「[データ バインドの概要](../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
 前述のとおり、`x:Name` \(または `Name`\) は、`x:Key` も使用する状況では適用しないでください。  [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> は、この動作を適用する方法として、自らを XAML 名前スコープとして定義するにもかかわらず、<xref:System.Windows.Markup.INameScope> API については Not Implemented または null 値を返すという特殊な動作をするためです。  XAML で定義された <xref:System.Windows.ResourceDictionary> 内に WPF XAML パーサーが `Name` または `x:Name` を検出した場合、いずれの XAML 名前スコープにも名前は追加されません。  その名前を XAML 名前スコープから見つけようとしても、`FindName` メソッドからは有効な結果は返されません。  
  
### x:Name および Name  
 WPF アプリケーションで `x:Name` 属性をまったく使用せずに済むケースも多くあります。これは、<xref:System.Windows.FrameworkElement> や <xref:System.Windows.FrameworkContentElement> などのいくつかの重要な基本クラスの既定の XAML 名前空間内で指定される `Name` 依存関係プロパティが、同じ機能を満たすからです。  それでも、フレームワーク レベルで `Name` プロパティのない要素へのコード アクセスが重要となる XAML および WPF の一般的なシナリオもあります。  たとえば、一部のアニメーション サポート クラスおよびストーリーボード サポート クラスは、`Name` プロパティをサポートしていません。しかし、アニメーションを制御するためには、多くの場合、それらをコード内で参照する必要があります。  XAML で作成するタイムラインと変換を後でコードから参照するには、その属性として `x:Name` を指定する必要があります。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> をクラスのプロパティとして使用できる場合、<xref:System.Windows.FrameworkElement.Name%2A> と `x:Name` のどちらも属性として使用できますが、両方を同じ要素で指定すると解析例外が発生します。  XAML をマークアップ コンパイルすると、マークアップ コンパイル時に例外が発生します。それ以外の場合は、読み込み時に例外が発生します。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> は、XAML 属性構文や <xref:System.Windows.DependencyObject.SetValue%2A> を使用するコードで設定できます。ただし、コードから <xref:System.Windows.FrameworkElement.Name%2A> プロパティを設定した場合、XAML が既に読み込まれているほとんどの状況では、これを表すフィールド参照が XAML 名前スコープ内に作成されない場合があるので注意してください。  コードに <xref:System.Windows.FrameworkElement.Name%2A> を設定する代わりに、コードから適切な名前スコープに対して <xref:System.Windows.NameScope> メソッドを使用します。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> は、内部テキストと一緒にプロパティ要素構文を使用して設定することもできますが、これは一般的ではありません。  対照的に、`x:Name` は、XAML プロパティ要素構文で設定したり、<xref:System.Windows.DependencyObject.SetValue%2A> を使用するコードで設定したりすることはできません。ディレクティブであるため、オブジェクトで要素の属性構文を使用する場合にのみ設定できます。  
  
## Silverlight の使用上の注意  
 Silverlight 用の `x:Name` に関しては、別途ドキュメントが用意されています。  詳細については、「[XAML 名前空間 \(x:\) 言語機能 \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkId=199081)」を参照してください。  
  
## 参照  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=fullName>   
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=fullName>   
 [WPF のツリー](../../../docs/framework/wpf/advanced/trees-in-wpf.md)