---
title: "WPF XAML 名前スコープ | Microsoft Docs"
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
  - "API, 名前関連"
  - "クラス, FrameworkContentElement"
  - "クラス, FrameworkElement"
  - "クラス, RegisterName"
  - "FrameworkContentElement クラス"
  - "FrameworkElement クラス"
  - "名前関連 API"
  - "名前スコープ"
  - "RegisterName クラス"
  - "スタイル, 名前スコープ"
  - "テンプレート, 名前スコープ"
  - "XAML, 名前スコープ"
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# WPF XAML 名前スコープ
XAML 名前スコープは、XAML で定義されるオブジェクトを識別する概念です。  XAML 名前スコープの名前を使用すると、XAML で定義されたオブジェクトの名前とそれに対応するインスタンスとの関係をオブジェクト ツリーとして確立できます。  通常、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] マネージ コードの XAML 名前スコープは、XAML アプリケーションの個々の XAML ページ ルートの読み込み時に作成されます。  プログラミング オブジェクトとしての XAML 名前スコープは、<xref:System.Windows.Markup.INameScope> インターフェイスによって定義され、実際的な <xref:System.Windows.NameScope> クラスによって実装されます。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## 読み込まれた XAML アプリケーションにおける名前スコープ  
 広義のプログラミングまたはコンピューター サイエンスのコンテキストでは、プログラミングの概念に、オブジェクトへのアクセスに使用できる一意の識別子または名前の原則が含まれる場合がよくあります。  識別子または名前を使用するシステムの場合、名前スコープによって、その名前のオブジェクトが要求されたときにプロセスまたは技法で検索する境界、または識別名の一意性を適用する境界が定義されます。  XAML 名前スコープには、これらの一般原則が当てはまります。  WPF では、XAML 名前スコープは、XAML ページを読み込むときに、そのルート要素上に作成されます。  XAML ページ内で指定した名前は、それぞれ関連する XAML 名前スコープに追加されます。名前はページ ルートから始まります。  
  
 WPF XAML では、共通ルート要素である要素 \(<xref:System.Windows.Controls.Page> や <xref:System.Windows.Window> など\) が XAML 名前スコープを常に制御します。  マークアップのページのルート要素が <xref:System.Windows.FrameworkElement> や <xref:System.Windows.FrameworkContentElement> などの要素である場合は、有効な XAML 名前スコープを <xref:System.Windows.Controls.Page> が提供できるように、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサによって <xref:System.Windows.Controls.Page> ルートが暗黙的に追加されます。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップ内の要素に `Name` 属性または `x:Name` 属性が定義されていない場合でも、WPF ビルド アクションによって XAML 稼働環境の XAML 名前スコープが作成されます。  
  
 1 つの XAML 名前スコープ内で同じ名前を 2 回使用しようとすると、例外が発生します。  分離コードを持ち、コンパイル済みアプリケーションの一部である WPF XAML の場合、この例外は、WPF ビルド アクションによるビルド時、最初のマークアップ コンパイル中にページに対する生成クラスが作成されるときに発生します。  どのビルド アクションによってもマークアップ コンパイルされない XAML では、XAML の読み込み時に XAML 名前スコープの問題に関連する例外が発生することがあります。  XAML デザイナーがデザイン時に XAML 名前スコープの問題を予測できる場合もあります。  
  
### ランタイム オブジェクト ツリーへのオブジェクトの追加  
 XAML が解析されるのは、WPF XAML 名前スコープが作成され、定義される時点です。  XAML が解析されてオブジェクト ツリーが生成された後、そのオブジェクト ツリーにオブジェクトを追加しても、新しいオブジェクトの `Name` または `x:Name` の値によって XAML 名前スコープ内の情報が自動的に更新されることはありません。  XAML の読み込み後にオブジェクトの名前を WPF XAML 名前スコープに追加するには、XAML 名前スコープを定義するオブジェクトの適切な <xref:System.Windows.Markup.INameScope.RegisterName%2A> の実装を呼び出す必要があります。通常、これは XAML ページ ルートです。  名前が登録されていない場合、追加したオブジェクトを <xref:System.Windows.FrameworkElement.FindName%2A> などのメソッドを使用して名前で参照することはできません。また、名前をアニメーションのターゲットとして使用することもできません。  
  
 アプリケーション開発者にとって最も一般的なシナリオでは、<xref:System.Windows.FrameworkElement.RegisterName%2A> を使用して、ページの現在のルート上の XAML 名前スコープに名前を登録します。  <xref:System.Windows.FrameworkElement.RegisterName%2A> は、オブジェクトをアニメーションのターゲットとするストーリーボードにとって重要なシナリオの一部です。  詳細については、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
 XAML 名前スコープを定義するオブジェクト以外のオブジェクトで <xref:System.Windows.FrameworkElement.RegisterName%2A> を呼び出した場合も、XAML 名前スコープを定義するオブジェクトで <xref:System.Windows.FrameworkElement.RegisterName%2A> を呼び出した場合と同様に、名前は呼び出し元のオブジェクトが保持されている XAML 名前スコープに登録されます。  
  
