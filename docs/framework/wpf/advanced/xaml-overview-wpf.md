---
title: "XAML の概要 (WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interfaces [XAML]
- classes [XAML]
- root element [XAML]
- XAML [WPF], about XAML
- base classes [XAML]
- routed events [WPF]
- code-behind files [WPF], XAML
- collection properties [XAML]
- events [XAML]
- property element [XAML]
- content models [XAML]
- Extensible Application Markup Language (see XAML)
- attribute syntax [XAML]
ms.assetid: a80db4cd-dd0f-479f-a45f-3740017c22e4
caps.latest.revision: "57"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24ad84c604921e4dd33e818c0b80d8ab315cd58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-overview-wpf"></a>XAML の概要 (WPF)
このトピックは、XAML 言語の機能について説明し、書き込む XAML を使用する方法について説明[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションです。 具体的には、このトピックにはによって実装される XAML について説明します[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 XAML 自体よりも大きい言語の概念は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。  
  
  
  
<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>XAML とは何ですか。  
 XAML は、宣言型マークアップ言語です。 適用されると、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]プログラミング モデル、XAML 作成を簡略化、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]アプリケーションです。 表示を作成することができます[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]宣言型の XAML マークアップでとし、別の要素、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]部分クラス定義を使用するマークアップに参加している分離コード ファイルを使用して実行時のロジックを定義します。 XAML は、直接バッキング アセンブリで定義されている型の特定のセット内のオブジェクトをインスタンス化を表します。 これは、ほとんど他のマークアップ言語には、通常、バッキング型システムに直接同順せず、解釈された言語とは異なりします。 XAML は、別のパーティがで作業できるワークフローを使用する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]および可能性のあるさまざまなツールを使用して、アプリケーションのロジックです。  
  
 XAML ファイルは、一般にある XML ファイルでテキストとして表されている、`.xaml`拡張機能です。 任意の XML エンコードしますが、utf-8 は一般的なエンコードしてファイルをエンコードすることができます。  
  
 次の例は、ボタンの一部として作成する方法を示しています、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 この例は XAML で一般的な表現方法のフレーバーをすることを目的としていますだけ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]プログラミング要素 (完全なサンプルではありません)。  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>XAML 構文の概要  
 次のセクションでは、XAML 構文の基本的な形式を説明し、短いマークアップの例を提供します。 これらのセクションでは、これらをバッキング型システムでの表現する方法など、各の構文形式の完全な情報を提供するものではありません。 このトピックで導入された、構文の各の XAML 構文の仕様に関する詳細については、次を参照してください。 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)です。  
  
 以降のセクションの内容の多くは、XML 言語に精通していればするには、基本的になります。 これは、XAML の基本的なデザインの原則の 1 つの結果です。  XAML 言語には、独自の概念が定義されていますが、XML 言語、およびマークアップ フォーム内でこれらの概念の作業です。  
  
### <a name="xaml-object-elements"></a>XAML オブジェクト要素  
 Object 要素は、通常、型のインスタンスを宣言します。 その型は、バッキング型を言語としての XAML を使用するテクノロジを提供するアセンブリで定義されます。  
  
 オブジェクトの要素の構文は、常に始め山かっこで始まります (\<)。 これが続く型の名前、インスタンスを作成します。 (名前は、プレフィックスは後で説明する概念を含めることができます可能性があります)。その後、オブジェクト要素の属性をオプションで宣言できます。 完了するにはオブジェクト要素のタグの終わりには、終わりの山かっこ (>)。 代わりにスラッシュでタグを完了して、終わり山かっこを連続してによって、コンテンツを持たない自己終了フォームを使用できます (/>)。 たとえば、前に示したマークアップ スニペットは、もう一度見てください。  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 2 つのオブジェクトの要素を指定します: `<StackPanel>` (とコンテンツ、終了タグを後で)、および`<Button .../>`(自己終了フォームをいくつかの属性を持つ)。 Object 要素`StackPanel`と`Button`で定義されているクラスの名前にそれぞれマップ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の一部となって、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ。 オブジェクト要素のタグを指定する場合は、xaml の新しいインスタンスを作成する処理命令を作成します。 各インスタンスは、解析と XAML を読み込み時に、基になる型の既定のコンス トラクターを呼び出すことによって作成されます。  
  
