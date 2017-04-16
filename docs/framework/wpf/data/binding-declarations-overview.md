---
title: "バインディング宣言の概要 | Microsoft Docs"
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
  - "バインド (データを), 宣言"
  - "バインディング宣言"
  - "データ バインディング, 宣言"
  - "マークアップ拡張機能"
  - "オブジェクト要素構文"
  - "構文, オブジェクト要素"
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# バインディング宣言の概要
ここでは、バインディングを宣言するさまざまな方法について説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Prereq"></a>   
## 必要条件  
 このトピックを読む前に、マークアップ拡張機能の概念と使用方法を理解していることが重要です。  マークアップ拡張機能の詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
 ここでは、データ バインディングの概念については説明しません。  データ バインディングの概念については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
<a name="BindinginXAML"></a>   
## XAML でバインディングを宣言する  
 ここでは、XAML でバインディングを宣言する方法について説明します。  
  
<a name="MarkupExtensionSyntax"></a>   
### マークアップ拡張機能の使用方法  
 <xref:System.Windows.Data.Binding> はマークアップ拡張機能です。  バインディング拡張を使用してバインディングを宣言する場合、その宣言は、`Binding` キーワードの後に一連の句をコンマ \(,\) で区切って並べたものになります。  バインディング宣言では、句は任意の順序で並べることができ、また、さまざまな組み合わせが可能です。  句は *名前*\=*値* という形のペアで、*名前*は <xref:System.Windows.Data.Binding> プロパティの名前、*値* はそのプロパティに設定する値です。  
  
 バインディング宣言文字列をマークアップで作成する場合、それらの文字列はターゲット オブジェクトの特定の[依存関係プロパティ](GTMT)に関連付ける必要があります。  バインディング拡張を使用し、<xref:System.Windows.Data.Binding.Source%2A> プロパティおよび <xref:System.Windows.Data.Binding.Path%2A> プロパティを指定して、<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> プロパティをバインドする方法を次の例に示します。  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <xref:System.Windows.Data.Binding> クラスのほとんどのプロパティは、この方法で指定できます。  バインディング拡張の詳細、およびバインディング拡張を使用して設定できない <xref:System.Windows.Data.Binding> プロパティのリストについては、「[バインドのマークアップ拡張機能](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)」の概要を参照してください。  
  
