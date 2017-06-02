---
title: "PropertyPath の XAML 構文 | Microsoft Docs"
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
  - "PropertyPath オブジェクト"
  - "XAML, PropertyPath オブジェクト"
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# PropertyPath の XAML 構文
<xref:System.Windows.PropertyPath> オブジェクトは、<xref:System.Windows.PropertyPath> 型を値として使用する各種プロパティを設定するうえで、複雑な [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] インライン構文をサポートします。  このトピックでは、バインディング構文とアニメーション構文に適用される <xref:System.Windows.PropertyPath> 構文について説明します。  
  
   
  
<a name="where"></a>   
## PropertyPath を使用する場所  
 <xref:System.Windows.PropertyPath> は、さまざまな [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 機能で使用される共通のオブジェクトです。  共通の <xref:System.Windows.PropertyPath> を使用してプロパティ パス情報を伝えるにもかかわらず、<xref:System.Windows.PropertyPath> を型として使用する各機能の使用法はそれぞれ異なります。  そのため、機能ごとに構文を説明する方が実際的です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は主に、<xref:System.Windows.PropertyPath> を使用して、オブジェクト データ ソースのプロパティを走査するオブジェクト モデル パスを記述し、ターゲット アニメーションのターゲット パスを記述します。  
  
 <xref:System.Windows.Setter.Property%2A?displayProperty=fullName> など一部のスタイル プロパティやテンプレート プロパティでは、一見すると <xref:System.Windows.PropertyPath> と似ているプロパティの修飾名が使用されます。  しかし、これは実際の <xref:System.Windows.PropertyPath> ではなく、<xref:System.Windows.DependencyProperty> の型コンバーターと組み合わせて WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサで有効化される、*owner.property* の修飾文字列形式の使用法です。  
  
<a name="databinding_s"></a>   
## データ バインディングにおけるオブジェクトの PropertyPath  
 データ バインディングは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の機能であり、[依存関係プロパティ](GTMT)のターゲット値にバインドできます。  ただし、このようなデータ バインディングのソースが[依存関係プロパティ](GTMT)である必要はなく、適切なデータ プロバイダーで認識される任意のプロパティ型でかまいません。  プロパティ パスは特に <xref:System.Windows.Data.ObjectDataProvider> で使用され、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクトのバインディング ソースとそのプロパティを取得するのに使用されます。  
  
 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] へのデータ バインディングでは、<xref:System.Windows.PropertyPath> が使用されないことに注意してください。これは、<xref:System.Windows.Data.Binding> 内で <xref:System.Windows.Data.Binding.Path%2A> を使用しないためです。  代わりに、<xref:System.Windows.Data.Binding.XPath%2A> を使用して、有効な XPath 構文をデータの [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] に指定します。  <xref:System.Windows.Data.Binding.XPath%2A> も文字列として指定されますが、ここでは説明しません。「[XMLDataProvider と XPath クエリを使用して XML データにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)」を参照してください。  
  
 データ バインディングにおけるプロパティ パスを理解するうえで鍵となるのは、個々のプロパティ値をバインドの対象にすることも、リストまたはコレクションを使用するターゲット プロパティにバインドすることもできるということです。  コレクションをバインドする場合 \(コレクション内のデータ項目の数に応じて拡張される <xref:System.Windows.Controls.ListBox> をバインドする場合など\)、プロパティ パスは個々のコレクション項目を参照するのではなく、コレクション オブジェクトを参照する必要があります。  データ バインディング エンジンは、データ ソースとして使用されるコレクションをバインディング ターゲットの型に自動的に一致させます。その結果、<xref:System.Windows.Controls.ListBox> への項目配列の読み込みなどの処理が行われます。  
  
<a name="singlecurrent"></a>   
### データ コンテキストとしての直接のオブジェクト上の単一のプロパティ  
  
```  
<Binding Path="propertyName" .../>  
```  
  
 *propertyName* は、<xref:System.Windows.Data.Binding.Path%2A> の使用に対して、現在の <xref:System.Windows.FrameworkElement.DataContext%2A> 内にあるプロパティの名前に解決される必要があります。  バインディングがソースを更新する場合、そのプロパティは読み書き可能であり、ソース オブジェクトは変更可能である必要があります。  
  
<a name="singleindex"></a>   
### データ コンテキストとしての直接のオブジェクト上の単一のインデクサー  
  