### <a name="attribute-syntax-properties"></a>属性構文 (プロパティ)  
 オブジェクトのプロパティは、オブジェクト要素の属性としてよく表現できます。 属性構文は名前属性の構文、後ろに代入演算子 (=) で設定されるプロパティです。 属性の値は常に、引用符内に含まれる文字列として指定します。  
  
 属性構文はプロパティの設定の最も簡潔な構文であり、開発者、過去のマークアップ言語を使用しているユーザーに使用する最も簡単な構文です。 次のマークアップが赤いテキストと表示テキストとして指定だけでなく青色の背景を持つボタンを作成するなど、`Content`です。  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>プロパティ要素構文  
 オブジェクト要素のいくつかのプロパティでは、属性の構文ではありません、可能なオブジェクトまたはプロパティ値を提供するために必要な情報を二重引用符と属性の構文の文字列の制限内で適切に表現できません。 このような場合、プロパティ要素構文と呼ばれる別の構文を使用していることができます。  
  
 プロパティ要素の開始タグの構文は、 `<` *typeName*`.`*propertyName*`>`です。 一般に、そのタグの内容は、そのプロパティがその値として受け取る型のオブジェクト要素です。 コンテンツを指定してから、終了タグを持つプロパティ要素を閉じる必要があります。 終了タグの構文は、 `</` *typeName*`.`*propertyName*`>`です。  
  
 属性構文が可能な場合は、属性の構文を使用して通常方が便利ですよりコンパクトなマークアップしますが、多くの場合、スタイル、技術的な制限ではないだけで済みます。 次の例では、すべてのプロパティのプロパティ要素構文を使用して、前の属性の構文の例が、この時間のように設定されている同じプロパティ、`Button`です。  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>コレクションの構文  
 XAML 言語よりわかりやすいマークアップを生成するいくつかの最適化が含まれています。 このような最適化は 1 つです。 特定のプロパティは、コレクション型をコレクションのプロパティの値になる部分内の子要素としてのマークアップで宣言する項目。 ここで子オブジェクトの要素のコレクションは、コレクション プロパティに設定されている値です。  
  
 次の例の値の設定のコレクション構文を示しています、<xref:System.Windows.Media.GradientBrush.GradientStops%2A>プロパティ。  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->  
    <GradientStop Offset="0.0" Color="Red" />  
    <GradientStop Offset="1.0" Color="Blue" />  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
### <a name="xaml-content-properties"></a>XAML コンテンツ プロパティ  
 XAML では、クラスを指定、XAML コンテンツ プロパティは、そのプロパティの 1 つだけで、言語の機能を指定します。 そのオブジェクト要素の子要素は、そのコンテンツ プロパティの値の設定に使用されます。 つまり、コンテンツのプロパティの一意に、XAML マークアップでそのプロパティを設定すると、プロパティ要素を省略でき、マークアップで見やすい親/子比喩を生成できます。  
  
 たとえば、<xref:System.Windows.Controls.Border>のコンテンツ プロパティを指定<xref:System.Windows.Controls.Decorator.Child%2A>です。 次の 2 つ<xref:System.Windows.Controls.Border>要素は同一に扱われます。 1 つ目は、コンテンツ プロパティの構文を利用し、省略、`Border.Child`プロパティ要素。 2 番目の例を示しています`Border.Child`明示的にします。  
  
```xaml  
<Border>  
  <TextBox Width="300"/>  
</Border>  
<!--explicit equivalent-->  
<Border>  
  <Border.Child>  
    <TextBox Width="300"/>  
  </Border.Child>  
</Border>  
```  
  
 原則として、XAML 言語の XAML コンテンツ プロパティの値を指定してください前に、またはその他のすべてのプロパティ要素の後に完全に、そのオブジェクト。 たとえば、次のマークアップはコンパイルされません。  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 XAML コンテンツ プロパティでこの制限に関する詳細については、の「XAML コンテンツ プロパティ」セクションを参照してください。 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)です。  
  
### <a name="text-content"></a>テキストの内容  
 XAML 要素の数が少ないは、そのコンテンツとしてテキストを直接処理できます。 これを有効にするのには、次の場合のいずれかの必要があります。  
  
-   クラスは、コンテンツのプロパティを宣言する必要があり、コンテンツ プロパティが文字列に割り当てることができる型である必要があります (型になります<xref:System.Object>)。 インスタンスのいずれか<xref:System.Windows.Controls.ContentControl>を使用して<xref:System.Windows.Controls.ContentControl.Content%2A>型は、そのコンテンツのプロパティとして<xref:System.Object>、実用的で次の使用法をサポートしているこのと<xref:System.Windows.Controls.ContentControl>など、 <xref:System.Windows.Controls.Button>:`<Button>Hello</Button>`です。  
  
-   型は、ケースのテキストの内容がその型コンバーターの初期化のテキストとして使用される、型コンバーターを宣言する必要があります。 たとえば、`<Brush>Blue</Brush>` のようにします。 この場合は、実際にはあまり一般的です。  
  
-   種類は、既知の XAML 言語プリミティブである必要があります。  
  
### <a name="content-properties-and-collection-syntax-combined"></a>コンテンツのプロパティとコレクション構文の組み合わせ  
 次の例について考えます。  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 ここでは、各<xref:System.Windows.Controls.Button>の子要素は、<xref:System.Windows.Controls.StackPanel>です。 これは、2 つのさまざまな理由で 2 つのタグを省略する簡素化されたで直感的なマークアップです。  
  