<a name="ObjectElementSyntax"></a>   
### オブジェクト要素の構文  
 オブジェクト要素構文を使用しても、バインディング宣言を作成できます。  ほとんどの場合、マークアップ拡張機能とオブジェクト要素構文のどちらを使用した場合でも、特別な利点はありません。  ただし、設定するプロパティ値が型変換のない非文字列型である場合のように、目的のシナリオがマークアップ拡張機能でサポートされない場合には、オブジェクト要素構文を使用する必要があります。  
  
 オブジェクト要素構文とマークアップ拡張機能の両方の使用方法を次の例に示します。  
  
 [!code-xml[BindConversionMarkup#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 この例では、拡張構文を使用してバインディングを宣言することにより、<xref:System.Windows.Controls.TextBlock.Foreground%2A> プロパティをバインドしています。  <xref:System.Windows.Controls.TextBlock.Text%2A> プロパティのバインディング宣言では、オブジェクト要素構文を使用しています。  
  
 各種の用語の詳細については、「[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」を参照してください。  
  
<a name="MBandPB"></a>   
### MultiBinding および PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> および <xref:System.Windows.Data.PriorityBinding> は、XAML 拡張構文をサポートしません。  そのため、XAML で <xref:System.Windows.Data.MultiBinding> または <xref:System.Windows.Data.PriorityBinding> を宣言する場合は、オブジェクト要素構文を使用する必要があります。  
  
<a name="BindinginCode"></a>   
## コードでバインディングを作成する  
 バインディングを指定するもう一つの方法として、コード内で <xref:System.Windows.Data.Binding> オブジェクトのプロパティを直接設定する方法があります。  <xref:System.Windows.Data.Binding> オブジェクトを作成し、コードでプロパティを指定する方法を次の例に示します。  この例では、`TheConverter` は <xref:System.Windows.Data.IValueConverter> インターフェイスを実装するオブジェクトです。  
  
 [!code-csharp[BindConversion#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
[!code-csharp[BindConversion#end1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#end1)]
[!code-vb[BindConversion#end1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#end1)]  
  
 バインドする対象のオブジェクトが <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> の場合は、<xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=fullName> を使用する代わりに、オブジェクトで `SetBinding` メソッドを直接呼び出すことができます。  例については、「[コードでバインディングを作成する](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)」を参照してください。  
  
<a name="Path_Syntax"></a>   
## パス構文をバインドする  
 バインドするソースの値を指定するには、<xref:System.Windows.Data.Binding.Path%2A> プロパティを使用します。  
  
-   特に単純な使用例では、<xref:System.Windows.Data.Binding.Path%2A> プロパティ値は `Path=PropertyName` など、バインディングに使用するソース オブジェクトのプロパティの名前になります。  
  
-   プロパティのサブプロパティは、[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 内の構文と同様の構文によって指定できます。  たとえば、`Path=ShoppingCart.Order` 句は、オブジェクトまたはプロパティ `ShoppingCart` のサブプロパティ `Order` へのバインディングを設定します。  
  
-   [添付プロパティ](GTMT)にバインドするには、[添付プロパティ](GTMT)をかっこで囲みます。  たとえば、[添付プロパティ](GTMT) <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> にバインドする構文は、`Path=(DockPanel.Dock)` です。  
  
-   プロパティのインデクサーは、インデクサーが適用されるプロパティ名の後に続く角かっこ内に指定できます。  たとえば、`Path=ShoppingCart[0]` 句は、プロパティの内部のインデックスのリテラル文字列 "0" の処理方法に対応するインデックスにバインディングを設定します。  入れ子になったインデクサーもサポートされています。  
  
-   インデクサーとサブプロパティは、`Path` 句に混在させることができます。たとえば、`Path=ShoppingCart.ShippingInfo[MailingAddress,Street]` のように使用できます。  
  
-   インデクサーの内側では、複数のインデクサー パラメーターをコンマ \(,\) で区切って指定できます。  各パラメーターの型は、かっこを使用して指定できます。  たとえば、`Path="[(sys:Int32)42,(sys:Int32)24]"` のように指定します。ここで、`sys` は `System` 名前空間にマップされます。  
  
-   ソースがコレクション ビューであるときは、現在の項目をスラッシュ \(\/\) で指定できます。  たとえば、`Path=/` 句は、ビュー内の現在の項目へのバインディングを設定します。  ソースがコレクションである場合、この構文は、既定のコレクション ビューの現在の項目を指定します。  
  
-   プロパティ名とスラッシュを組み合わせて、コレクションである各プロパティを走査することができます。  たとえば、`Path=/Offices/ManagerName` は、それ自体がコレクションである `Offices` プロパティを含む、ソース コレクションの現在の項目を指定します。  その現在の項目は、`ManagerName` プロパティを含むオブジェクトです。  
  
-   また、ピリオド \(.\) パスを使用して現在のソースにバインドすることもできます。  たとえば、`Text="{Binding}"` は `Text="{Binding Path=.}"` と同じ意味です。  
  
### エスケープ機構  
  
-   インデクサー \(\[ \]\) 内では、キャレット文字 \(^\) は次の文字をエスケープします。  
  
-   XAML で <xref:System.Windows.Data.Binding.Path%2A> を指定する場合は、XML 言語定義で特別な意味を持つ特定の文字についても \(XML エンティティを使用して\) 次のようにエスケープする必要があります。  
  
    -   文字 "&" をエスケープするには、`&` を使用します。  
  
    -   タグの終了を示す "\>" をエスケープするには、`>` を使用します。  
  
-   また、マークアップ拡張構文を使用して、属性内にバインディング全体を記述する場合には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] マークアップ拡張機能パーサーにとって特別な意味を持つ次の文字を \(バックスラッシュ \\ を使用して\) エスケープする必要があります。  
  
    -   バックスラッシュ \(\\\) は、それ自体がエスケープ文字です。  
  
    -   等号 \(\=\) は、プロパティ名とプロパティ値を区切ります。  
  
    -   コンマ \(,\) は、複数のプロパティを区切ります。  
  
    -   右中かっこ \(}\) は、マークアップ拡張機能の終了を示します。  
  
<a name="Default"></a>   
## 既定の動作  
 宣言に指定がない場合の既定の動作は次のとおりです。  
  
-   [バインディング ソース](GTMT)値と[バインディング ターゲット](GTMT)値を相互に型変換する既定のコンバーターが作成されます。  型変換できない場合、既定のコンバーターは `null` を返します。  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A> を設定しない場合、バインディング エンジンでは、[バインディング ターゲット](GTMT) オブジェクトの `Language` プロパティが使用されます。  XAML では、このプロパティは既定で "en\-US" に設定されるか、明示的に設定されている場合はページのルート要素 \(または任意の要素\) から値を継承します。  
  
-   バインディングに既にデータ コンテキストが存在し \(たとえば、親要素から継承したデータ コンテキストの場合\)、そのコンテキストから返される項目またはコレクションがすべてバインディングするために適切であり、パスを変更する必要もない場合には、バインディング宣言は、`{Binding}` のように、句を一切含めないで宣言することができます。これは、バインディングがコレクションに影響を与えるデータ スタイルに対してバインディングを指定する場合に多く用いられる方法です。  詳細については、「[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)」の「オブジェクト全体をバインディング ソースとして使用する」セクションを参照してください。  
  
-   既定の <xref:System.Windows.Data.Binding.Mode%2A> は、バインドされる[依存関係プロパティ](GTMT)に応じて、一方向と双方向のいずれかになります。  バインディングを目的どおりに動作させるために、バインディング モードを常に明示的に宣言できます。  一般に、ユーザーが編集できる <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> や <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=fullName> などのコントロール プロパティは、既定で双方向のバインディングであり、それ以外のほとんどのプロパティは既定で一方向のバインディングになります。  
  
-   既定の <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 値も、バインドされる[依存関係プロパティ](GTMT)に応じて、<xref:System.Windows.Data.UpdateSourceTrigger> と <xref:System.Windows.Data.UpdateSourceTrigger> のいずれかになります。  ほとんどの[依存関係プロパティ](GTMT)の既定値は <xref:System.Windows.Data.UpdateSourceTrigger> であるのに対し、<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> プロパティの既定値は <xref:System.Windows.Data.UpdateSourceTrigger> です。  
  
## 参照  
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [データ バインド](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [PropertyPath の XAML 構文](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)