```  
<Binding Path="[key]" .../>  
```  
  
 `key` には、ディクショナリまたはハッシュ テーブルの型指定されたインデックス、または配列の整数インデックスを指定する必要があります。  また、キーの値は、適用先のプロパティに直接バインドできる型である必要があります。  たとえば、文字列キーと文字列値が含まれるハッシュ テーブルをこのように使用することで、<xref:System.Windows.Controls.TextBox> の Text にバインドできます。  キーがコレクションまたはサブインデックスを指す場合は、この構文を使用して、ターゲット コレクション プロパティにバインドできます。  それ以外の場合は、`<Binding Path="[``key``].``propertyName``" .../>` などの構文を通じて、特定のプロパティを参照する必要があります。  
  
 必要に応じて、インデックスの型を指定できます。  インデックス付きプロパティ パスのこの特徴の詳細については、「<xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName>」を参照してください。  
  
<a name="multipleindirect"></a>   
### 複数プロパティ \(間接的なプロパティの対象化\)  
  
```  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName` は、現在の <xref:System.Windows.FrameworkElement.DataContext%2A> であるプロパティの名前に解決される必要があります。  パス プロパティ `propertyName` および `propertyName2` は、リレーションシップ内に存在する任意のプロパティにすることができます。`propertyName2` は、`propertyName` の値である型に存在するプロパティです。  
  
<a name="singleattached"></a>   
### 添付または型修飾された単一のプロパティ  
  