-   **省略された StackPanel.Children プロパティ要素:** <xref:System.Windows.Controls.StackPanel>から派生した<xref:System.Windows.Controls.Panel>です。 <xref:System.Windows.Controls.Panel>定義<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>としての XAML コンテンツ プロパティです。  
  
-   **省略された UIElementCollection オブジェクト要素:** 、<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>プロパティは、型を受け取り<xref:System.Windows.Controls.UIElementCollection>を実装する<xref:System.Collections.IList>です。 コレクションの処理などの XAML 規則に基づいて、コレクションの要素のタグを省略できます<xref:System.Collections.IList>です。 (この場合、<xref:System.Windows.Controls.UIElementCollection>実際にインスタンス化できない既定のコンス トラクターでは、公開されず、理由があるため、<xref:System.Windows.Controls.UIElementCollection>オブジェクトの要素をコメント化されて表示)。  
  
```xaml  
<StackPanel>  
  <StackPanel.Children>  
    <!--<UIElementCollection>-->  
    <Button>First Button</Button>  
    <Button>Second Button</Button>  
    <!--</UIElementCollection>-->  
  </StackPanel.Children>  
</StackPanel>  
```  
  
### <a name="attribute-syntax-events"></a>属性構文 (イベント)  
 属性構文は、メンバー プロパティではなく、イベントに対しても使用できます。 ここでは、属性の名前は、イベントの名前です。 XAML のイベントの WPF 実装には、属性の値は、そのイベントのデリゲートを実装するハンドラーの名前です。 たとえば、次のマークアップがのハンドラーを割り当てます、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントを<xref:System.Windows.Controls.Button>マークアップで作成します。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 イベントと wpf XAML 属性の構文の例だけをよりがあります。 たとえば、でしょうか新機能、`ClickHandler`表し、定義方法、ここで参照されています。 これについては、次回[イベントと XAML コード ビハインド](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#events_and_xaml_codebehind)このトピックの「します。  
  
<a name="case_and_whitespace_in_xaml"></a>   
## <a name="case-and-whitespace-in-xaml"></a>ケース テーブルと XAML 内の空白文字  
 XAML は、大文字小文字を区別は一般にします。 バッキング型の解決のために、WPF XAML は、CLR は大文字小文字を区別する、同じルールで大文字小文字を区別します。 による機密性の高い大文字と小文字で名前を付けて、基になるアセンブリの型、または型のメンバーを比較した場合に、オブジェクトの要素、プロパティ要素および属性名のすべてを指定してください。 XAML 言語のキーワードとのプリミティブも大文字と小文字はします。 値は、常に大文字小文字を区別はありません。 値の大文字小文字の区別を値、またはプロパティの値の型を受け取るプロパティに関連付けられている型コンバーターの動作は異なります。 使用するプロパティなど、<xref:System.Boolean>型には、次`true`または`True`ネイティブの WPF XAML パーサーは入力文字列に変換するためにのみ、同等の値として<xref:System.Boolean>既にこれらの同等として許可します。  
  
 WPF XAML プロセッサとシリアライザーを無視するか、意味のすべての空白を削除しは、重要な空白を正規化します。 これは、XAML の仕様の既定の空白の動作の推奨設定と一致します。 この動作は、通常 XAML コンテンツ プロパティ内の文字列を指定した場合ののみです。 簡単に言うでは、XAML が、スペースにスペース、改行、タブ文字を変換し、場合領域のいずれかが保存されますが、連続する文字列の先頭または末尾を見て、します。 XAML の空白の処理の詳しい説明については、このトピックでは説明しません。 詳細については、「 [XAML での空白の処理](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)です。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>マークアップ拡張機能  
 マークアップ拡張機能は、XAML 言語概念です。 属性構文、中かっこの値を指定するために使用する場合 (`{`と`}`) マークアップ拡張機能の使用方法を示します。 これにより、XAML の処理がエスケープ、一般的な属性値のリテラル文字列または文字列に変換できる値のいずれかとして処理されます。  
  
 使用される最も一般的なマークアップ拡張[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション プログラミングは[バインディング](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)データ バインディング式、およびリソースの参照のために使用される[StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)と[DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)です。 マークアップ拡張機能を使用するには、そのプロパティが属性構文を一般にサポートしない場合でも、プロパティの値を指定するのに属性の構文を使用できます。 多くの場合、マークアップ拡張機能では、中間式の型を使用して、値を遅らせることや、実行時に存在するその他のオブジェクトを参照するなどの機能を有効にします。  
  
 次のマークアップがの値を設定するなど、<xref:System.Windows.FrameworkElement.Style%2A>プロパティ属性の構文を使用します。 <xref:System.Windows.FrameworkElement.Style%2A>プロパティがのインスタンスを受け取り、<xref:System.Windows.Style>クラスは、既定では、属性の構文の文字列によってインスタンス化できませんでした。 この場合、属性を参照して、特定のマークアップ拡張機能が、 [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)です。 マークアップ拡張機能の処理時に、リソース ディクショナリのキーを持つリソースとして既にインスタンス化されているスタイルへの参照を返します。  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 参照を一覧表示するすべてのマークアップ拡張機能の XAML は、WPF では具体的には実装されているため、次を参照してください。 [WPF XAML 拡張](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)です。 System.Xaml であり、.NET Framework の XAML 実装の使用可能なより広範で定義されているマークアップ拡張機能の参照一覧については、次を参照してください[XAML Namespace (x:)。言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)します。 マークアップ拡張機能の概念の詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>型コンバーター  
 [XAML 構文の概要](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#xaml_syntax_in_brief) セクションで、属性の値は文字列で設定できる必要がありますを示されていました。 文字列が他のオブジェクト型またはプリミティブ値に変換される方法の基本的なネイティブの処理がに基づいて、<xref:System.String>型自体などの型をネイティブではさらに特定の処理<xref:System.DateTime>または<xref:System.Uri>です。 しかし、多く[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]型またはそれらの型のメンバーは、処理動作は、このような形でより複雑なオブジェクトの種類のインスタンスを文字列との属性として指定できること、基本的な文字列属性を拡張します。  
  
 <xref:System.Windows.Thickness>構造体は、XAML の使用法に対して有効になっている型の変換を持つ型の例を示します。 <xref:System.Windows.Thickness>入れ子になった四角形内での測定値を示しなどのプロパティの値として使用される<xref:System.Windows.FrameworkElement.Margin%2A>です。 実行する型コンバーターを配置することによって<xref:System.Windows.Thickness>を使用するすべてのプロパティ、<xref:System.Windows.Thickness>を簡単に属性として指定されるため、XAML で指定されます。 次の例の値を指定する型の変換と属性の構文を使用して、 <xref:System.Windows.FrameworkElement.Margin%2A>:  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 上記の属性の構文例は、次に相当詳細での構文例では、ここで、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティ要素構文を含むによって設定されている代わりに、<xref:System.Windows.Thickness>オブジェクト要素。 4 つのプロパティのキー<xref:System.Windows.Thickness>新しいインスタンスに対して属性として設定されます。  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  型変換が唯一のパブリック型自体に既定のコンス トラクターがあるないためにのサブクラスを含めず、その型へのプロパティを設定する方法のオブジェクト数が制限されてもします。 例としては<xref:System.Windows.Input.Cursor>します。  
  
 型変換とその使用の属性の詳細については、構文がサポートされているを参照してください[TypeConverters と XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)です。  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML ルート要素と XAML 名前空間  
 XAML ファイルでは、両方を適切な形式にするために 1 つだけのルート要素があります[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ファイルと有効な XAML ファイル。 WPF の一般的なシナリオの意味を持つ、著名な WPF アプリケーション モデルのルート要素を使用する (たとえば、<xref:System.Windows.Window>または<xref:System.Windows.Controls.Page>ページの  <xref:System.Windows.ResourceDictionary> 、外部のディクショナリのまたは<xref:System.Windows.Application>アプリケーション定義の)。 次の例の一般的な XAML ファイルのルート要素を示しています、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  ページのルート要素を持つ<xref:System.Windows.Controls.Page>します。  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 ルート要素は、属性も含まれています。`xmlns`と`xmlns:x`です。 これらの属性は、XAML 名前空間が、マークアップで要素として参照の種類のバックアップの種類の定義を含む XAML プロセッサに対して示します。 `xmlns`属性は、具体的には、既定の XAML 名前空間を示します。 既定の XAML 名前空間内では、プレフィックスなし、マークアップ内のオブジェクトの要素を指定できます。 ほとんどの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション シナリオと示した例のほとんどすべての[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のセクションでは、 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]、既定の XAML 名前空間にマップされて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]名前空間[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]です。 `xmlns:x`属性は XAML 名前空間が追加され、XAML 言語の名前空間のマッピングを示します[!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)]です。  
  
 この使用法`xmlns`スコープの使用状況と、名前空間のマッピングを定義するのには、XML 1.0 仕様に一致します。 XAML 名前スコープは XML 名前空間と異なるのみを XAML 名前スコープでは名前空間の要素は、のバックアップ方法の種類によって型の解決や、XAML を解析する際に何かことも意味します。  
  
 なお、`xmlns`属性は厳密に各 XAML ファイルのルート要素に必要なだけです。 `xmlns`定義は、ルート要素のすべての子孫要素に適用されます (この動作は、XML 1.0 仕様に一致をもう一度`xmlns`)。`xmlns`属性は、ルートの下にあるその他の要素では許可されてもおよび定義の要素の子孫の要素に適用されます。 ただし、頻繁に定義または XAML 名前空間の再定義は、読みにくいされる XAML マークアップ スタイルで発生します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサの実装には WPF コア アセンブリの認知度を持つインフラストラクチャが含まれています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コア アセンブリがサポートする型を格納する既知の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]既定の XAML 名前空間にマッピングします。 これを使用して、プロジェクトのビルドの一部である構成ファイルと、WPF をビルドし、プロジェクト システムです。 したがって、既定値として既定の XAML 名前空間を宣言する`xmlns`に由来する XAML 要素を参照するために必要なものは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ。  
  
### <a name="the-x-prefix"></a>X: プレフィックス  
 前のルート要素例で、プレフィックス`x:`XAML 名前空間をマップに使用された[!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)]、これは XAML 言語をサポートする専用の XAML 名前空間を作成します。 これは、`x:`例については、および全体でこのドキュメントの プロジェクトのテンプレートでこの XAML 名前空間のマッピングのプレフィックスが使用される[!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]です。 XAML 言語の XAML 名前空間は、XAML で非常に頻繁に使用するいくつかのプログラミング構成要素を含めます。 最も一般的なの一覧を次に示します`x:`プログラミング構成要素を使用するプレフィックスします。  
  
