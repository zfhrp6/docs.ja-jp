---
title: "マークアップ拡張機能と WPF XAML | Microsoft Docs"
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
  - "*Extension クラス"
  - "バインディングのマークアップ拡張機能"
  - "中かっこ文字"
  - "文字, 中かっこ"
  - "クラス, MarkupExtension"
  - "中かっこ文字 ({})"
  - "DynamicResource のマークアップ拡張機能"
  - "リテラル中かっこ文字 ({})"
  - "マークアップ拡張機能"
  - "MarkupExtension クラス"
  - "入れ子 (拡張構文の)"
  - "RelativeSource のマークアップ拡張機能"
  - "StaticResource のマークアップ拡張機能"
  - "TemplateBinding のマークアップ拡張機能"
  - "XAML, マークアップ拡張機能"
ms.assetid: 618dc745-8b14-4886-833f-486d2254bb78
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# マークアップ拡張機能と WPF XAML
ここでは、構文規則、目的、およびその基になるクラス オブジェクト モデルを含む XAML のマークアップ拡張機能の概念について説明します。  マークアップ拡張機能は、XAML 言語、および XAML サービスの .NET 実装の一般的な機能です。  ここでは、WPF XAML で使用するマークアップ拡張機能について特に詳しく説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="XAML_Processors_and_Markup_Extensions"></a>   
## XAML プロセッサとマークアップ拡張機能  
 一般に、XAML パーサーは、属性値を、プリミティブに変換できるリテラル文字列として解釈するか、いくつかの方法でオブジェクトに変換できます。  そのような方法の 1 つは、型コンバーターを参照することです。この方法については、「[TypeConverters および XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)」で説明しています。  しかし、シナリオによっては、別の動作が必要な場合もあります。  たとえば、XAML プロセッサに対して、ある属性値がオブジェクト グラフの新しいオブジェクトにならないように指示することがあります。  この場合、属性は、オブジェクト グラフの別の部分にある既に構築したオブジェクト、または静的オブジェクトを参照するオブジェクト グラフにする必要があります。  別のシナリオとして、XAML プロセッサに対して、オブジェクトのコンストラクターに既定以外の引数を渡す構文を使用するように指示する場合もあります。このような種類のシナリオは、マークアップ拡張機能によって解決できます。  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## 基本的なマークアップ拡張構文  
 マークアップ拡張機能は、属性使用のプロパティ、プロパティ要素使用のプロパティ、またはこれらの両方に値を指定するために実装できます。  
  
 属性値を指定するために使用するときは、XAML プロセッサに対してマークアップ拡張機能を区別する構文として、始め中かっこと終わり中かっこ \({ および }\) が使用されます。  マークアップ拡張機能の種類は、次の始め中かっこの直後の文字列トークンによって識別されます。  
  
 プロパティ要素構文で使用する場合、マークアップ拡張機能は、プロパティ要素値を指定するために使用されるその他の要素と表示上は同じになります。つまり、山かっこ \(\<\>\) で囲まれたマークアップ拡張機能クラスを要素として参照する XAML 要素宣言になります。  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## XAML で定義されたマークアップ拡張機能  
 XAML の WPF 実装に固有ではなく、言語としての XAML の組み込みまたは機能の実装であるマークアップ拡張機能がいくつか存在します。  これらのマークアップ拡張機能は、一般的な .NET Framework XAML サービスの一部として System.Xaml アセンブリに実装され、XAML 言語の XAML 名前空間内にあります。  これらのマークアップ拡張機能は、一般的なマークアップの使用方法では、通常 `x:` プレフィックスで識別できます。  <xref:System.Windows.Markup.MarkupExtension> 基本クラス \(これも System.Xaml で定義されています\) には、WPF XAML に含まれる XAML リーダーと XAML ライターでマークアップ拡張機能がサポートされるようにするために、すべてのマークアップ拡張機能で使用する必要のあるパターンが用意されています。  
  
-   `x:Type` は、指定した型の <xref:System.Type> オブジェクトを示します。  この機能は、スタイルとテンプレートで最もよく使用されます。  詳細については、「[x:Type マークアップ拡張機能](../../../../docs/framework/xaml-services/x-type-markup-extension.md)」を参照してください。  
  
-   `x:Static` は、静的な値を生成します。  この値は、直接的にはプロパティの値の型ではなくても、その型に評価することができる値型コード エンティティから生成されます。  詳細については、「[x:Static のマークアップ拡張機能](../../../../docs/framework/xaml-services/x-static-markup-extension.md)」を参照してください。  
  
