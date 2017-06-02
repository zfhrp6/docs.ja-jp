---
title: "カスタム依存関係プロパティ | Microsoft Docs"
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
  - "カスタム依存関係プロパティ"
  - "依存関係プロパティ, カスタム"
  - "実装, ラッパー"
  - "メタデータ, プロパティ"
  - "プロパティ, メタデータ"
  - "プロパティ, 登録"
  - "登録 (プロパティを)"
  - "ラッパー, 実装"
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# カスタム依存関係プロパティ
ここでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの開発者とコンポーネント作成者に対して、カスタム[依存関係](GTMT)の作成を推奨する理由を説明し、その実装手順と共に、プロパティのパフォーマンス、操作性、または汎用性の向上につながるいくつかの実装オプションを示します。  
  
   
  
<a name="prerequisites"></a>   
## 必要条件  
 このトピックでは、ユーザーが [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスの既存の依存関係プロパティの使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」トピックを通読していることを前提としています。  このトピックの例を理解するには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] についての理解があり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの記述方法を理解していることも必要です。  
  
<a name="whatis"></a>   
## 依存関係プロパティとは  
 通常なら[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティになるプロパティを[依存関係プロパティ](GTMT)として実装すると、そのプロパティでスタイル設定、データ バインディング、継承、アニメーション、および既定値をサポートできるようになります。  依存関係プロパティは、<xref:System.Windows.DependencyProperty.Register%2A> メソッド \(または <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>\) を呼び出すことによって [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムに登録され、<xref:System.Windows.DependencyProperty> 識別子フィールドによって補足されるプロパティです。  依存関係プロパティを使用できるのは <xref:System.Windows.DependencyObject> 型のみですが、<xref:System.Windows.DependencyObject> は [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラス階層の中で非常に高い位置にあるため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で使用できるクラスの大多数は依存関係プロパティをサポートすることができます。  依存関係プロパティと、この [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] で依存関係プロパティの説明に使用している一部の用語と規則の詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
<a name="example_dp"></a>   
## 依存関係プロパティの例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のクラスに実装されている依存関係プロパティは多数あり、その例として <xref:System.Windows.Controls.Control.Background%2A> プロパティ、<xref:System.Windows.FrameworkElement.Width%2A> プロパティ、<xref:System.Windows.Controls.TextBox.Text%2A> プロパティなどが挙げられます。  クラスによって公開される依存関係プロパティにはそれぞれ <xref:System.Windows.DependencyProperty> 型の public static フィールドが対応付けられ、その同じクラスで公開されます。これは、依存関係プロパティの識別子です。  この識別子には、名前付け規則に従って、[依存関係プロパティ](GTMT)の名前に文字列 `Property` を加えた名前が付けられます。  たとえば、<xref:System.Windows.Controls.Control.Background%2A> プロパティに対応する <xref:System.Windows.DependencyProperty> 識別子フィールドの名前は <xref:System.Windows.Controls.Control.BackgroundProperty> になります。  識別子には[依存関係プロパティ](GTMT)に関する登録情報が格納され、後に[依存関係プロパティ](GTMT)関連のその他の操作 \(<xref:System.Windows.DependencyObject.SetValue%2A> の呼び出しなど\) に使用されます。  
  
 「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」で説明しているとおり、"ラッパー" の実装のため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の依存関係プロパティ \(大部分の[添付プロパティ](GTMT)は除く\) はいずれも [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティを兼ねます。  したがって、他の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティを使用するときと同様にラッパーを定義する [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] アクセサーをコードから呼び出すことによって、依存関係プロパティを取得または設定することができます。  通常、確立された依存関係プロパティのコンシューマーは、基になるプロパティ システムへのコネクション ポイントである <xref:System.Windows.DependencyObject> の <xref:System.Windows.DependencyObject.GetValue%2A> メソッドや <xref:System.Windows.DependencyObject.SetValue%2A> メソッドは使用しません。  [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティの既存の実装により、識別子フィールドが適切に使用され、プロパティの `get` ラッパーと `set` ラッパーの実装内で <xref:System.Windows.DependencyObject.GetValue%2A> と <xref:System.Windows.DependencyObject.SetValue%2A> があらかじめ呼び出されるようになっています。  カスタム依存関係プロパティを自分で実装する場合は、同様の方法でラッパーを定義することになります。  
  
<a name="backing_with_dp"></a>   
## 依存関係プロパティの実装が必要になるケース  
 プロパティをクラスに実装する場合、対象となるクラスが <xref:System.Windows.DependencyObject> から派生したものであれば、そのプロパティを <xref:System.Windows.DependencyProperty> 識別子で補足することによって依存関係プロパティにするという選択肢があります。  プロパティを依存関係プロパティにする必要性や妥当性の有無は、それぞれのシナリオのニーズによって異なります。  プロパティをプライベート フィールドで補足する通常の手法で十分な場合もあります。  ただし、プロパティで次のいずれか 1 つ以上の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 機能がサポートされるようにするには、必ず[依存関係プロパティ](GTMT)として実装する必要があります。  
  
-   プロパティをスタイル内で設定する機能。  詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
-   プロパティでデータ バインディングをサポートする機能。  依存関係プロパティのデータ バインディングの詳細については、「[2 つのコントロールのプロパティをバインドする](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md)」を参照してください。  
  
-   プロパティを動的リソース参照で設定する機能。  詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
-   プロパティ値を要素ツリー内の親要素から自動的に継承する機能。  この場合、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] アクセス用のプロパティ ラッパーを作成する場合でも、<xref:System.Windows.DependencyProperty.RegisterAttached%2A> メソッドで登録します。  詳細については、「[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)」を参照してください。  
  
-   プロパティをアニメーション化する機能。  詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
-   プロパティの以前の値がプロパティ システムのアクション、環境、ユーザー、またはスタイルの読み込みや使用によって変更された場合に、プロパティ システムから報告を受ける機能。  プロパティのメタデータを使用することによって、プロパティでコールバック メソッドを指定し、プロパティ システムがプロパティ値の決定的な変更を確認するたびに、そのメソッドが呼び出されるようにすることができます。  関連する概念として、プロパティ値の強制型変換があります。  詳細については、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」を参照してください。  
  
-   プロパティ値の変更に伴ってレイアウト システムで要素のビジュアルの再構成が必要になるかどうかの報告を受けるなど、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロセスでも使用される、確立されたメタデータ規則を使用する機能。  または、メタデータのオーバーライドを使用して、メタデータに基づいた既定値などの特性を派生クラスで変更する機能。  
  
-   カスタム コントロールのプロパティが、**\[プロパティ\]** ウィンドウの編集など、[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]のサポートを受ける機能。  詳細については、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
 これらのシナリオを検討するときは、まったく新しいプロパティを実装するのではなく、既存の[依存関係プロパティ](GTMT)のメタデータをオーバーライドすることによって、自分のシナリオを実現できるかどうかも考慮する必要があります。  メタデータのオーバーライドが実際的かどうかはシナリオに依存し、そのシナリオが [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の既存の依存関係プロパティおよびクラスとどの程度似ているかにもよります。  既存のプロパティのメタデータをオーバーライドする方法の詳細については、「[依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)」を参照してください。  
  
<a name="checklist"></a>   
## 依存関係プロパティを定義する場合のチェックリスト  
 依存関係プロパティの定義は、4 つの概念で構成されています。  これらの概念は、実装内では 1 行のコードで表されるものもあるため、必ずしも厳密な手順というわけではありません。  
  
-   \(オプション\) 依存関係プロパティのプロパティ メタデータを作成します。  
  
-   プロパティ システムにプロパティ名を登録します。その際、所有者型およびプロパティ値の型を指定します。  また、プロパティ メタデータを使用する場合は、併せて指定します。  
  
-   所有者型に <xref:System.Windows.DependencyProperty> 識別子を `public` `static` `readonly` フィールドとして定義します。  
  
-   依存関係プロパティと同じ名前で、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] の "ラッパー" プロパティを定義します。  [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] の "ラッパー" プロパティの `get` および `set` アクセサーを、基になる依存関係プロパティと連係するように実装します。  
  
<a name="registering"></a>   
### プロパティ システムへのプロパティの登録  
 プロパティを[依存関係プロパティ](GTMT)にするには、そのプロパティをプロパティ システムによって保持されるテーブルに登録し、以降のプロパティ システム操作で修飾子として使用される一意の識別子を付与する必要があります。  これらの操作は内部操作の場合もあれば、独自のコードによるプロパティ システム [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] の呼び出しの場合もあります。  プロパティを登録するには、クラスの本文 \(クラス内のメンバー定義以外の部分\) で <xref:System.Windows.DependencyProperty.Register%2A> メソッドを呼び出します。  <xref:System.Windows.DependencyProperty.Register%2A> メソッドを呼び出すと、その戻り値として識別子フィールドも提供されます。  <xref:System.Windows.DependencyProperty.Register%2A> の呼び出しを他のメンバー定義の外で行うのは、この戻り値を使用して、<xref:System.Windows.DependencyProperty> 型の `public` `static` `readonly` フィールドをクラスの一部として割り当てて作成するためです。  このフィールドは、依存関係プロパティの識別子になります。  
  
 [!code-csharp[WPFAquariumSln#RegisterAG](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
 [!code-vb[WPFAquariumSln#RegisterAG](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]  
  
<a name="nameconventions"></a>   
### 依存関係プロパティの名前付け規則  
 依存関係プロパティに関しては確立された名前付け規則があり、例外的な状況を除いて必ずその規則に従う必要があります。  
  
 依存関係プロパティ自体の基本的な名前 \(この例では "AquariumGraphic"\) を、<xref:System.Windows.DependencyProperty.Register%2A> の最初のパラメーターとして指定します。  その名前は、それぞれの登録型の中で一意である必要があります。  基本型を通じて継承される依存関係プロパティは、既に登録型の一部であると見なされ、継承されたプロパティの名前を再び登録することはできません。  ただし、その依存関係プロパティが継承されていない場合でも、依存関係プロパティの所有者として、クラスを追加する方法はあります。詳細については、「[依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)」を参照してください。  
  
 識別子フィールドを作成するときは、プロパティの登録名にサフィックス `Property` を加えた名前を付けます。  このフィールドは依存関係プロパティの識別子であり、ラッパー内で行う <xref:System.Windows.DependencyObject.SetValue%2A> と <xref:System.Windows.DependencyObject.GetValue%2A> の呼び出しの入力として、また、独自のコード、許可した外部コード、プロパティ システム、および場合によっては [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサによるプロパティへのその他のコード アクセスの入力として、後で使用されます。  
  
> [!NOTE]
>  通常の実装ではクラスの本文で依存関係プロパティを定義しますが、クラスの静的コンストラクターで依存関係プロパティを定義することも可能です。  依存関係プロパティを初期化するために複数のコード行が必要な場合は、この方法が理にかなっています。  
  
<a name="wrapper1"></a>   
### "ラッパー" の実装  
 ラッパー実装では、`get` の実装で <xref:System.Windows.DependencyObject.GetValue%2A> を呼び出し、`set` の実装で <xref:System.Windows.DependencyObject.SetValue%2A> を呼び出します \(ここでは、わかりやすくするために元の登録呼び出しとフィールドを示しています\)。  
  
 例外的な状況を除いて、ラッパー実装は、<xref:System.Windows.DependencyObject.GetValue%2A> と <xref:System.Windows.DependencyObject.SetValue%2A> の処理をそれぞれ実行します。  その理由については、「[XAML 読み込みと依存関係プロパティ](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のクラスに用意されている既存のパブリック依存関係プロパティは、この単純なラッパー実装モデルを使用します。依存関係プロパティのしくみの複雑さは、プロパティ システムの動作に内在するものか、プロパティ メタデータによる強制やプロパティ変更コールバックなどの他の概念に由来するものがほとんどです。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
 繰り返しますが、ラッパー プロパティの名前は通常、プロパティを登録する際に <xref:System.Windows.DependencyProperty.Register%2A> の呼び出しの最初のパラメーターとして選択し、指定した名前と同じである必要があります。  この規則に従わないとプロパティが完全に使用できなくなるわけではありませんが、注意を要するいくつかの問題が発生します。  
  
-   スタイルとテンプレートの一部が機能しません。  
  
-   ほとんどのツールとデザイナーでは、名前付け規則への準拠が [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の適切なシリアル化やプロパティ単位のデザイナー環境支援の条件となっています。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ローダーの現在の実装は、属性を処理するときにラッパーを完全にバイパスし、名前付け規則に依存します。  詳細については、「[XAML 読み込みと依存関係プロパティ](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)」を参照してください。  
  
<a name="metadata"></a>   
### 新しい依存関係プロパティのプロパティ メタデータ  
 依存関係プロパティを登録すると、プロパティ システムを通じた登録によって、プロパティ特性を格納するメタデータ オブジェクトが作成されます。  これらの特性の多くは、プロパティが <xref:System.Windows.DependencyProperty.Register%2A> の簡易署名で登録された場合に設定される既定値を持っています。  <xref:System.Windows.DependencyProperty.Register%2A> のその他の署名を使用すると、必要なメタデータをプロパティの登録時に指定することができます。  依存関係プロパティに対して指定する最も一般的なメタデータは、そのプロパティを使用する新しいインスタンスに適用する既定値を指定します。  
  
 <xref:System.Windows.FrameworkElement> の派生クラスに存在する依存関係プロパティを作成する場合は、基本クラス <xref:System.Windows.PropertyMetadata> ではなく、より特化したメタデータ クラス <xref:System.Windows.FrameworkPropertyMetadata> を使用できます。  <xref:System.Windows.FrameworkPropertyMetadata> クラスのコンストラクターには、さまざまなメタデータ特性を組み合わせて指定できる署名がいくつか存在します。  既定値のみを指定する場合は、<xref:System.Object> 型の単一のパラメーターを受け取る署名を使用します。  そのオブジェクト パラメーターをプロパティの型固有の既定値として渡します \(指定する既定値の型は、<xref:System.Windows.DependencyProperty.Register%2A> の呼び出しで `propertyType` パラメーターとして指定した型である必要があります\)。  
  
 <xref:System.Windows.FrameworkPropertyMetadata> の場合は、プロパティのメタデータ オプション フラグを指定することもできます。  これらのフラグは、登録後にプロパティ メタデータの個々のプロパティに変換され、特定の条件を、レイアウト エンジンなど、他のプロセスに伝えるのに使用されます。  
  
#### 適切なメタデータ フラグの設定  
  
-   プロパティ \(またはその値の変更\) が[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] に影響を及ぼす場合、特に、レイアウト システムが要素をページ内にレイアウトする際のサイズ設定と描画に影響する場合は、<xref:System.Windows.FrameworkPropertyMetadataOptions>、<xref:System.Windows.FrameworkPropertyMetadataOptions>、<xref:System.Windows.FrameworkPropertyMetadataOptions> のいずれか 1 つ以上のフラグを設定します。  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions> は、このプロパティの変更に伴って [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] レンダリングの変更が必要になり、格納オブジェクトが親の内部に必要とする領域が増減する可能性があることを示します。  たとえば、"Width" プロパティにはこのフラグを設定する必要があります。  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions> は、このプロパティの変更に伴って [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] レンダリングの変更が必要になり、その変更が、通常は専用領域の変更は必要としないものの、領域内の配置変更を示唆することを示します。  たとえば、"Alignment" プロパティにはこのフラグを設定する必要があります。  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions> は、その他の何らかの変更が発生しており、レイアウトと測定値には影響しないものの、新たに描画する必要があることを示します。  例としては、既存の要素の色を変更する "Background" などのプロパティが挙げられます。  
  
    -   多くの場合、これらのフラグは、独自に行うプロパティ システムのオーバーライド実装やレイアウト コールバックのメタデータでプロトコルとして使用されます。  <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> コールバックを例にとると、インスタンスのいずれかのプロパティで値の変更が報告され、そのメタデータで <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> が `true` になっていることを条件として、<xref:System.Windows.UIElement.InvalidateArrange%2A> を呼び出すことができます。  
  
-   一部のプロパティは、それが含まれている親要素のレンダリング特性に対し、前述した必要サイズの変更以上の影響を及ぼす可能性があります。  その例としては、フロー ドキュメント モデルで使用される <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> プロパティが挙げられます。このプロパティが変更されると、該当する段落を含むフロー ドキュメントの全体的なレンダリングに変更が生じる可能性があります。  独自のプロパティで同様のケースを識別するには、<xref:System.Windows.FrameworkPropertyMetadataOptions> または <xref:System.Windows.FrameworkPropertyMetadataOptions> を使用します。  
  
-   既定では、依存関係プロパティはデータ バインディングをサポートします。  データ バインディングの現実的なシナリオがない場合や、大きなオブジェクトに対するデータ バインディングのパフォーマンスが問題として認識されている場合には、データ バインディングを意図的に無効にすることができます。  
  
-   既定では、依存関係プロパティのデータ バインディング <xref:System.Windows.Data.Binding.Mode%2A> の既定値は <xref:System.Windows.Data.BindingMode> になっています。  バインディングは、バインディング インスタンスごとにいつでも <xref:System.Windows.Data.BindingMode> に変更できます。詳細については、「[バインディングの方向を指定する](../../../../docs/framework/wpf/data/how-to-specify-the-direction-of-the-binding.md)」を参照してください。  ただし、依存関係プロパティの作成者の判断で、プロパティの既定のバインディング モードを <xref:System.Windows.Data.BindingMode> にすることもできます。  既存の依存関係プロパティの例として、<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=fullName> が挙げられます。このプロパティについては、<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> 設定ロジックと <xref:System.Windows.Controls.MenuItem> の複合が既定のテーマ スタイルと対話するシナリオが想定されています。  <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> プロパティ ロジックは、データ バインディングをネイティブに使用し、他の状態プロパティおよびメソッド呼び出しに応じてプロパティの状態を保持します。  既定で <xref:System.Windows.Data.BindingMode> のバインディングを行うプロパティのもう 1 つの例は <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> です。  
  
-   <xref:System.Windows.FrameworkPropertyMetadataOptions> フラグを設定することによって、カスタム依存関係プロパティでプロパティの継承を有効にすることもできます。  プロパティの継承は、親要素と子要素に共通のプロパティがあるシナリオで役立ちます。子要素がその特定のプロパティ値を親と同じ値に設定することは理にかなっています。  継承可能なプロパティの例としては、<xref:System.Windows.FrameworkElement.DataContext%2A> が挙げられます。このプロパティは、データの表示に関する重要なマスター詳細シナリオを実現するためのバインディング操作に使用されます。  <xref:System.Windows.FrameworkElement.DataContext%2A> を継承可能にすると、そのデータ コンテキストもすべての子要素に継承されます。  プロパティ値の継承により、ページまたはアプリケーションのルートでデータ コンテキストを指定すると、あらゆる子要素内のバインディングについて改めて指定しなくても済むようになります。  <xref:System.Windows.FrameworkElement.DataContext%2A> は、継承によって既定値がオーバーライドされるものの、特定の子要素で常にローカルに設定できることを示す例としても適しています。詳細については、「[階層データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)」を参照してください。  プロパティ値の継承はパフォーマンスの低下につながる可能性があるため、多用は避けてください。詳細については、「[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)」を参照してください。  
  
-   依存関係プロパティがナビゲーション履歴サービスで検出または使用されるようにするかどうかを示すには、<xref:System.Windows.FrameworkPropertyMetadataOptions> フラグを設定します。  例としては、<xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> プロパティが挙げられます。選択コントロールで選択された項目は、ジャーナル履歴のナビゲーション時に保持する必要があります。  
  
<a name="RODP"></a>   
## 読み取り専用の依存関係プロパティ  
 読み取り専用の依存関係プロパティを定義することができます。  ただし、プロパティを読み取り専用として定義する理由に関するシナリオは、これらをプロパティ システムに登録し、識別子を公開する手順同様に、少し異なります。  詳細については、「[読み取り専用の依存関係プロパティ](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)」を参照してください。  
  
<a name="CTDP"></a>   
## コレクション型依存関係プロパティ  
 コレクション型依存関係プロパティには、別途考慮する必要のある実装上の問題がいくつかあります。  詳細については、「[コレクション型依存関係プロパティ](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)」を参照してください。  
  
<a name="SecurityC"></a>   
## 依存関係プロパティに関するセキュリティ上の考慮事項  
 依存関係プロパティは、パブリック プロパティとして宣言する必要があります。  依存関係プロパティの識別子フィールドは、public static フィールドとして宣言する必要があります。  他のアクセス レベル \(保護など\) を宣言しようとしても、依存関係プロパティには、識別子とプロパティ システム [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] の組み合わせを使用して常にアクセスできます。  <xref:System.Windows.LocalValueEnumerator> など、プロパティ システムに組み込まれているメタデータ報告や値決定の [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] により、保護された識別子フィールドにもアクセスできる可能性があります。  詳細については、「[依存関係プロパティのセキュリティ](../../../../docs/framework/wpf/advanced/dependency-property-security.md)」を参照してください。  
  
<a name="DPCtor"></a>   
## 依存関係プロパティとクラス コンストラクター  
 マネージ コード プログラミングでは、\(通例 FxCop などのコード分析ツールによって適用される\) 一般的な方針として、クラス コンストラクターで仮想メソッドを呼び出すことは避ける必要があります。  これは、コンストラクターは派生クラスのコンストラクターの基本の初期化として呼び出すことができ、コンストラクターを通じた仮想メソッドの入力は、構築中のオブジェクト インスタンスの初期化が不完全な状態で実行される可能性があるためです。  <xref:System.Windows.DependencyObject> の派生クラスからさらに派生させる場合は、仮想メソッドの呼び出しと公開をプロパティ システム自体が内部的に行う点に注意が必要です。  これらの仮想メソッドは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムのサービスの一部です。  メソッドをオーバーライドすると、派生クラスが値の決定に参加できるようになります。  ランタイムの初期化で問題が発生するのを避けるため、特定のコンストラクター パターンに従わない限り、依存関係プロパティの値はクラスのコンストラクター内で定義しないでください。  詳細については、「[DependencyObject の安全なコンストラクター パターン](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)」を参照してください。  
  
## 参照  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [コレクション型依存関係プロパティ](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)   
 [依存関係プロパティのセキュリティ](../../../../docs/framework/wpf/advanced/dependency-property-security.md)   
 [XAML 読み込みと依存関係プロパティ](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)   
 [DependencyObject の安全なコンストラクター パターン](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)