-   [X:key](../../../../docs/framework/xaml-services/x-key-directive.md): 内の各リソースの一意のキーを設定、 <xref:System.Windows.ResourceDictionary> (またはその他のフレームワークのようなディクショナリの概念)。 `x:Key`90% のアカウントではおそらく、`x:`使用状況の一般的な WPF アプリケーションのマークアップに表示されます。  
  
-   [X:class](../../../../docs/framework/xaml-services/x-class-directive.md): を指定します、 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] XAML ページの分離コードを提供するクラスの名前空間とクラス名。 WPF のプログラミング モデルごとに分離コードをサポートするために、このようなクラスが必要し、そのため、ほとんどの場合を参照してください`x:`マップされている場合でも、リソースはありません。  
  
-   [X:name](../../../../docs/framework/xaml-services/x-name-directive.md): オブジェクト要素が処理された後、実行時のコードに存在するインスタンスの実行時のオブジェクト名を指定します。 WPF 定義されているのと同じプロパティを頻繁に使用する一般に、 [X:name](../../../../docs/framework/xaml-services/x-name-directive.md)です。 などのプロパティ プロパティのバッキング CLR を具体的にマップされ、したがってアプリケーション プログラミングの方が便利で頻繁に使用する実行時のコード初期化された XAML から名前付きの要素を検索します。 このようなプロパティは、最も一般的な<xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>します。 使用することもあります[X:name](../../../../docs/framework/xaml-services/x-name-directive.md)ときと同じ WPF フレームワーク レベル<xref:System.Windows.FrameworkElement.Name%2A>プロパティは、特定の種類でサポートされていません。 これは、特定のアニメーションのシナリオで発生します。  
  