```  
<object property="(ownerType.propertyName)" .../>  
```  
  
 かっこは、<xref:System.Windows.PropertyPath> 内のこのプロパティを、部分修飾を使用して構築する必要があることを示します。  XML 名前空間を使用して、適切なマッピングを含む型を検出できます。  `ownerType` は、各アセンブリ内の <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 宣言を通じて、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサがアクセスできる型を検索します。  ほとんどのアプリケーションは、[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 名前空間に対応付けられた既定の XML 名前空間を持ちます。そのため、プレフィックスは通常、カスタム型や、名前空間の外部の型に限って必要です。  `propertyName` は、`ownerType` に存在するプロパティの名前に解決される必要があります。  この構文は、通常、次のいずれかの場合に使用されます。  
  
-   指定されたターゲット型を持たないスタイルまたはテンプレート内の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でパスが指定されている場合。  通常、これ以外のケースでの修飾子の使用は無効です。スタイルやテンプレート以外のケースでは、プロパティは型ではなくインスタンス上に存在します。  
  
-   プロパティが添付プロパティの場合。  
  
-   静的プロパティにバインドしている場合。  
  
 ストーリーボード ターゲットとして使用する場合、`propertyName` として指定されるプロパティは、<xref:System.Windows.DependencyProperty> にする必要があります。  
  
<a name="sourcetraversal"></a>   
### ソースの走査 \(コレクションの階層のバインディング\)  
  
```  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 この構文内の \/ を使用して階層的なデータ ソース オブジェクト内を移動し、後続する \/ 文字で階層への複数ステップがサポートされます。  ソースの走査は現在のレコード ポインター位置に対応しており、これはデータをビューの UI と同期することによって決定されます。  階層的なデータ ソース オブジェクトのバインディング、およびデータ バインディングにおける現在のレコード ポインターの概念の詳細については、「[階層データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)」または「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
> [!NOTE]
>  この構文は、一見すると [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] に似ています。  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データ ソースにバインドするための実際の [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] 式は <xref:System.Windows.Data.Binding.Path%2A> 値としては使用されず、代わりに、同時には指定できない <xref:System.Windows.Data.Binding.XPath%2A> プロパティで使用される必要があります。  
  
### コレクション ビュー  
 名前付きコレクション ビューを参照するには、コレクション ビュー名の前にハッシュ記号 \(`#`\) を付けます。  
  
### 現在のレコード ポインター  
 コレクション ビューまたはマスター詳細データ バインディング シナリオの現在のレコード ポインターを参照するには、パス文字列の先頭にスラッシュ \(`/`\) を追加します。  スラッシュより後ろのパスは、現在のレコード ポインターから開始して走査されます。  
  
### 複数のインデクサー  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 あるオブジェクトが複数のインデクサーをサポートする場合、そのインデクサーは、配列参照構文のように、順番に指定できます。  当該のオブジェクトは、現在のコンテキスト、または複数のインデクサー オブジェクトが含まれるプロパティの値です。  
  
 既定では、インデクサー値は、基になるオブジェクトの特性を使用して型指定されます。  必要に応じて、インデックスの型を指定できます。  インデクサーの型指定の詳細については、「<xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName>」を参照してください。  
  
<a name="mixing"></a>   
### 構文の混合  
 上記の各構文は、混在させることができます。  たとえば、<xref:System.Windows.Media.SolidColorBrush> オブジェクトのピクセル グリッド配列が含まれる、`ColorGrid` プロパティの特定の x、y にある色へのプロパティ パスを作成する例を次に示します。  
  
```  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### プロパティ パス文字列のエスケープ  
 特定のビジネス オブジェクトでは、正しく解析するために、プロパティ パス文字列にエスケープ シーケンスが必要な場合があります。  このような文字の多くには、通常ビジネス オブジェクトを定義するために使用される言語において、名前付けの相互作用に関する同様の問題があるので、エスケープが必要になることはほとんどありません。  
  
-   インデクサー \(\[ \]\) 内では、キャレット文字 \(^\) は次の文字をエスケープします。  
  
-   XML 言語定義で特別な意味を持つ特定の文字を \(XML エンティティを使用して\) エスケープする必要があります。  文字 "&" をエスケープするには、`&` を使用します。  タグの終了を示す "\>" をエスケープするには、`>` を使用します。  
  
-   マークアップ拡張機能の処理に関する WPF XAML パーサーの動作で特別な意味を持つ文字を、\(バックスラッシュ `\` を使用して\) エスケープする必要があります。  
  
    -   バックスラッシュ \(`\`\) は、それ自体がエスケープ文字です。  
  
    -   等号 \(`=`\) は、プロパティ名とプロパティ値を区切ります。  
  
    -   コンマ \(`,`\) は、複数のプロパティを区切ります。  
  
    -   右中かっこ \(`}`\) は、マークアップ拡張機能の終了を示します。  
  
> [!NOTE]
>  厳密に言うと、これらのエスケープはストーリーボードのプロパティ パスに役立ちますが、通常は既存の WPF オブジェクトのオブジェクト モデルを走査するので、エスケープは不要です。  
  
<a name="databinding_sa"></a>   
## アニメーション ターゲットの PropertyPath  
 アニメーションのターゲット プロパティは[依存関係プロパティ](GTMT)であり、<xref:System.Windows.Freezable> またはプリミティブ型を使用します。  ただし、型のターゲット プロパティと最終的なアニメーション プロパティは異なるオブジェクト上に存在できます。  アニメーションの場合は、プロパティ パスを使用して、プロパティ値内のオブジェクトとプロパティのリレーションシップを調べることによって、名前付きのアニメーション ターゲット オブジェクトのプロパティと目的のターゲット アニメーション プロパティの間の接続が定義されます。  
  
<a name="general"></a>   
### アニメーションに関するオブジェクトとプロパティの一般的な注意事項  
 一般的なアニメーションの概念の詳細については、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」および「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
 アニメーション化される値型またはプロパティは、<xref:System.Windows.Freezable> 型またはプリミティブである必要があります。  パスを開始するプロパティは、指定された <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 型に存在する[依存関係プロパティ](GTMT)の名前に解決される必要があります。  
  
 既にフリーズしている <xref:System.Windows.Freezable> のアニメーションの複製をサポートするには、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> が、<xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> 派生クラスである必要があります。  
  
<a name="singlestepanim"></a>   
### ターゲット オブジェクト上の単一プロパティ  
  
```  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName` は、指定された <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 型に存在する[依存関係プロパティ](GTMT)の名前に解決される必要があります。  
  
<a name="indirectanim"></a>   
### 間接的なプロパティの対象化  
  
```  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName` は、指定された <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 型に存在する、<xref:System.Windows.Freezable> 値型またはプリミティブのプロパティである必要があります。  
  
 `propertyName2` は、`propertyName` の値であるオブジェクトに存在する[依存関係プロパティ](GTMT)の名前に解決される必要があります。  言い換えると、`propertyName2` は、`propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A> 型の依存関係プロパティとして存在する必要があります。  
  
 適用されるスタイルとテンプレートにより、アニメーションの間接的な対象化が必要です。  アニメーションを対象にするには、ターゲット オブジェクトの <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> が必要であり、その名前は [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md) または <xref:System.Windows.FrameworkElement.Name%2A> によって設定されます。  テンプレート要素とスタイル要素にも名前を設定できますが、その名前は、スタイルとテンプレートの名前スコープ内でのみ有効です   \(テンプレートとスタイルがアプリケーション マークアップと名前スコープを共有していない場合、名前は一意ではありません。  スタイルとテンプレートはインスタンス間で完全に共有されており、重複する名前が永続化されます\)。このため、アニメーション化する要素の個々のプロパティがスタイルやテンプレートに基づく場合は、スタイル テンプレートに基づかない、名前付きの要素インスタンスで操作を開始し、スタイルまたはテンプレートのビジュアル ツリーに対象を移動し、アニメーション化する目的のプロパティにアクセスします。  
  
 たとえば、<xref:System.Windows.Controls.Panel> の <xref:System.Windows.Controls.Panel.Background%2A> プロパティは、テーマ テンプレートに基づく完全な <xref:System.Windows.Media.Brush> \(実際には <xref:System.Windows.Media.SolidColorBrush>\) です。  <xref:System.Windows.Media.Brush> を完全にアニメーション化するには、BrushAnimation \(多くの場合、<xref:System.Windows.Media.Brush> 型ごとに 1 つ\) であることが必要ですが、このような型はありません。  Brush をアニメーション化するには、代わりに、特定の <xref:System.Windows.Media.Brush> 型のプロパティをアニメーション化します。  <xref:System.Windows.Media.SolidColorBrush> からその <xref:System.Windows.Media.SolidColorBrush.Color%2A> までを取得して、<xref:System.Windows.Media.Animation.ColorAnimation> を適用します。  この例のプロパティ パスは `Background.Color` です。  
  
