---
title: "XAML の概要 (WPF) | Microsoft Docs"
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
  - "属性構文 [XAML]"
  - "基本クラス [XAML]"
  - "クラス [XAML]"
  - "分離コード ファイル [WPF], XAML"
  - "コレクション プロパティ [XAML]"
  - "コンテンツ モデル [XAML]"
  - "イベント [XAML]"
  - "Extensible Application Markup Language ("XAML" を参照)"
  - "プロパティ要素 [XAML]"
  - "ルート要素 [XAML]"
  - "ルーティング イベント"
  - "ユーザー インターフェイス [XAML]"
  - "XAML [WPF], 概要 (XAML の)"
ms.assetid: a80db4cd-dd0f-479f-a45f-3740017c22e4
caps.latest.revision: 57
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 50
---
# XAML の概要 (WPF)
ここでは、XAML 言語の機能と、XAML を使用して実際に [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションを記述する方法について説明します。  ここで説明する XAML は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって実装されている XAML です。  XAML 自体は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] よりも大きい言語概念です。  
  
   
  
<a name="what_is_xaml"></a>   
## XAML とは  
 XAML は、宣言型マークアップ言語です。  XAML を [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] プログラミング モデルに適用すると、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の作成が簡単になります。  表示される [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を宣言的 XAML マークアップで作成し、分離コード ファイルを使用して [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 定義をランタイム ロジックから分離させることができます。分離コード ファイルは部分クラス定義を通じてマークアップに結合されます。  XAML では、アセンブリで定義されている一連のバッキング型のオブジェクトのインスタンス化が直接表現されます。これは、他のほとんどのマークアップ言語 \(一般に、このようにバッキング型システムと直接関連付けられていない解釈される言語\) とは異なります。  XAML により、アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] とロジックの作業を別々の作業者が \(場合によっては別々のツールを使用して\) 行うことができるワークフローが実現されます。  
  
 テキストとして表現された場合の XAML ファイルは XML ファイルで、拡張子は通常 `.xaml` です。  ファイルは任意の XML エンコーディングでエンコードできますが、UTF\-8 としてエンコードするのが一般的です。  
  
 次の例は、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の一部としてボタンを作成する方法を示しています。  この例は、一般的な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] プログラミング要素が XAML でどのように表現されるのかを大まかに示すためのものであり、完全なサンプルではありません。  
  
 [!code-xml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## XAML 構文の概要  
 ここでは、XAML 構文の基本的な形式について説明し、短いマークアップの例を紹介します。  各構文形式に関する詳細な説明 \(それらがバッキング型システムでどのように表現されるかなど\) は含まれません。  ここで紹介する各形式の XAML 構文の詳細については、「[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」を参照してください。  
  
 既に XML 言語に精通している方にとって、以降のセクションで説明する内容はほとんどが初歩的なものです。  これは、XAML の基本的な設計原則の 1 つに従った結果です。  XAML 言語ではそれ自体の概念が定義されますが、これらの概念は XML 言語およびマークアップ形式内で機能します。  
  
### XAML オブジェクト要素  
 通常、オブジェクト要素は型のインスタンスを宣言します。  その型は、XAML を言語として使用するテクノロジにバッキング型を提供するアセンブリで定義されています。  
  
 オブジェクト要素構文は常に左山かっこ \(\<\) で始まります。  次に、インスタンスを作成する型の名前を指定します   \(名前にプレフィックスを含めることもできます。プレフィックスについては後で説明します\)。その後に、オブジェクト要素の属性を宣言することもできます。  オブジェクト要素タグを完成させるには、右山かっこ \(\>\) でタグを閉じます。  コンテンツを含まない自己終了形式を使用することもできます。その場合は、タグを閉じるときにスラッシュと右山かっこを続けて入力します \(\/\>\)。  例として、先ほどのマークアップ スニペットをもう一度示します。  
  
 [!code-xml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 ここでは、`<StackPanel>` \(コンテンツが含まれ、その後に終了タグがあります\) と `<Button .../>` \(自己終了形式。いくつかの属性が含まれています\) という 2 つのオブジェクト要素が指定されています。  `StackPanel` と `Button` というオブジェクト要素は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって定義されているクラスの名前にそれぞれマッピングされます。これらのクラスは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アセンブリの一部になっています。  オブジェクト要素タグを指定すると、XAML 処理に対する命令が作成されて、新しいインスタンスが作成されます。  各インスタンスは、XAML が解析されて読み込まれるときに、基になる型の既定のコンストラクターを呼び出して作成されます。  
  
### 属性構文 \(プロパティ\)  
 オブジェクトのプロパティは、多くの場合、オブジェクト要素の属性として表現できます。  属性構文では、属性構文で設定するプロパティの名前を指定し、代入演算子 \(\=\) をはさんで、  属性の値を指定します。値は常に、引用符で囲まれた文字列として指定されます。  
  
 属性構文は最も簡潔なプロパティ設定構文であり、マークアップ言語を使用した経験がある開発者が最も直感的に使用できるのがこの構文です。  たとえば、次のマークアップは、赤いテキストと青い背景を持つボタンを作成します。このボタンには、`Content` として指定された表示テキストも含まれます。  
  
 [!code-xml[XAMLOvwSupport#BlueRedButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### プロパティ要素の構文  
 オブジェクト要素のプロパティには、プロパティ値を指定するために必要なオブジェクトや情報を引用符で囲んで適切に表現できないため、および属性構文の文字列の制限があるため、属性構文を使用できないものもあります。  そのような場合は、プロパティ要素構文と呼ばれる別の構文を使用できます。  
  
 プロパティ要素の開始タグの構文は、`<`*typeName*`.`*propertyName*`>` です。  このタグのコンテンツには、一般に、そのプロパティが値として受け取る型のオブジェクト要素を指定します。  コンテンツを指定した後は、終了タグを使用してプロパティ要素を終了する必要があります。  終了タグの構文は、`</`*typeName*`.`*propertyName*`>` です。  
  
 属性構文を使用できる場合は、通常、属性構文を使用した方が便利で、マークアップもよりコンパクトになります。ただし、多くの場合、これは単なるスタイルの問題であり、技術的な制限ではありません。  次の例では、前の属性構文の例で設定したのと同じプロパティを設定しています。ただし、ここでは、`Button` のすべてのプロパティに対してプロパティ要素構文を使用しています。  
  
 [!code-xml[XAMLOvwSupport#BlueRedButtonPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### コレクションの構文  
 XAML 言語には、人が判読しやすいマークアップを生成するいくつかの最適化機能が盛り込まれています。  そのような最適化の 1 つは、特定のプロパティがコレクション型を受け取る場合、そのプロパティの値内の子要素としてマークアップで宣言する項目がそのコレクションの一部になるということです。  この場合、一連の子オブジェクト要素が、そのコレクション プロパティに設定される値になります。  
  
 次の例は、<xref:System.Windows.Media.GradientBrush.GradientStops%2A> プロパティの値を設定するコレクション構文の例を示しています。  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->  
    <GradientStop Offset="0.0" Color="Red" />  
    <GradientStop Offset="1.0" Color="Blue" />  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
### XAML コンテンツ プロパティ  
 XAML で規定されている言語機能として、クラスでそのプロパティのうちの 1 つだけを XAML コンテンツ プロパティとして指定できます。  コンテンツ プロパティの値は、そのオブジェクト要素の子要素を使用して設定されます。  つまり、コンテンツ プロパティのみについては、XAML マークアップでそのプロパティを設定するときにプロパティ要素を省略し、よりわかりやすい親\/子メタファをマークアップに生成できます。  
  
 たとえば、<xref:System.Windows.Controls.Border> では <xref:System.Windows.Controls.Decorator.Child%2A> がコンテンツ プロパティとして指定されています。  次の 2 つの <xref:System.Windows.Controls.Border> 要素は同じように扱われます。  1 つ目の例では、コンテンツ プロパティ構文を利用して `Border.Child` プロパティ要素を省略しています。  2 つ目の例では、`Border.Child` が明示的に指定されています。  
  
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
  
 XAML 言語の規則として、XAML コンテンツ プロパティの値は、そのオブジェクト要素の他のすべてのプロパティ要素の前または後に指定する必要があります。  たとえば、次のマークアップはコンパイルされません。  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 この XAML コンテンツ プロパティの制限の詳細については、「[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」の「XAML コンテンツ プロパティ」を参照してください。  
  
### テキスト コンテンツ  
 一部の XAML 要素では、テキストをコンテンツとして直接処理できます。  これが有効になるのは、次のいずれかの状況に当てはまる場合です。  
  
-   クラスでコンテンツ プロパティが宣言されていて、そのコンテンツ プロパティの型が文字列に代入可能な型 \(<xref:System.Object> など\) である。  たとえば、すべての <xref:System.Windows.Controls.ContentControl> は、<xref:System.Object> 型の <xref:System.Windows.Controls.ContentControl.Content%2A> をコンテンツ プロパティとして使用します。この場合、実際の <xref:System.Windows.Controls.ContentControl> \(<xref:System.Windows.Controls.Button> など\) で `<Button>Hello</Button>` という使用方法がサポートされます。  
  
-   型で型コンバーターが宣言されている。この場合は、テキスト コンテンツがその型コンバーターの初期化テキストとして使用されます   たとえば、`<Brush>Blue</Brush>` のようにします。  このケースは、実際にはあまり見られません。  
  
-   型が既知の XAML 言語プリミティブである。  
  
### コンテンツ プロパティとコレクション構文の組み合わせ  
 次の例について考えます。  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 ここで、各 <xref:System.Windows.Controls.Button> は <xref:System.Windows.Controls.StackPanel> の子要素です。  この簡略化された直観的なマークアップでは、2 つのタグがそれぞれ異なる理由で省略されています。  
  
-   **StackPanel.Children プロパティ要素の省略 :**  <xref:System.Windows.Controls.StackPanel> は <xref:System.Windows.Controls.Panel> から派生します。  <xref:System.Windows.Controls.Panel> では、<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=fullName> がその XAML コンテンツ プロパティとして定義されています。  
  
-   **UIElementCollection オブジェクト要素の省略 :** <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=fullName> プロパティは、<xref:System.Collections.IList> を実装する <xref:System.Windows.Controls.UIElementCollection> 型を受け取ります。  コレクションの要素タグは、<xref:System.Collections.IList> などのコレクションの処理に関する XAML の規則に基づいて省略できます   \(この例では、<xref:System.Windows.Controls.UIElementCollection> は既定のコンストラクターを公開していないため、実際にはインスタンス化できません。<xref:System.Windows.Controls.UIElementCollection> オブジェクト要素がコメント アウトされているのはこのためです\)。  
  
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
  
### 属性構文 \(イベント\)  
 属性構文は、プロパティではなくイベントであるメンバーに対しても使用できます。  この場合、属性の名前はイベントの名前です。  XAML のイベントの WPF 実装では、属性の値は、そのイベントのデリゲートを実装するハンドラーの名前です。  たとえば、次のマークアップでは、マークアップで作成された <xref:System.Windows.Controls.Button> に <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントのハンドラーを割り当てています。  
  
 [!code-xml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 WPF のイベントと XAML については、この属性構文の例だけでは説明しきれません。  たとえば、ここで参照されている `ClickHandler` が何を表し、どのように定義されているのかが気になった方もいるでしょう。  これについては、後ほど「」で説明します。  
  
<a name="case_and_whitespace_in_xaml"></a>   
## XAML の大文字\/小文字と空白  
 一般に、XAML は大文字と小文字を区別します。  バッキング型の解決という目的上、CLR が大文字と小文字を区別する同じ規則によって、WPF XAML は大文字と小文字を区別します。  アセンブリ内の基になる型や型のメンバーとの名前による比較の際は、すべてのオブジェクト要素、プロパティ要素、および属性名を、大文字と小文字を正しく区別して指定する必要があります。  XAML 言語のキーワードとプリミティブも大文字と小文字を区別します。  値の大文字と小文字は必ずしも区別されるわけではありません。  値の大文字と小文字が区別されるかどうかは、その値を受け取るプロパティ \(そのプロパティの値型\) に関連付けられている型コンバーターの動作によって決まります。  たとえば、<xref:System.Boolean> 型を受け取るプロパティでは、`true` と `True` のいずれかを同じ値として受け取ることができますが、これは、ネイティブ WPF XAML パーサーの文字列から <xref:System.Boolean> への型変換で、これらを同じ値として扱うことが許可済みであるためです。  
  
 WPF XAML プロセッサとシリアライザーでは、意味のない空白はすべて無視 \(省略\) され、意味のある空白は正規化されます。  これは、XAML 仕様で推奨される既定の空白の動作と一致しています。  この動作は、通常、XAML コンテンツ プロパティ内に文字列を指定した場合にのみ行われます。  簡単に言うと、XAML では、空白、ライン フィード、およびタブ文字が空白に変換され、連続する文字列の前または後ろに空白がある場合は、それぞれ 1 つの空白が保持されます。  XAML の空白の処理の詳細は、このトピックでは扱いません。  詳細については、「[XAML での空白の処理](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)」を参照してください。  
  
<a name="markup_extensions"></a>   
## マークアップ拡張  
 マークアップ拡張機能は XAML 言語の概念です。  属性構文の値を指定するために使用する場合は、中かっこ \(`{` と `}`\) によってマークアップ拡張機能の使用方法を示します。  これにより、XAML プロセッサの通常の処理 \(リテラル文字列か、文字列に変換できる値のいずれかとして属性値を扱う処理\) がエスケープされます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション プログラミングで使用される最も一般的なマークアップ拡張機能には、データ バインディング表現に使用する [Binding](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)、およびリソース参照 [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) と [DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) があります。  マークアップ拡張機能を使用すると、通常は属性構文をサポートしないプロパティでも、属性構文を使用してプロパティの値を指定できます。  また、中間式の型を使用して、値の設定の遅延や、実行時にしか存在しない他のオブジェクトの参照などの機能を有効にすることもできます。  
  
 たとえば、次のマークアップでは、属性構文を使用して <xref:System.Windows.FrameworkElement.Style%2A> プロパティの値を設定しています。  <xref:System.Windows.FrameworkElement.Style%2A> プロパティは <xref:System.Windows.Style> クラスのインスタンスを受け取ります。これは、既定では属性構文の文字列でインスタンス化することはできません。  しかし、この例では、属性が [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) のマークアップ拡張機能を参照しています。  このマークアップ拡張機能が処理されると、リソース ディクショナリ内のキーを持つリソースとして既にインスタンス化されているスタイルへの参照が返されます。  
  
<!-- TODO: review snippet reference  [!CODE [FEResourceSH#XAMLOvwShortResources](FEResourceSH#XAMLOvwShortResources)]  -->  
<!-- TODO: review snippet reference [!CODE [FEResourceSH#XAMLOvwShortResources2](FEResourceSH#XAMLOvwShortResources2)]  -->  
<!-- TODO: review snippet reference [!CODE [FEResourceSH#XAMLOvwShortResources3](FEResourceSH#XAMLOvwShortResources3)]  -->  
  
 特に WPF に実装されている XAML のすべてのマークアップ拡張機能のリファレンス情報については、「[WPF XAML 拡張機能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)」を参照してください。  System.Xaml で定義され、.NET Framework XAML の実装でより広範に使用できるマークアップ拡張機能のリファレンス情報については、「[XAML 名前空間 \(x:\) 言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)」を参照してください。  マークアップ拡張機能の概念の詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
<a name="type_converters"></a>   
## 型コンバーター  
 「」で説明したように、属性値は文字列で設定できる必要があります。  文字列から他のオブジェクト型やプリミティブ値への変換という基本的なネイティブの処理は、<xref:System.DateTime> や <xref:System.Uri> などの一部の型のネイティブ処理と同様に、<xref:System.String> 型自体に基づいて行われます。  ただし、多くの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 型やそのメンバーでは、基本的な文字列属性の処理の動作を拡張して、より複雑なオブジェクト型のインスタンスを文字列や属性として指定できるようにしています。  
  
 XAML での使用時に型変換が有効になる型の一例として、<xref:System.Windows.Thickness> 構造体があります。  <xref:System.Windows.Thickness> は、入れ子になった四角形内の寸法を表す構造体で、<xref:System.Windows.FrameworkElement.Margin%2A> などのプロパティの値として使用されます。  <xref:System.Windows.Thickness> に型コンバーターを配置すると、<xref:System.Windows.Thickness> を使用するすべてのプロパティを属性として指定できるようになるため、XAML での指定が簡単になります。  次の例では、型変換と属性構文を使用して <xref:System.Windows.FrameworkElement.Margin%2A> の値を指定しています。  
  
 [!code-xml[XAMLOvwSupport#MarginTCE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 この属性構文の例は、次の例に示すより冗長な構文と同等です。次の例では、<xref:System.Windows.Thickness> オブジェクト要素を含むプロパティ要素構文によって <xref:System.Windows.FrameworkElement.Margin%2A> が設定されています。  <xref:System.Windows.Thickness> の 4 つの主要なプロパティが、新しいインスタンスの属性として設定されています。  
  
 [!code-xml[XAMLOvwSupport#MarginVerbose](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  オブジェクトによっては、型自体に既定のコンストラクターがないため、サブクラスを含めずにプロパティをその型に設定するには型変換を使用する以外方法がない場合もあります。  <xref:System.Windows.Input.Cursor> はその一例です。  
  
 型変換および属性構文での型変換の使用がどのようにサポートされているかの詳細については、「[TypeConverters および XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)」を参照してください。  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## XAML ルート要素と XAML 名前空間  
 XAML ファイルを整形式の [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ファイルにし、有効な XAML ファイルにするためには、ルート要素を 1 つだけ指定する必要があります。  一般的な WPF シナリオでは、WPF アプリケーション モデルにおいて重要な意味を持つルート要素を使用します \(ページの場合は <xref:System.Windows.Window> や <xref:System.Windows.Controls.Page>、外部ディクショナリの場合は <xref:System.Windows.ResourceDictionary>、アプリケーション定義の場合は <xref:System.Windows.Application> など\)。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページの一般的な XAML ファイルの <xref:System.Windows.Controls.Page> というルート要素の例を次に示します。  
  
 [!code-xml[XAMLOvwSupport#RootOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xml[XAMLOvwSupport#RootOnly2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 このルート要素には、`xmlns` と `xmlns:x` という属性も含まれています。  これらの属性は、マークアップで要素として参照するバッキング型の型定義が含まれている XAML 名前空間を XAML プロセッサに対して示します。  `xmlns` 属性は、既定の XAML 名前空間を明示的に指定しています。  既定の XAML 名前空間内では、マークアップのオブジェクト要素をプレフィックスなしで指定できます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのほとんどのシナリオ \(およびこの [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] セクションのほとんどすべての例\) で、既定の XAML 名前空間は [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 名前空間 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] にマッピングされます。  `xmlns:x` 属性は追加の XAML 名前空間を示し、XAML 言語の名前空間 [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)] を割り当てています。  
  
 このように `xmlns` を使用して名前空間の使用方法とマッピングのスコープを定義することは、XML 1.0 仕様に一致しています。  XAML 名前空間と XML 名前空間の違いは、XAML 名前空間は、型の解決や XAML の解析の際に、名前空間の要素のバッキング タイプを特定するためにも使用されるということだけです。  
  
 `xmlns` 属性が厳密に必要なのは、各 XAML ファイルのルート要素に対してだけです。  `xmlns` の定義はルート要素のすべての子孫要素に適用されます \(この動作も `xmlns` の XML 1.0 仕様に一致しています\)。`xmlns` 属性をルートの下のその他の要素で定義することも可能で、その場合も、定義されている要素のすべての子孫要素に適用されます。  ただし、XAML 名前空間を頻繁に定義したり再定義したりすると、XAML のマークアップが読みにくくなる可能性があります。  
  
 XAML プロセッサの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 実装には、WPF コア アセンブリを認識するインフラストラクチャが含まれます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コア アセンブリは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] から既定の XAML 名前空間へのマッピングをサポートする型を含んでいることがわかっています。  これは、プロジェクト ビルド ファイルに含まれている構成と、WPF のビルド システムとプロジェクト システムによって実現されます。  このため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アセンブリに基づく XAML 要素を参照するには、既定の XAML 名前空間を既定の `xmlns` として宣言するだけで済みます。  
  
### x: プレフィックス  
 前のルート要素の例では、`x:` というプレフィックスを使用して、XAML 名前空間 [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)] \(XAML 言語構成要素をサポートする専用の XAML 名前空間\) をマップしていました。  この `x:` プレフィックスは、この [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 全体を通じて、プロジェクトのテンプレート、例、およびドキュメントで、この XAML 名前空間をマッピングするために使用されています。  XAML 言語用の XAML 名前空間には、XAML で頻繁に使用されるプログラミング構成要素がいくつか含まれます。  `x:` プレフィックスのプログラミング構成要素の中で最もよく使用されるものを以下に示します。  
  
-   [x:Key](../../../../docs/framework/xaml-services/x-key-directive.md): <xref:System.Windows.ResourceDictionary> 内の各リソース \(または他のフレームワークの同様のディクショナリの概念\) に一意キーを設定します。  おそらく、一般的な WPF アプリケーションのマークアップで使用される `x:` の約 90% は `x:Key` であると考えられます。  
  
-   [x:Class](../../../../docs/framework/xaml-services/x-class-directive.md): XAML ページの分離コードを提供するクラスの [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 名前空間とクラス名を指定します。  WPF プログラミング モデルごとに分離コードをサポートするには、このようなクラスが必要です。リソースがない場合でもほぼ必ず `x:` が割り当てられるのはこのためです。  
  
-   [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md): オブジェクト要素が処理された後のランタイム コードに存在するインスタンスのランタイム オブジェクト名を指定します。  一般に、[x:Name](../../../../docs/framework/xaml-services/x-name-directive.md) に対応する WPF で定義されている同様のプロパティを使用することがよくあります。  このようなプロパティは特に CLR バッキング プロパティに割り当てられるので、初期化された XAML から名前付き要素を見つけるために実行時コードを使用することがよくある、アプリケーションのプログラミングで役立ちます。  このようなプロパティで最も一般的に使用されるのは、<xref:System.Windows.FrameworkElement.Name%2A?displayProperty=fullName> です。  それでも、[x:Name](../../../../docs/framework/xaml-services/x-name-directive.md) は、同等の [WPF フレームワーク レベル](GTMT)の <xref:System.Windows.FrameworkElement.Name%2A> プロパティが特定の型でサポートされない場合に使用します。  一部のアニメーション シナリオでこのような状況が見られます。  
  
-   [x:Static](../../../../docs/framework/xaml-services/x-static-markup-extension.md): XAML 互換のプロパティとしては定義されていない静的な値を返す参照を可能にします。  
  
-   [x:Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md): 型の名前に基づいて <xref:System.Type> の参照を作成します。  これは、<xref:System.Windows.Style.TargetType%2A?displayProperty=fullName> など、<xref:System.Type> を受け取る属性を指定する場合に使用します。ただし、多くの場合、プロパティには文字列から <xref:System.Type> へのネイティブ変換が用意されており、[x:Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md) マークアップ拡張機能の使用は任意です。  
  
 `x:` プレフィックス\/XAML 名前空間には、これ以外にも、あまり一般的でないプログラミング構成要素があります。  詳細については、「[XAML 名前空間 \(x:\) 言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)」を参照してください。  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## XAML のカスタム プレフィックスとカスタム型  
 独自のカスタム アセンブリや、WPF コアの PresentationCore、PresentationFramework、および WindowsBase 以外のアセンブリに対しては、カスタム `xmlns` マッピングの一部としてそのアセンブリを指定できます。  そうすると、目的の XAML の使用方法をサポートするように型が正しく実装されている限り、そのアセンブリの型を XAML で参照できるようになります。  
  
 XAML マークアップでカスタム プレフィックスがどのように機能するのかをごく簡単な例で見てみましょう。  プレフィックス `custom` がルート要素タグで定義され、アプリケーションにパッケージ化されている特定のアセンブリに対応付けられています。  このアセンブリには、`NumericUpDown` という型が含まれています。この型は、一般的な XAML の使用方法と、この型を WPF XAML コンテンツ モデルのこの特定の場所に挿入できるようにするクラス継承の使用をサポートするように実装されています。  この `NumericUpDown` コントロールのインスタンスは、プレフィックスを使用してオブジェクト要素として宣言されます。プレフィックスにより、この型がどの XAML 名前空間に含まれているか、さらには型定義を含むバッキング アセンブリがどこにあるかを XAML パーサーが認識できるようになります。  
  
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
  
 XAML のカスタム型の詳細については、「[WPF における XAML とカスタム クラス](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)」を参照してください。  
  
 XML 名前空間とアセンブリ内の対応するコードの名前空間との関連の詳細については、「[XAML 名前空間および WPF XAML の名前空間の割り当て](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。  
  
<a name="events_and_xaml_codebehind"></a>   
## イベントと XAML 分離コード  
 ほとんどの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションは、XAML マークアップと分離コードの両方で構成されています。  プロジェクト内では、XAML は `.xaml` ファイルとして作成され、分離コード ファイルの記述には [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] や [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] などの [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 言語が使用されます。  WPF プログラミングとアプリケーション モデルの一部として XAML ファイルをマークアップ コンパイルすると、XAML のルート要素の `x:Class` 属性として指定された名前空間とクラスにより、XAML ファイルに対応する XAML 分離コード ファイルの場所が特定されます。  
  
 これまでに見てきた例にはいくつかのボタンが含まれていましたが、それらのボタンにはまだ論理的な動作が関連付けられていません。  オブジェクト要素の動作を追加するためのアプリケーション レベルの主要なメカニズムでは、要素クラスの既存のイベントを使用して、そのイベントの特定のハンドラーを作成します。実行時にそのイベントが発生すると、そのハンドラーが呼び出されます。  イベントの名前と使用するハンドラーの名前をマークアップで指定し、ハンドラーを実装するコードは分離コードで定義します。  
  
 [!code-xml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 この分離コード ファイルでは、CLR 名前空間 `ExampleNamespace` が使用されており、その名前空間内の部分クラスとして `ExamplePage` が宣言されています。  これは、マークアップのルートで指定されている `x:Class` 属性値 `ExampleNamespace`.`ExamplePage` に対応しています。  WPF マークアップ コンパイラは、ルート要素の型からクラスを派生させることにより、コンパイルされた XAML ファイルの部分クラスを作成します。  同じ部分クラスを定義する分離コードを指定した場合、作成されるコードは、コンパイルされたアプリケーションの同じ名前空間とクラスに結合されます。  
  
 WPF での分離コード プログラミングの要件の詳細については、「[WPF における分離コードと XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)」の「分離コード、イベント ハンドラー、および部分クラスの要件」を参照してください。  
  
 独立した分離コード ファイルを作成しない場合は、XAML ファイル内にインラインでコードを埋め込むこともできます。  ただし、インライン コードには多くの制限があり、汎用性の面で劣ります。  詳細については、「[WPF における分離コードと XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)」を参照してください。  
  
### ルーティング イベント  
 [ルーティング イベント](GTMT)は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の基本的なイベント機能です。  ルーティング イベントを使用すると、ツリー リレーションシップでつながっている要素間において、ある要素で発生したイベントを別の要素で処理できます。  XAML 属性を使用してイベント処理を指定する際には、要素のクラス メンバー テーブルにその特定のイベントが含まれているかどうかに関係なく、任意の要素でルーティング イベントをリッスンおよび処理できます。  これを実現するには、所有するクラスの名前でイベント名属性を修飾します。  たとえば、ここで使用している `StackPanel` \/ `Button` の例の親 `StackPanel` で子要素ボタンの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントのハンドラーを登録するには、`StackPanel` オブジェクト要素で属性 `Button.Click` を指定します。属性値は、使用するハンドラーの名前です。  ルーティング イベントのしくみの詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」を参照してください。  
  
<a name="x_name_and_xaml_named_elements"></a>   
## XAML の名前付き要素  
 XAML オブジェクト要素を処理することによってオブジェクト グラフに作成されたオブジェクト インスタンスには、既定では一意の識別子やオブジェクト参照はありません。  これに対し、コードでコンストラクターを呼び出す場合は、作成されたインスタンスを後からコードで参照できるように、コンストラクターの結果として返されたインスタンスを変数に設定することが一般的です。  XAML の場合は、マークアップ定義によって作成されたオブジェクトへの標準的なアクセスを実現する方法として、[x:Name 属性](../../../../docs/framework/xaml-services/x-name-directive.md)が定義されています。  `x:Name` 属性の値は、任意のオブジェクト要素で設定できます。  指定した識別子は、分離コードにおいて、作成されたインスタンスを参照するインスタンス変数と同じように機能します。  名前付きの要素はあらゆる点でオブジェクト インスタンスのように機能するため \(名前で対象のインスタンスが参照されます\)、名前付きの要素を分離コードで参照してアプリケーション内の実行時のやり取りを処理できます。  インスタンスと変数間のこの関連付けは、WPF XAML マークアップ コンパイラによって実現し、より具体的には <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> などの機能とパターン \(ここでは詳しく説明しません\) が必要です。  
  
 [WPF フレームワーク レベル](GTMT)の XAML 要素は、<xref:System.Windows.FrameworkElement.Name%2A> プロパティを継承しています。このプロパティは、XAML で定義される `x:Name` 属性と同等です。  その他のクラスでも、`x:Name` と同等のプロパティが用意されている場合があり、そのようなプロパティも通常は `Name` プロパティとして定義されています。  一般に、目的の要素\/型のメンバー テーブルに `Name` プロパティがない場合は、代わりに `x:Name` を使用します。  `x:Name` の値は、特定のサブシステムまたはユーティリティ メソッド \(<xref:System.Windows.FrameworkElement.FindName%2A> など\) によって、実行時に使用できる XAML 要素に識別子を提供します。  
  
 次の例では、<xref:System.Windows.Controls.StackPanel> 要素の <xref:System.Windows.FrameworkElement.Name%2A> を設定しています。  その後、その <xref:System.Windows.Controls.StackPanel> 内の <xref:System.Windows.Controls.Button> のハンドラーで、<xref:System.Windows.FrameworkElement.Name%2A> で設定したインスタンス参照 `buttonContainer` を使用して <xref:System.Windows.Controls.StackPanel> を参照しています。  
  
 [!code-xml[XAMLOvwSupport#NamedE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xml[XAMLOvwSupport#NamedE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 変数と同様に、インスタンスの XAML 名も、予測可能な特定のスコープ内において名前が一意になるように、スコープの概念によって制御されています。  ページを定義するプライマリ マークアップで一意の XAML 名前スコープが指定され、XAML 名前スコープの境界はそのページのルート要素になります。  ただし、実行時には、スタイルやスタイル内のテンプレートなどの他のマークアップ ソースもページとやり取りをする可能性があります。そのようなマークアップ ソースは、ページの XAML 名前スコープとは必ずしも関連のない独自の XAML スコープを持っていることがよくあります。  `x:Name` および XAML 名前スコープの詳細については、「<xref:System.Windows.FrameworkElement.Name%2A>」、「[x:Name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)」、または「[WPF XAML 名前スコープ](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)」を参照してください。  
  
<a name="attached_properties_and_attached_events"></a>   
## 添付プロパティと添付イベント  
 XAML で規定されている言語機能では、要素の型の定義に存在するかどうかに関係なく、特定のプロパティやイベントを任意の要素で指定できます。  この機能は、プロパティでは[添付プロパティ](GTMT)、イベントでは[添付イベント](GTMT)と呼びます。  添付プロパティと添付イベントは、概念的には、任意の XAML 要素\/オブジェクト インスタンスに設定できるグローバル メンバーと考えることができます。  ただし、その要素\/クラス、またはより大きなインフラストラクチャは、添付された値のバッキング プロパティ ストアをサポートする必要があります。  
  
 XAML の添付プロパティは、通常、属性構文で使用されます。  属性構文では、*ownerType*.*propertyName* という形式で添付プロパティを指定します。  
  
 この形式は、表面的にはプロパティ要素の使用方法に似ていますが、ここで指定する *ownerType* は常に、添付プロパティが設定されるオブジェクト要素とは別の型です。  *ownerType* は、XAML プロセッサで添付プロパティの値を取得したり設定したりするために必要なアクセサー メソッドを提供する型です。  
  
 添付プロパティのシナリオとしては、子要素が親要素にプロパティ値を報告できるようにするために使用されるのが最も一般的です。  
  
 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 添付プロパティの例を次に示します。  <xref:System.Windows.Controls.DockPanel> クラスは、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> のアクセサーを定義しています。したがって、この添付プロパティを所有しています。  <xref:System.Windows.Controls.DockPanel> クラスには、子要素を反復処理して各要素で <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> の設定値がないかどうかをチェックするロジックも含まれています。  値が見つかった場合は、レイアウト時に子要素を配置するために使用されます。  実際、<xref:System.Windows.Controls.DockPanel> クラスは、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 添付プロパティとこの配置の機能のために使用されます。  
  
 [!code-xml[XAMLOvwSupport#DockAP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、大部分またはすべての添付プロパティは[依存関係プロパティ](GTMT)としても実装されます。  詳細については、「[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)」を参照してください。  
  
 添付イベントも、*ownerType*.*eventName* という同じような形式の属性構文を使用します。  他のイベントの場合と同様に、XAML の添付イベントの属性値では、要素でイベントが処理されるときに呼び出されるハンドラー メソッドの名前を指定します。  WPF XAML で添付イベントを使用することはあまり一般的ではありません。  詳細については、「[添付イベントの概要](../../../../docs/framework/wpf/advanced/attached-events-overview.md)」を参照してください。  
  
<a name="base_classes_and_xaml"></a>   
## 基本型と XAML  
 WPF XAML とその XAML 名前空間の基礎になっているのは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトに対応する一連の型です。これらのクラスは、XAML のマークアップ要素にも対応しています。  ただし、すべてのクラスを要素に対応付けられるわけではありません。  <xref:System.Windows.Controls.Primitives.ButtonBase> などの抽象クラスや一部の非抽象基本クラスは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクト モデルでは継承のために使用されます。  それでも基本クラスは、抽象クラスも含め、XAML 開発にとって重要です。これは、XAML の各具象要素は、その階層構造内の基本クラスのメンバーを継承するためです。  それらのメンバーには、多くの場合、要素の属性として設定できるプロパティや、処理できるイベントが含まれています。  <xref:System.Windows.FrameworkElement> は、[WPF フレームワーク レベル](GTMT)における [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の具象基本 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] クラスです。  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をデザインする際には、さまざまな図形、パネル、デコレータ、コントロールのクラスを使用しますが、それらはすべて <xref:System.Windows.FrameworkElement> から派生します。  関連する基本クラスの <xref:System.Windows.FrameworkContentElement> は、<xref:System.Windows.FrameworkElement> の [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] を意図的に反映する [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] を使用して、フロー レイアウトのプレゼンテーションに適したドキュメント指向の要素をサポートします。  要素レベルの属性と [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクト モデルの組み合わせにより、一連の共通プロパティをほとんどの具象 XAML 要素で、特定の XAML 要素や基になる型に関係なく設定できるようになっています。  
  
<a name="xaml_security"></a>   
## XAML のセキュリティ  
 XAML は、オブジェクトのインスタンス化と実行を直接表現するマークアップ言語です。  したがって、XAML で作成された要素では、対応する生成コードと同じシステム リソースとのやり取り \(ネットワーク アクセスやファイル システムの入出力など\) が可能です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] セキュリティ フレームワークの [!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)] をサポートしています。  このため、インターネット ゾーンで実行される [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、実行のアクセス許可を制限されます。  "Loose XAML" \(読み込み時に XAML ビューアーによって解釈されるコンパイルされない XAML のページ\) と [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] は、通常このインターネット ゾーンで実行され、同じアクセス許可セットを使用します。  ただし、完全に信頼されたアプリケーションに読み込まれた XAML は、システム リソースに対してホスト アプリケーションと同じアクセス権を持ちます。  詳細については、「[WPF 部分信頼セキュリティ](../../../../docs/framework/wpf/wpf-partial-trust-security.md)」を参照してください。  
  
<a name="loading_xaml_from_code"></a>   
## コードからの XAML の読み込み  
 XAML を使用してすべての UI を定義することもできますが、UI の一部のみを XAML で定義することが適している場合もあります。  この機能を利用すると、部分的なカスタマイズ、情報のローカル保存、XAML を使用したビジネス オブジェクトの提供など、さまざまなシナリオが可能になります。  このようなシナリオで重要になるのは、<xref:System.Windows.Markup.XamlReader> クラスおよびその <xref:System.Windows.Markup.XamlReader.Load%2A> メソッドです。  XAML ファイルを入力とし、そのマークアップから作成された実行時のすべてのオブジェクト ツリーを表す 1 つのオブジェクトが出力となります。  このオブジェクトを、アプリケーション内に既に存在する別のオブジェクトのプロパティとして挿入できます。  そのプロパティが、最終的な表示機能を備え、アプリケーションへの新しいコンテンツの追加を実行エンジンに通知するコンテンツ モデルにおける適切なプロパティであれば、XAML を使用して、実行中のアプリケーションのコンテンツを非常に簡単に修正できます。  ただし、実行中のアプリケーションにファイルを読み込むことは明らかにセキュリティに影響するので、この機能を利用できるのは、一般に完全信頼アプリケーションの場合のみです。  
  
<a name="whats_next"></a>   
## 次の内容  
 ここでは、WPF に適用される XAML 構文の概念と用語の基本的な概要を紹介しました。  ここで使用した用語の詳細については、「[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」を参照してください。  
  
 まだ終えていない場合は、「[チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)」のチュートリアルの演習に挑戦してみることをお勧めします。  このチュートリアルで説明されているマークアップ中心のアプリケーションを作成すると、ここで説明した多くの概念の理解が深まります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、<xref:System.Windows.Application> クラスに基づく特有のアプリケーション モデルを使用します。  詳細については、「[アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)」を参照してください。  
  
 XAML を含むアプリケーションをコマンド ラインから作成する方法、および [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] を使用して作成する方法の詳細については、「[WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプロパティの汎用性についての詳細、および[依存関係プロパティ](GTMT)の概念の概要については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
## 参照  
 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)   
 [WPF における XAML とカスタム クラス](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [XAML 名前空間 \(x:\) 言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)   
 [WPF XAML 拡張機能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)   
 [基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)