-   [X:static](../../../../docs/framework/xaml-services/x-static-markup-extension.md): プロパティを返す静的な値は、それ以外の場合はありませんが、XAML と互換性のある参照を有効にします。  
  
-   [X:type](../../../../docs/framework/xaml-services/x-type-markup-extension.md): 構築、<xref:System.Type>型名の上に基づく参照します。 受け取る属性を指定するのに使用<xref:System.Type>など<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>プロパティが頻繁にネイティブの文字列には、-を-<xref:System.Type>ように変換する、 [X:type](../../../../docs/framework/xaml-services/x-type-markup-extension.md)マークアップ拡張機能の使用は、省略可能です。  
  
 プログラミング構成要素がある、`x:`プレフィックスと XAML 名前空間と一般的ではありません。 詳細については、「 [XAML Namespace (x:)言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)します。  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>カスタムのプレフィックスと XAML でカスタム型  
 カスタムの一部としてアセンブリを指定するには、独自のカスタム アセンブリや WindowsBase、PresentationCore、PresentationFramework の WPF コアの外部アセンブリでは、`xmlns`マッピングします。 Xaml でそのアセンブリからは、その型が正しく実行しようとして、XAML の使用をサポートするために実装されていれば、型を参照できますし、します。  
  
 XAML マークアップでどのようにカスタム プレフィックス作業の非常に基本的な例を次に示します。 プレフィックス`custom`はルート要素タグで定義されているし、パッケージ、アプリケーションで使用可能な特定のアセンブリにマップします。 このアセンブリには、型が含まれている`NumericUpDown`は一般的な XAML を使用できるだけでなく、XAML の WPF コンテンツ モデルでのこの特定のポイントでの挿入を許可するクラスの継承を使用してをサポートするために実装されています。 このインスタンス`NumericUpDown`コントロールがオブジェクト要素として宣言されている、名前空間プレフィックスを使用している XAML を XAML パーサーが認識できるように、種類を含むし、型定義を含むバッキング アセンブリが、そのためです。  
  