<a name="attachedanim"></a>   
### 添付プロパティ  
  
```  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 かっこは、<xref:System.Windows.PropertyPath> 内のこのプロパティを、部分修飾を使用して構築する必要があることを示します。  XML 名前空間を使用して型を検出できます。  `ownerType` は、各アセンブリ内の <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 宣言を通じて、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサがアクセスできる型を検索します。  ほとんどのアプリケーションは、[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 名前空間に対応付けられた既定の XML 名前空間を持ちます。そのため、プレフィックスは通常、カスタム型や、名前空間の外部の型に限って必要です。  `propertyName` は、`ownerType` に存在するプロパティの名前に解決される必要があります。  `propertyName` として指定されるプロパティは、<xref:System.Windows.DependencyProperty> にする必要があります   \(すべての [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 添付プロパティは、依存関係プロパティとして実装されます。そのため、この問題は、カスタム添付プロパティにのみ関係します\)。  
  
<a name="indexanim"></a>   
### インデクサー  
  
```  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 ほとんどの依存関係プロパティまたは <xref:System.Windows.Freezable> 型は、インデクサーをサポートしていません。  そのため、アニメーション パス内でインデクサーを使用するのは、名前付きターゲット上でチェーンを開始するプロパティと、最終的にアニメーション化されるプロパティの間の中間位置に限られます。  提供される構文の中で、これは `propertyName2` です。  たとえば、`RenderTransform.Children[1].Angle` などのプロパティ パス内で、中間プロパティが <xref:System.Windows.Media.TransformGroup> などのコレクションの場合は、インデクサーの使用が必要になることがあります。  
  
<a name="ppincode"></a>   
## コード内の PropertyPath  
 <xref:System.Windows.PropertyPath> を構築する方法を含めて、<xref:System.Windows.PropertyPath> をコードで使用する方法については、<xref:System.Windows.PropertyPath> の参照トピックを参照してください。  
  
 一般に、<xref:System.Windows.PropertyPath> は、バインディングでの使用と単純なアニメーションでの使用を目的とするコンストラクター、および複雑なアニメーションでの使用を目的とするコンストラクターの、2 種類のコンストラクターを使用するように設計されています。  オブジェクトが文字列であるバインディング使用の場合は、<xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> シグネチャを使用します。  オブジェクトが <xref:System.Windows.DependencyProperty> である 1 ステップのアニメーション パスの場合は、<xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> シグネチャを使用します。  複雑なアニメーションの場合は、[PropertyPath\(String, Object\<xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> シグネチャを使用します。  後者のコンストラクターでは、先頭のパラメーター用のトークン文字列と、トークン文字列内の位置に設定されるオブジェクトの配列を使用して、プロパティ パスのリレーションシップを定義します。  
  
## 参照  
 <xref:System.Windows.PropertyPath>   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)