-   `x:Null` は、プロパティの値として `null` を指定し、属性またはプロパティ要素の値として使用できます。  詳細については、「[x:Null のマークアップ拡張機能](../../../../docs/framework/xaml-services/x-null-markup-extension.md)」を参照してください。  
  
-   `x:Array` は、XAML の構文での一般的な配列の作成をサポートします。WPF 基本要素とコントロール モデルで提供されているコレクションのサポートをあえて使用しない場合に使用します。  詳細については、「[x:Array のマークアップ拡張機能](../../../../docs/framework/xaml-services/x-array-markup-extension.md)」を参照してください。  
  
> [!NOTE]
>  `x:` プレフィックスは、XAML ファイルまたは稼働環境のルート要素において、組み込み XAML 言語の一般的な XAML 名前空間の割り当てに使用されます。  たとえば、WPF アプリケーション用の [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] テンプレートは、この `x:` の割り当てを使用して XAML ファイルを開始します。  独自の XAML 名前空間の割り当てで別のプレフィックスを選択できますが、このドキュメントでは、既定の WPF 名前空間、または特定のフレームワークに無関係である他の XAML 名前空間ではなく、XAML 言語用の XAML 名前空間の定義済みの部分であるエンティティを識別する方法として、既定の `x:` の割り当てを想定しています。  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## WPF 固有のマークアップ拡張機能  
 WPF プログラミングで最も一般的なマークアップ拡張機能には、リソース参照 \(`StaticResource` と `DynamicResource`\) をサポートする拡張機能と、データ バインディング \(`Binding`\) をサポートする拡張機能があります。  
  
-   `StaticResource` は、既に定義されているリソースの値を置き換えることによって、プロパティの値を指定します。  `StaticResource` の評価は、最終的に XAML 読み込み時に行われ、実行時にはオブジェクト グラフにアクセスできません。詳細については、「[StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)」を参照してください。  
  
-   `DynamicResource` は、リソースへの実行時参照として値の決定を遅延することによって、プロパティの値を指定します。  動的リソース参照では、このようなリソースにアクセスするたびに、強制的に新しいルックアップが行われ、実行時にオブジェクト グラフにアクセスできます。  このようにアクセスできるようにするために、`DynamicResource` の概念が、WPF プロパティ システムの依存関係プロパティ、および評価された式でサポートされます。  したがって、`DynamicResource` は依存関係プロパティ ターゲットにのみ使用できます。  詳細については、「[DynamicResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)」を参照してください。  
  
-   `Binding` は、実行時に親オブジェクトに適用されるデータ コンテキストを使用して、プロパティのデータ バインドされた値を指定します。  このマークアップ拡張機能では、データ バインディングを指定するためのインライン構文を大量に使用できるようになるため、比較的複雑です。  詳細については、「[バインドのマークアップ拡張機能](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)」を参照してください。  
  
-   `RelativeSource` は、ランタイム オブジェクト ツリーに存在する可能性のあるいくつかの関係をナビゲーションできる <xref:System.Windows.Data.Binding> に、ソース情報を指定します。  これにより、多目的のテンプレートで作成されるバインディング、または周囲のオブジェクト ツリーを完全には把握していないコードで作成されるバインディングのために、特殊なソース指定を行うことができます。  詳細については、「[RelativeSource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)」を参照してください。  
  