### コードでの XAML 名前スコープ  
 コードで XAML 名前スコープを作成して使用できます。  API および XAML 名前スコープの作成に関連する概念は、純粋なコードを使用する場合でも同じです。これは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の XAML プロセッサが XAML 自体を処理するときにこれらの API と概念を使用するためです。  この概念と API の主な目的は、通常は一部または全体が XAML で定義されるオブジェクト ツリー内で、名前でオブジェクトを検索できるようにすることです。  
  
 XAML の読み込みによるのではなくプログラムで作成されるアプリケーションの場合、XAML 名前スコープをサポートするためには、XAML 名前スコープを定義するオブジェクトが <xref:System.Windows.Markup.INameScope> を実装しているか、<xref:System.Windows.FrameworkElement> 派生クラスまたは <xref:System.Windows.FrameworkContentElement> 派生クラスである必要があります。  
  
 また、XAML プロセッサによって読み込みおよび処理が行われない要素の場合、既定では、オブジェクトの XAML 名前スコープは作成または初期化されません。  後で名前を登録する予定のオブジェクトに対しては、新しい XAML 名前スコープを明示的に作成する必要があります。  XAML 名前スコープを作成するには、静的な <xref:System.Windows.NameScope.SetNameScope%2A> メソッドを呼び出します。  `dependencyObject` パラメーターとしてそれを所有するオブジェクトを、`value` パラメーターとして新しい <xref:System.Windows.NameScope.%23ctor%2A> コンストラクターの呼び出しを指定します。  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> に対する `dependencyObject` として指定したオブジェクトが、<xref:System.Windows.Markup.INameScope> 実装、<xref:System.Windows.FrameworkElement>、または <xref:System.Windows.FrameworkContentElement> のいずれでもない場合、子要素上で <xref:System.Windows.FrameworkElement.RegisterName%2A> を呼び出しても効果はありません。  新しい XAML 名前スコープを明示的に作成しなかった場合、<xref:System.Windows.FrameworkElement.RegisterName%2A> を呼び出すと例外が発生します。  
  
 XAML 名前スコープ API をコードで使用する例については、「[名前のスコープを定義する](../../../../docs/framework/wpf/graphics-multimedia/how-to-define-a-name-scope.md)」を参照してください。  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## スタイルとテンプレートにおける XAML 名前スコープ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のスタイルとテンプレートを使用すると、コンテンツを直接再利用および再適用できます。  ただし、スタイルとテンプレートには、テンプレート レベルで定義された XAML 名を持つ要素も含まれている可能性があります。  同一のテンプレートが、ページ内で複数回使用される可能性があります。  このため、スタイルとテンプレートでは両方とも、適用先のオブジェクト ツリー内の場所に依存しない独自の XAML 名前スコープを定義します。  
  
 次に例を示します。  
  
 [!code-xml[XamlOvwSupport#NameScopeTemplates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 ここでは、同一のテンプレートを 2 つの異なるボタンに適用しています。  これらのテンプレートがそれぞれ異なる XAML 名前スコープを持っていない場合、テンプレート内で使用されている `TheBorder` という名前により、XAML 名前スコープで名前の競合が発生することになります。  テンプレートの各インスタンスは独自の XAML 名前スコープを持つため、この例の場合、インスタンス化された各テンプレートの XAML 名前スコープに、名前が必ず 1 つずつ含まれます。  
  
 スタイルも独自の XAML 名前スコープを定義します。これは主に、ストーリーボードの各部分に独自の名前が割り当てられるようにするためです。  コントロールのカスタマイズ時にテンプレートを再定義した場合も、これらの名前によって、名前の要素を対象とするコントロール固有の動作が可能となります。  
  
 XAML 名前スコープが複数存在するため、テンプレート内の指定要素の検索が、ページ内のテンプレートなしの指定要素の検索よりも困難になります。  まず、テンプレートが適用されたコントロールの <xref:System.Windows.Controls.Control.Template%2A> プロパティ値を取得して、適用されたテンプレートを判断する必要があります。  その後、テンプレート バージョンの <xref:System.Windows.FrameworkTemplate.FindName%2A> を呼び出し、テンプレートが適用されたコントロールを 2 番目のパラメーターとして渡します。  
  
 コントロールの作成者が生成している規則で、適用されたテンプレートの特定の指定要素を、コントロール自体によって定義される動作の対象とする場合は、コントロール実装コードから <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> メソッドを使用できます。  <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> メソッドはプロテクトされているため、コントロールの作成者のみがアクセスできます。  
  
 テンプレート内での作業中に、テンプレートが適用される XAML 名前スコープを取得する必要がある場合は、<xref:System.Windows.FrameworkElement.TemplatedParent%2A> の値を取得した後、そこで <xref:System.Windows.FrameworkElement.FindName%2A> を呼び出します。  テンプレート内で作業するのは、たとえば、適用したテンプレート内の要素からイベントを発生させるようなイベント ハンドラーを記述する場合です。  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## XAML 名前スコープと名前関連 API  
 <xref:System.Windows.FrameworkElement> には、<xref:System.Windows.FrameworkElement.FindName%2A>、<xref:System.Windows.FrameworkElement.RegisterName%2A>、<xref:System.Windows.FrameworkElement.UnregisterName%2A> の各メソッドがあります。  これらのメソッドを呼び出すオブジェクトが XAML 名前スコープを所有している場合、そのメソッドは関連する XAML 名前スコープのメソッドを呼び出します。  それ以外の場合、親要素が XAML 名前スコープを所有しているかどうかが調べられ、XAML 名前スコープが見つかるまでこの処理が再帰的に続行されます \(XAML プロセッサの動作により、ルートには必ず XAML 名前スコープが存在します\)。  <xref:System.Windows.FrameworkContentElement> での動作もこれに類似していますが、いずれの <xref:System.Windows.FrameworkContentElement> も XAML 名前スコープを所有しない点だけが異なります。  <xref:System.Windows.FrameworkContentElement> にもそれらのメソッドが存在するため、呼び出しは、最終的に <xref:System.Windows.FrameworkElement> 親要素まで転送されることができます。  
  
 新しい XAML 名前スコープを既存のオブジェクトに割り当てるには、<xref:System.Windows.NameScope.SetNameScope%2A> を使用します。  XAML 名前スコープをリセットしたり消去したりするために <xref:System.Windows.NameScope.SetNameScope%2A> を複数回呼び出すこともできますが、一般的な使用方法ではありません。  また、通常、<xref:System.Windows.NameScope.GetNameScope%2A> をコードから使用することはありません。  
  
### XAML 名前スコープの実装  
 次のクラスは、<xref:System.Windows.Markup.INameScope> を直接実装します。  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> はディクショナリの実装であるため、XAML 名または名前スコープの代わりにキーを使用します。  <xref:System.Windows.ResourceDictionary> で <xref:System.Windows.Markup.INameScope> を実装する唯一の理由は、ユーザー コードに対して例外を発生可能にして、本当の XAML 名前スコープと <xref:System.Windows.ResourceDictionary> によるキーの処理方法との違いを明確にしたり、XAML 名前スコープが特に親要素によって <xref:System.Windows.ResourceDictionary> に適用されないようにしたりできるためです。  
  
 <xref:System.Windows.FrameworkTemplate> および <xref:System.Windows.Style> は、明示的なインターフェイス定義を通じて <xref:System.Windows.Markup.INameScope> を実装します。  明示的に実装すると、<xref:System.Windows.Markup.INameScope> インターフェイスからこれらの XAML 名前スコープにアクセスした場合に、それらが従来どおりに動作します。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内部プロセスは、このアクセス方法を使用して XAML 名前スコープと通信します。  しかし、明示的なインターフェイス定義は、<xref:System.Windows.FrameworkTemplate> と <xref:System.Windows.Style> の通常の API サーフェイスには含まれません。これは、<xref:System.Windows.FrameworkTemplate> や <xref:System.Windows.Style> では、<xref:System.Windows.Markup.INameScope> のメソッドを直接呼び出す必要がほとんどなく、代わりに <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> などの他の API を使用するためです。  
  
 次のクラスは、<xref:System.Windows.NameScope?displayProperty=fullName> ヘルパー クラスを使用し、<xref:System.Windows.NameScope.NameScope%2A?displayProperty=fullName> 添付プロパティからその XAML 名前スコープ実装に接続することにより、独自の XAML 名前スコープを定義します。  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## 参照  
 [XAML 名前空間および WPF XAML の名前空間の割り当て](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)   
 [x:Name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)