```  
<Page  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
    xmlns:custom="clr-namespace:NumericUpDownCustomControl;assembly=CustomLibrary"  
    >  
  <StackPanel Name="LayoutRoot">  
    <custom:NumericUpDown Name="numericCtrl1" Width="100" Height="60"/>  
...  
  </StackPanel>  
</Page>  
```  
  
 XAML でカスタム型の詳細については、次を参照してください。 [XAML と WPF のカスタム クラス](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)です。  
  
 XML 名前空間とアセンブリのコードの名前空間を関連する方法の詳細については、次を参照してください。 [XAML 名前空間と WPF XAML のマッピングの Namespace](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)です。  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>イベントと XAML コードの分離  
 ほとんど[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML マークアップと分離コードの両方のアプリケーションが構成されます。 として書き込まれますが、XAML、プロジェクト内で、`.xaml`ファイル、および[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]などの言語[!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]または[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]分離コード ファイルを書き込むために使用します。 XAML コード ビハインドの場所が、名前空間を指定することによって識別される XAML ファイルのファイルし、クラスの XAML ファイルをマークアップ WPF プログラミングおよびアプリケーション モデルの一部としてコンパイルされるとき、 `x:Class` XAML のルート要素の属性です。  
  
 例では、これまで、いくつかのボタンを表示するが、論理的な動作がまだ関連付けられていたこれらのボタンのいずれもします。 オブジェクト要素の動作を追加するアプリケーション レベルの主要なメカニズムは、要素クラスの既存のイベントを使用して、その実行時にそのイベントが発生したときに呼び出されるイベントの特定のハンドラーを作成するには。 イベント名と使用するハンドラーの名前は、ハンドラーを実装するコードが分離コードで定義されている一方、マークアップでは、指定します。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 分離コード ファイルが CLR 名前空間を使用することに注意してください`ExampleNamespace`を宣言および`ExamplePage`その名前空間内の部分クラスとして。 これは対応して、`x:Class`属性の値の`ExampleNamespace`します。`ExamplePage` マークアップのルートに指定されました。 WPF のマークアップ コンパイラでは、ルート要素の型からクラスを派生してコンパイルされた XAML ファイルの部分クラスを作成します。 同じ部分クラスを定義する分離コードを指定すると、結果として得られるコードが、同じ名前空間と、コンパイルされたアプリケーションのクラス内で結合されます。  
  
 WPF でのコード ビハインド プログラミングの要件の詳細については、の「分離コード、イベント ハンドラー、および部分クラスの要件」セクションを参照してください。[分離コードと wpf XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)です。  
  
 分離コード ファイルを作成しない場合は、することもできますインライン XAML ファイルで自分のコード。 ただし、インライン コードは、多くの制限のある小さい多様な手法です。 詳細については、「[WPF における分離コードと XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)」を参照してください。  
  
### <a name="routed-events"></a>ルーティングされたイベント  
 特定のイベントの機能を基盤となるもの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ルーティング イベントがします。 ルーティング イベントを使用する要素がツリー リレーションシップを介して接続されている限りでさまざまな要素で発生したイベントを処理します。 XAML の属性を持つ処理イベントを指定する場合は、ルーティング イベントをリッスンし、が特定のイベント クラスのメンバー テーブルが記載されていない要素を含む任意の要素で処理します。 これは、所有しているクラスの名前を持つイベントの name 属性を修飾することによって行います。 親インスタンスの`StackPanel`、進行中で`StackPanel`  /  `Button`の例は、子要素のボタンのハンドラーを登録できなかった<xref:System.Windows.Controls.Primitives.ButtonBase.Click>属性を指定することによってイベント`Button.Click`上、 `StackPanel`属性の値として、ハンドラー名を持つオブジェクト要素。 どのようにルーティング イベントの動作の詳細については、次を参照してください。[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)です。  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>XAML の Named 要素  
 既定では、XAML オブジェクト要素の処理では、オブジェクト グラフを作成するオブジェクトのインスタンスがない、一意の識別子またはオブジェクト参照。 これに対し、コードでコンス トラクターを呼び出す場合は、ほぼ常に使用するコンス トラクターの結果、構築されたインスタンスに変数を設定するのに後続のコードでインスタンスを参照できるようにします。 XAML の定義、マークアップ定義によって作成されたオブジェクトへの標準的なアクセスを提供するために、 [X:name 属性](../../../../docs/framework/xaml-services/x-name-directive.md)です。 値を設定することができます、`x:Name`任意のオブジェクト要素の属性です。 分離コードで、選択した識別子は、作成されるインスタンスを参照するインスタンス変数と同じです。 すべての点で名前付きの要素の機能よういたオブジェクトのインスタンス (名前は、そのインスタンスを参照)、分離コードでは、アプリケーション内で実行時の対話の処理には、名前付きの要素を参照できます。 インスタンスと変数の間には、この接続は、WPF XAML マークアップ コンパイラより具体的にが含まれる機能、およびパターンなど<xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A>をこのトピックで詳しくでは説明しません。  
  
 WPF フレームワーク レベルの XAML 要素を継承する<xref:System.Windows.FrameworkElement.Name%2A>プロパティで定義されている XAML に相当ある`x:Name`属性。 その他のクラスも用意されてのプロパティ レベルの等価な`x:Name`、として一般に定義されている、`Name`プロパティです。 一般に、見つからない場合、 `Name` 、選択した要素/種類を使用するのメンバー テーブルでプロパティ`x:Name`代わりにします。 `x:Name`使用できる、実行時に特定のサブシステムまたはユーティリティ メソッドのいずれかなどの XAML 要素に識別子を指定する値<xref:System.Windows.FrameworkElement.FindName%2A>です。  
  
 次の例のセット<xref:System.Windows.FrameworkElement.Name%2A>上、<xref:System.Windows.Controls.StackPanel>要素。 ハンドラーを次に、<xref:System.Windows.Controls.Button>内<xref:System.Windows.Controls.StackPanel>参照、<xref:System.Windows.Controls.StackPanel>のインスタンス参照を通じて`buttonContainer`によって設定<xref:System.Windows.FrameworkElement.Name%2A>です。  
  
 [!code-xaml[XAMLOvwSupport#NamedE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 変数と同じようには予測可能な特定のスコープ内で一意である名前を適用できるように、インスタンスの XAML 名前は、スコープの概念によって管理されます。 ページを定義するマークアップをプライマリでは、XAML 名前スコープの境界をページのルート要素と 1 つ固有の XAML 名前スコープを表します。 ただし、他のマークアップのソースは、スタイルやスタイル内のテンプレートなど、実行時に、ページと対話できます、このようなマークアップ ソース多くの場合、必ずしもの接続があるページの XAML 名前スコープで独自の XAML 名前スコープ。 詳細については`x:Name`の XAML 名前スコープを参照してください、 <xref:System.Windows.FrameworkElement.Name%2A>、 [X:name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)、または[WPF XAML 名前スコープ](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)です。  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>アタッチされるプロパティおよび添付イベント  
 XAML では、特定のプロパティやに設定されている要素の型の定義に、プロパティまたはイベントが存在するかどうかに関係なく、任意の要素で指定するイベントを有効にする言語機能を指定します。 この機能のプロパティのバージョンには、添付プロパティを呼び出すと、イベントのバージョンには、添付イベントが呼び出されます。 概念的には、アタッチされるプロパティおよび添付イベントの任意の XAML 要素/オブジェクトのインスタンスに対して設定できるグローバルのメンバーとして考えることができます。 ただし、その要素またはクラスや大規模なインフラストラクチャは、接続されている値のバッキング プロパティ ストアをサポートする必要があります。  
  
 XAML の添付プロパティは通常、属性構文で使用されます。 属性の構文では、フォームで添付プロパティを指定する*ownerType*.*propertyName*です。  
  
 一見すると、これにプロパティ要素の使用方法に似ていますが、ここでは、 *ownerType*は常にオブジェクトの要素とは異なる型添付プロパティが設定されているを指定します。 *ownerType*を取得または添付プロパティの値を設定するために、XAML プロセッサによって必要なアクセサー メソッドを提供する型です。  
  
 添付プロパティの最も一般的なシナリオは、それぞれの親要素にプロパティ値を報告する子要素を有効にするのにです。  
  
 次の例を示しています、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>添付プロパティ。 <xref:System.Windows.Controls.DockPanel>クラス定義のアクセサー<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>したがって添付プロパティを所有しています。 <xref:System.Windows.Controls.DockPanel>クラスは、その子要素を反復処理し、値の設定の各要素を具体的にはチェック ロジックも含まれています。<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>です。 値が見つかった場合、その値が、子要素を配置するレイアウト時に使用されます。 使用、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>添付プロパティと、この配置機能のスタブに適したシナリオでは実際には、<xref:System.Windows.Controls.DockPanel>クラスです。  
  
 [!code-xaml[XAMLOvwSupport#DockAP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、添付プロパティの大部分または全部が依存関係プロパティとしても実装します。 詳細については、「[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)」を参照してください。  
  
 添付イベントを使用して類似した*ownerType*.*eventName*属性構文のフォームです。 非添付イベントと同じようには、XAML で添付イベントの属性値は、要素のイベントを処理するときに呼び出されるハンドラー メソッドの名前を指定します。 添付イベントの使用法 WPF XAML ではあまり一般的でします。 詳細については、次を参照してください。[添付イベントの概要](../../../../docs/framework/wpf/advanced/attached-events-overview.md)です。  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>基本型、および XAML  
 基になる WPF XAML と XAML 名前空間に対応する型のコレクションは、 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] XAML のマークアップ要素だけでなくオブジェクト。 ただし、すべてのクラスは、要素にマップできます。 など、クラスを抽象化<xref:System.Windows.Controls.Primitives.ButtonBase>での継承で特定非抽象基本クラスを使用して、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]オブジェクト モデルです。 基本クラス、抽象ものも含めてはその階層内のいずれかの基本クラスからメンバーを継承それぞれ具体的な XAML 要素のために XAML 開発することも重要です。 これらのメンバーが含まれる場合、要素の属性として設定できるプロパティやイベントを処理することができます。 <xref:System.Windows.FrameworkElement>具体的なベースである[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のクラス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]WPF フレームワーク レベル。 デザイン時[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]さまざまな図形、パネル、デコレータ、使用する、または指定したすべてのコントロール クラスから派生して<xref:System.Windows.FrameworkElement>です。 関連する基本クラスでは、 <xref:System.Windows.FrameworkContentElement>、フロー レイアウト プレゼンテーション、についても動作するドキュメント指向の要素をサポートを使用して[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]を意図的にミラー化、[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]で<xref:System.Windows.FrameworkElement>です。 要素レベルで属性の組み合わせと[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]オブジェクト モデルによって、特定の XAML 要素とその基になる型に関係なく、最も具体的な XAML 要素上では設定されている共通プロパティのセットでは提供します。  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>XAML セキュリティ  
 XAML は、直接オブジェクト インスタンスの作成と実行を表すマークアップ言語です。 したがって、XAML で作成された要素機能があります、同じを生成した同等のシステム リソース (ネットワーク アクセス、ファイル システムの入出力など) と対話するコードです。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]サポートしている、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]セキュリティ フレームワーク[!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)]です。 つまり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]インターネット ゾーンで実行されているコンテンツの実行権限が少なくなっています。 "Loose XAML"(コンパイルされていない XAML のページと解釈の読み込み時に XAML ビューアーで) と[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]このインターネット ゾーンでは、通常実行して、同じアクセス許可セットを使用します。  ただし、XAML を完全に信頼されたアプリケーションでロードでは、ホスト アプリケーションのようにシステム リソースへのアクセス権があります。 詳細については、次を参照してください。 [WPF 部分信頼セキュリティ](../../../../docs/framework/wpf/wpf-partial-trust-security.md)です。  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>コードからの XAML を読み込む  
 XAML は、すべての UI を定義するために使用できますが、また XAML で UI の一部だけを定義するがあります。 この機能には、ビジネス オブジェクト、またはさまざまなシナリオを提供する XAML を使用して、情報のローカル記憶域、部分的なカスタマイズを有効にすることできます。 これらのシナリオにキーが、<xref:System.Windows.Markup.XamlReader>クラスとその<xref:System.Windows.Markup.XamlReader.Load%2A>メソッドです。 入力は、XAML ファイルであり、出力は、そのマークアップから作成されたオブジェクトの実行時のツリーのすべてを表すオブジェクト。 アプリケーションに既に存在する別のオブジェクトのプロパティであるオブジェクトを挿入できます。 実行中のアプリケーションのコンテンツを非常に簡単に変更することができます、プロパティは、最終的な表示機能を持つ実行エンジンを通知すること、新しいコンテンツがアプリケーションに追加されているコンテンツ モデルで適切なプロパティである限り、で xaml 読み込みします。 機能が一般にのみ完全に信頼されたアプリケーションで使用できる明確なセキュリティに与える影響、実行時に、アプリケーションにファイルを読み込むために注意してください。  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>次の内容  
 このトピックは、WPF を適用する際に、XAML 構文の概念と用語の概要を示します。 ここで使用される用語の詳細については、次を参照してください。 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)です。  
  
 既に完了していない場合この、チュートリアルのトピックの手順を実行してください。[チュートリアル: 最初の WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)です。 このチュートリアルで説明されているマークアップを中心としたアプリケーションを作成するときにこのトピックで説明する概念の多くが深まります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]基になっている特定のアプリケーション モデルを使用して、<xref:System.Windows.Application>クラスです。 詳細については、「[アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)です。  
  
 [WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)XAML 包括的なアプリケーションを使用してコマンドラインからを構築する方法の詳細については、[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]です。  
  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)でプロパティの用途のための詳細については、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、し、依存関係プロパティの概念を紹介します。  
  
## <a name="see-also"></a>参照  
 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [WPF における XAML とカスタム クラス](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [XAML 名前空間 (x:) 言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [WPF XAML 拡張機能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