-   `TemplateBinding` は、コントロール テンプレートが、テンプレートを使用するクラスのオブジェクト モデル定義プロパティから取得される、テンプレートが適用されたプロパティの値を使用できるようにします。  つまり、テンプレート定義内のプロパティから、テンプレートが適用されたときしか存在しないコンテキストにアクセスできます。  詳細については、「[TemplateBinding のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)」を参照してください。  `TemplateBinding` の実際の使用方法の詳細については、[ControlTemplate を使用したスタイル設定のサンプル](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。  
  
-   `ColorConvertedBitmap` は、比較的高度なイメージング シナリオをサポートします。  詳細については、「[ColorConvertedBitmap のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/colorconvertedbitmap-markup-extension.md)」を参照してください。  
  
-   `ComponentResourceKey` および `ThemeDictionary` は、リソース ルックアップをサポートします。特に、カスタム コントロールと共にパッケージ化されるリソースおよびテーマを対象としています。  詳細については、「[ComponentResourceKey マークアップ拡張機能](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md)」、「[ThemeDictionary のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/themedictionary-markup-extension.md)」、または「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
<a name="StarExtension"></a>   
## \*Extension クラス  
 一般的な XAML 言語でも WPF 固有のマークアップ拡張機能でも、各マークアップ拡張機能の動作は、<xref:System.Windows.Markup.MarkupExtension> から派生する `*Extension` クラスを通じて XAML プロセッサに識別され、<xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> メソッドの実装を提供します。  各拡張機能が実装するこのメソッドは、マークアップ拡張機能の評価時に返されるオブジェクトを提供します。  返されるオブジェクトは、通常、マークアップ拡張機能に渡されたさまざまな文字列トークンに基づいて評価されます。  
  
 たとえば、<xref:System.Windows.StaticResourceExtension> クラスは、実際のリソース検索の外見的な実装を提供するため、その <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> 実装は必要なオブジェクトを返します。その際入力として、その実装の `x:Key` によってリソースを検索するために使用される文字列を使用します。  既存のマークアップ拡張機能を使用する場合は、この実装の詳細の大部分は重要ではありません。  
  
 一部のマークアップ拡張機能では、文字列トークン引数は使用されません。  これは、そのマークアップ拡張機能では静的な値や一貫した値が返されるため、または返される値のコンテキストが `serviceProvider` パラメーターを介して渡されるサービスの 1 つから得られるためです。  
  
 `*Extension` 名前付けパターンは、便宜上のものであり、一貫性を確保するためのものです。  XAML プロセッサがマークアップ拡張機能のサポートとしてそのクラスを識別するためには必要ではありません。  コードベースが System.Xaml を含んでいて、.NET Framework XAML サービスの実装を使用している限り、XAML マークアップ拡張機能として認識されるための要件は、<xref:System.Windows.Markup.MarkupExtension> から派生することと、構築構文をサポートすることだけです。  WPF には、`*Extension` 名前付けパターンに従わないマークアップ拡張機能対応のクラス \(たとえば <xref:System.Windows.Data.Binding>\) が定義されています。  通常、その理由は、クラスが純粋なマークアップ拡張機能のサポート以外のシナリオをサポートするためです。  <xref:System.Windows.Data.Binding> の場合、そのクラスは、XAML. とは無関係なシナリオにおけるオブジェクトのメソッドとプロパティへの実行時アクセスをサポートします。  
  
### 初期化テキストの拡張クラスの解釈  
 マークアップ拡張機能名の後に続き、まだ中かっこの中にある文字列トークンは、次の方法のいずれかで XAML プロセッサに解釈されます。  
  
-   コンマは常に個別のトークンの区切りまたは区切り記号を表します。  
  
-   個別の区切られたトークンに、等号が含まれない場合は、各トークンはコンストラクター引数として扱われます。  各コンストラクター パラメーターは、その署名で想定される型として、その署名で想定される適切な順序で指定する必要があります。  
  
    > [!NOTE]
    >  XAML プロセッサは、ペアの数の引数の数に一致するコンストラクターを呼び出す必要があります。  このため、カスタム マークアップ拡張機能を実装する場合は、複数のパラメーターに同じ引数の数を指定しないでください。  パラメーターの数が同じマークアップ拡張機能コンストラクター パスが複数存在する場合の XAML プロセッサの動作は定義されていません。ただし、マークアップ拡張機能の型定義がこのような状態になっていると、使用法に関する例外が XAML プロセッサーからスローされる可能性があることを想定しておく必要があります。  
  
-   個別の区切られたトークンに等号が含まれている場合、XAML プロセッサは最初にマークアップ拡張機能の既定のコンストラクターを呼び出します。  その後、各 "名前\=値" のペアは、マークアップ拡張機能に存在するプロパティ名、およびそのプロパティに割り当てられる値として解釈されます。  
  
-   マークアップ拡張機能において、コンストラクターの動作とプロパティの設定の動作に類似点がある場合は、どちらの動作を使用しても問題はありません。  複数の設定可能なプロパティを持つマークアップ拡張機能では、"*プロパティ*`=`*値*" のペアの方がよく使用されます。単に、その方がマークアップの意図が明確になり、コンストラクター パラメーターを間違って入れ替える可能性も低いためです   \("プロパティ\=値" のペアを指定した場合、それらのプロパティは任意の順序になります\)。また、マークアップ拡張機能によって、設定可能なプロパティのすべてを設定するコンストラクター パラメーターが提供されるという保証はありません。  たとえば、<xref:System.Windows.Data.Binding> は、多数のプロパティを持つマークアップ拡張機能であり、それらのプロパティは "*プロパティ*`=`*値*" の形式で拡張機能を使用することで設定できますが、<xref:System.Windows.Data.Binding> がサポートするコンストラクターは、既定のコンストラクターと初期パスを設定するコンストラクターの 2 つだけです。  
  
-   リテラルのコンマは、エスケープせずにマークアップ拡張機能に渡すことはできません。  
  
<a name="EscapeSequences"></a>   
## エスケープ シーケンスとマークアップ拡張機能  
 XAML プロセッサで処理する属性は、マークアップ拡張シーケンスのインジケーターとして中かっこを使用します。  必要に応じて、空の中かっこのペアとその後に続くリテラル中かっこを使用したエスケープ シーケンスを入力することによって、リテラル中かっこ文字属性値を生成することもできます。  「[{} エスケープ シーケンス\/マークアップ拡張機能](../../../../docs/framework/xaml-services/escape-sequence-markup-extension.md)」を参照してください。  
  
<a name="Nesting"></a>   
## XAML の使用におけるマークアップ拡張機能の入れ子  
 複数のマークアップ拡張機能を入れ子にすることができ、各マークアップ拡張は、最も深いものが最初に評価されます。  たとえば、次のような使用方法があります。  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
  
```  
  
 この使用方法では、`x:Static` ステートメントが最初に評価され、文字列を返します。  この文字列が、`DynamicResource` の引数として使用されます。  
  
## マークアップ拡張機能とプロパティ要素の構文  
 マークアップ拡張機能クラスは、プロパティ要素値を設定するオブジェクト要素として使用した場合、XAML で使用可能な通常の型に基づくオブジェクト要素と見た目上は区別できません。  通常のオブジェクト要素とマークアップ拡張機能の実用上の違いは、マークアップ拡張機能は、型指定された値に評価されるか、または式として処理が遅延されることです。  したがって、マークアップ拡張機能のプロパティ値について発生する可能性のある型エラーのメカニズムは異なります。これは、他のプログラミング モデルにおける遅延バインディング プロパティの処理方法と似ています。  通常のオブジェクト要素では、XAML が解析されるとき、その要素で設定しているターゲット プロパティに対して型の一致が評価されます。  
  
 ほとんどのマークアップ拡張機能は、プロパティ要素を指定するオブジェクト要素構文で使用される場合、内側にコンテンツや他のプロパティ要素の構文を含みません。  このため、オブジェクト要素タグを閉じ、子要素は指定しません。  オブジェクト要素が XAML プロセッサで検出されるたびに、そのクラスのコンストラクターが呼び出され、解析された要素から作成されたオブジェクトをインスタンス化します。  マークアップ拡張機能クラスも同じです。マークアップ拡張機能をオブジェクト要素構文で使用できるようにする場合は、既定のコンストラクターを用意する必要があります。  既存のマークアップ拡張機能の中には、有効な初期化のために指定する必要のある必須プロパティ値を少なくとも 1 つ持っているものがあります。  その場合、通常、そのプロパティ値はオブジェクト要素のプロパティ属性として指定されます。  「[XAML 名前空間 \(x:\) 言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)」および「[WPF XAML 拡張機能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)」の各リファレンス ページで、必須プロパティを持つマークアップ拡張機能 \(および必須プロパティの名前\) について説明します。  リファレンス ページでは、オブジェクト要素構文と属性構文のどちらかが特定のマークアップ拡張機能に対して許可されない場合についても説明します。  特に注意する必要があるケースは、[x:Array のマークアップ拡張機能](../../../../docs/framework/xaml-services/x-array-markup-extension.md)です。この場合、その配列の内容をタグ設定でコンテンツとして指定する必要があるため、属性構文をサポートできません。  配列の内容は一般的なオブジェクトとして扱われるため、属性の既定の型コンバーターは使用できません。  また、[x:Array のマークアップ拡張機能](../../../../docs/framework/xaml-services/x-array-markup-extension.md)には `type` パラメーターが必要です。  
  
## 参照  
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [XAML 名前空間 \(x:\) 言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)   
 [WPF XAML 拡張機能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)   
 [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)   
 [バインドのマークアップ拡張機能](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)   
 [DynamicResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)   
 [x:Type マークアップ拡張機能](../../../../docs/framework/xaml-services/x-type-markup-extension.md)