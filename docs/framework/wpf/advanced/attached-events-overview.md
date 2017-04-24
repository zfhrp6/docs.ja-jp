---
title: "添付イベントの概要 | Microsoft Docs"
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
  - "添付イベント [WPF], 定義"
  - "添付イベント [WPF], シナリオ"
  - "添付イベントとルーティング イベント [WPF]"
  - "サポート (添付イベントをルーティング イベントで) [WPF]"
  - "定義 (添付イベントをルーティング イベントとして) [WPF]"
  - "処理 (添付イベントを) [WPF]"
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 添付イベントの概要
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] は、言語コンポーネントと、*添付イベント*と呼ばれる種類のイベントも定義します。  添付イベントの概念によって、特定のイベントのハンドラーを、実際にそのイベントを定義または継承する要素ではなく任意の要素に追加することができます。  この場合、イベントを発生させる可能性のあるオブジェクトでも、インスタンスを処理する添付先でも、そのイベントを定義したり "所有" したりしません。  
  
   
  
<a name="prerequisites"></a>   
## 必要条件  
 このトピックは、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」および「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」を既に通読していることを前提としています。  
  
<a name="Syntax"></a>   
## 添付イベントの構文  
 添付イベントには [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 構文を使用します。また、添付イベントの使用に対応できるように、関連するコードでは特定のコーディング パターンを使用する必要があります。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 構文では、添付イベントはイベント名だけでなく、所有している型とイベント名をドット \(.\) で区切って指定します。  イベント名にそれが所有する型が付加されるため、添付イベントの構文では、インスタンス化できる任意の要素に添付イベントをアタッチすることができます。  
  
 たとえば、ハンドラーをカスタムの `NeedsCleaning` 添付イベントにアタッチする [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 構文の例を次に示します。  
  
 [!code-xml[WPFAquariumSln#AE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 `aqua:` プレフィクスがあることに注意してください。この例の添付イベントは独自にマップされた xmlns によるカスタム イベントであるため、このプレフィクスが必要です。  
  
<a name="WPFImplements"></a>   
## WPF の添付イベント実装方法  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、添付イベントは <xref:System.Windows.RoutedEvent> フィールドによってサポートされ、発生後はツリーを通じてルーティングされます。  通常、添付イベントの発生元 \(イベントを発生させたオブジェクト\) はシステムまたはサービスのオブジェクトです。したがって、イベントを発生させるコードを実行するオブジェクトは要素ツリーの直接の構成部分ではありません。  
  
<a name="Scenarios"></a>   
## 添付イベントのシナリオ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で添付イベントがよく使用されるのは、サービス レベルでの抽象化が含まれる機能で、これは静的 <xref:System.Windows.Input.Mouse> クラスまたは <xref:System.Windows.Controls.Validation> クラスによって有効にされるイベントなどのためです。  サービスと対話したりサービスを使用したりするクラスでは、イベントを添付イベント構文で使用するか、添付イベントをルーティング イベントとしてクラスによるサービス機能統合の一部とすることができます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には多くの添付イベントが定義されていますが、添付イベントを直接使用または処理するシナリオは限られます。  一般に添付イベントは、アーキテクチャ上の目的を満たしてから、非添付の \([!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベント "ラッパー" によってサポートされる\) ルーティング イベントに転送されます。  
  
 たとえば、基になる添付イベント <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=fullName> を特定の <xref:System.Windows.UIElement> でより簡単に処理するには、添付イベント構文を [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] またはコードで使用するのではなく、その <xref:System.Windows.UIElement> で <xref:System.Windows.UIElement.MouseDown> を使用します。  添付イベントは、入力デバイスを将来的に拡張することを可能にすることから、アーキテクチャ上の目的を満たします。  この架空のデバイスは、マウスからの入力をシミュレートする目的で <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=fullName> を発生させるためだけに必要であり、それを行うために <xref:System.Windows.Input.Mouse> から派生する必要はありません。  ただし、このシナリオでは、イベントを処理するコードが必要であり、添付イベントを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で処理することは不適切です。  
  
<a name="Handling"></a>   
## WPF の添付イベント処理  
 添付イベントを処理するプロセスと作成するハンドラー コードは、基本的にはルーティング イベントの場合と同じです。  
  
 一般に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の添付イベントは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のルーティング イベントと大差ありません。  違いは、イベントが発生する場所とクラスからメンバーとして公開される方法 \(これは [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ハンドラー構文にも影響する\) です。  
  
 ただし、既に触れたとおり、既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 添付イベントは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で処理されることを特に意図していません。  多くの場合、イベントの目的は、複合要素から複合の親要素に状態を報告できるようにすることです。このとき、一般にイベントはコードで発生し、関連する親クラスのクラス処理にも依存します。  たとえば、<xref:System.Windows.Controls.Primitives.Selector> 内の項目は添付 <xref:System.Windows.Controls.Primitives.Selector.Selected> イベントを生成すると見なされます。このイベントは <xref:System.Windows.Controls.Primitives.Selector> クラスによってクラス処理されてから、おそらくは <xref:System.Windows.Controls.Primitives.Selector> クラスによって別のルーティング イベント <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> に変換されます。  ルーティング イベントとクラス処理の詳細については、「[ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)」を参照してください。  
  
<a name="Custom"></a>   
## 独自の添付イベントをルーティング イベントとして定義する  
 共通の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 基本クラスから派生する場合、特定のパターンのメソッドをクラスに含め、基本クラスに既に提供されているユーティリティ メソッドを使用することにより、独自の添付イベントを実装することができます。  
  
 パターンは次のとおりです。  
  
-   2 つのパラメーターを指定した `Add*Handler` メソッド。  1 番目のパラメーターにはイベントを識別する情報を指定します。イベントの名前は、メソッド名の "\*" 部分に一致する必要があります。  2 番目のパラメーターは、追加するハンドラーです。  メソッドは、戻り値のないパブリックで静的なメソッドである必要があります。  
  
-   2 つのパラメーターを指定した `Remove*Handler` メソッド。  1 番目のパラメーターにはイベントを識別する情報を指定します。イベントの名前は、メソッド名の "\*" 部分に一致する必要があります。  2 番目のパラメーターは、削除するハンドラーです。  メソッドは、戻り値のないパブリックで静的なメソッドである必要があります。  
  
 `Add*Handler` アクセサー メソッドは、添付イベント ハンドラーの属性が要素で宣言されているときに [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の処理を手助けします。  `Add*Handler` メソッドと `Remove*Handler` メソッドも、添付イベントのイベント ハンドラー ストアにアクセスする手段となります。  
  
 この一般的なパターンは、まだフレームワークとして実装するほど厳密なものではありません。というのも、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リーダー実装では、基になるイベントを識別するためにサポート言語とアーキテクチャによって異なる方式が使用される場合があるためです。  これは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が添付イベントをルーティング イベントとして実装する理由の 1 つです。イベント \(<xref:System.Windows.RoutedEvent>\) に使用する識別子は、既に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベント システムに定義されています。  また、ルーティング イベントは、添付イベントの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 言語レベルの概念においては実装の自然な拡張です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 添付イベントの `Add*Handler` 実装は、ルーティング イベントとハンドラーを引数として指定する <xref:System.Windows.UIElement.AddHandler%2A> 呼び出しで構成されます。  
  
 この実装方式とルーティング イベント システム全般では、添付イベントを処理できるのは <xref:System.Windows.UIElement> 派生クラスまたは <xref:System.Windows.ContentElement> 派生クラスに限定されます。これらのクラスのみが <xref:System.Windows.UIElement.AddHandler%2A> を持つことがその理由です。  
  
 たとえば、次のコードでは、添付イベントをルーティング イベントとして宣言する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 添付イベント方式を使用して、`NeedsCleaning` 添付イベントを所有者クラス `Aquarium` に定義しています。  
  
 [!code-csharp[WPFAquariumSln#AECode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 添付イベントの識別子フィールド <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> を確立するために使用されるメソッドが、非添付ルーティング イベントを登録するために使用されるメソッドと実際には同じことに注意してください。  すべての添付イベントとルーティング イベントは、一元化された内部ストアに登録されます。  このイベント ストアの実装によって、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」で説明されている "インターフェイスとしてのイベント" という概念が実現されます。  
  
<a name="Raising"></a>   
## WPF 添付イベントの発生  
 通常は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に定義された既存の添付イベントをコードから発生させる必要はありません。  これらのイベントは一般的な "サービス" 概念モデルに従い、<xref:System.Windows.Input.InputManager> などのサービス クラスがイベントを発生させる処理を担います。  
  
 ただし、<xref:System.Windows.RoutedEvent> を基にする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の添付イベント モデルに基づいてカスタムの添付イベントを定義する場合は、<xref:System.Windows.UIElement.RaiseEvent%2A> を使用して添付イベントを任意の <xref:System.Windows.UIElement> または <xref:System.Windows.ContentElement> から発生させることができます。  ルーティング イベント \(添付または非添付\) を発生させるには、特定の要素をイベント ソースとして要素ツリー内で宣言する必要があります。このソースが <xref:System.Windows.UIElement.RaiseEvent%2A> 呼び出し元として報告されます。  ツリー内のどの要素が発生元として報告されるかを決定することは、作成するサービスの役目です。  
  
## 参照  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)   
 [WPF における XAML とカスタム クラス](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)