---
title: "プロパティ変更イベント | Microsoft Docs"
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
  - "変更イベント [WPF], プロパティ"
  - "作成 (プロパティ トリガーを) [WPF]"
  - "依存関係プロパティ [WPF], 変更イベント"
  - "イベント [WPF], プロパティ値の変更"
  - "識別 (プロパティ変更イベントを) [WPF]"
  - "プロパティ変更イベント [WPF]"
  - "プロパティ変更イベント [WPF], 型"
  - "プロパティ トリガー [WPF]"
  - "プロパティ トリガー [WPF], 定義"
  - "プロパティ値の変更 [WPF]"
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# プロパティ変更イベント
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、プロパティ値の変更に応答して発生するさまざまなイベントが定義されています。  通常、プロパティは[依存関係プロパティ](GTMT)です。  イベント自体は、[ルーティング イベント](GTMT)のこともあれば、標準の [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] イベントのこともあります。  要素ツリーを通じて適切にルーティングされるプロパティ変更もあれば、プロパティが変更されたオブジェクトにのみ関係するプロパティ変更もあるため、イベントの定義は状況によって異なります。  
  
## プロパティ変更イベントの識別  
 シグニチャ パターンまたは名前付けパターンに基づいてプロパティ変更を報告するすべてのイベントが、プロパティ変更イベントとして明示的に識別されるわけではありません。  通常、[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] ドキュメント内のイベントの説明では、イベントがプロパティ値の変更に直接結び付くものであるかどうかが示されており、プロパティとイベントのクロス リファレンスが提供されます。  
  
### RoutedPropertyChanged イベント  
 特定のイベントでは、プロパティ変更イベントで明示的に使用されるイベント データ型とデリゲートを使用します。  イベント データ型は <xref:System.Windows.RoutedPropertyChangedEventArgs%601> であり、デリゲートは <xref:System.Windows.RoutedPropertyChangedEventHandler%601> です。  イベント データもデリゲートも、ジェネリック型パラメーターを使用します。これは、ハンドラーを定義するときに、変更するプロパティの実際の型を指定するために使用されるものです。  イベント データは <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> および <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A> という 2 つのプロパティを持ち、これらはイベント データ内で型引数として渡されます。  
  
 名前の "Routed" 部分は、プロパティ変更イベントがルーティング イベントして登録されることを示しています。  プロパティ変更イベントのルーティングには、子要素 \(コントロールの複合部分\) のプロパティが値を変更した場合に、コントロールのトップレベルがプロパティ変更イベントを受信できるというメリットがあります。  たとえば、<xref:System.Windows.Controls.Slider> など、<xref:System.Windows.Controls.Primitives.RangeBase> コントロールが組み込まれたコントロールを作成するとします。  スライダー部分で <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> プロパティの値が変わった場合、その部分ではなく親コントロールでその変更を処理する必要がある場合があります。  
  
 古い値と新しい値があるため、このイベント ハンドラーがプロパティ値の検証コントロールとして使用される可能性があります。  しかし、プロパティ変更イベントの多くは、このような目的で設計されているわけではありません。  通常、値の提供は、他のロジックのコードでその値を処理するために行われます。しかし、イベント ハンドラー内から値を実際に変更することはお勧めできません。また、ハンドラーの実装方法によっては、意図しない再帰が生じることもあります。  
  
 プロパティがカスタム依存関係プロパティの場合、または、インスタンス化コードを定義した派生クラスで操作している場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムには、プロパティ変更を追跡する優れたメカニズムが組み込まれています。それは、<xref:System.Windows.CoerceValueCallback> および <xref:System.Windows.PropertyChangedCallback> というプロパティ システム コールバックです。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムを使用して検証および強制型変換を行う方法の詳細については、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」および「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
### DependencyPropertyChanged イベント  
 プロパティ変更イベントのシナリオには、<xref:System.Windows.DependencyPropertyChangedEventArgs> と <xref:System.Windows.DependencyPropertyChangedEventHandler> のペアも含まれます。  これらのプロパティ変更のイベントはルーティングされません。これらは、標準の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントです。  <xref:System.Windows.DependencyPropertyChangedEventArgs> は、<xref:System.EventArgs> から派生したものではなく、特殊なイベント データ レポート型です。<xref:System.Windows.DependencyPropertyChangedEventArgs> は構造体であり、クラスではありません。  
  
 <xref:System.Windows.DependencyPropertyChangedEventArgs> と <xref:System.Windows.DependencyPropertyChangedEventHandler> を使用するイベントは、`RoutedPropertyChanged` イベントより多少一般的です。  <xref:System.Windows.UIElement.IsMouseCapturedChanged> は、これらの種類を使用するイベントの例です。  
  
 <xref:System.Windows.RoutedPropertyChangedEventArgs%601> と同様、<xref:System.Windows.DependencyPropertyChangedEventArgs> も、プロパティの古い値と新しい値を報告します。  そのため、値を使用して行う操作に関して同じ注意が当てはまります。イベントに応答して送信元で値を変更することは、一般的にはお勧めできません。  
  
## プロパティ トリガー  
 プロパティ変更イベントに密接に関係する概念がプロパティ トリガーです。  プロパティ トリガーはスタイルまたはテンプレート内に作成され、プロパティ トリガーが割り当てられるプロパティの値に基づく条件付きの動作を作成できます。  
  
 プロパティ トリガーのプロパティは、依存関係プロパティです。  これは \(多くの場合\) 読み取り専用の依存関係プロパティです。  コントロールによって公開される依存関係プロパティが、プロパティ トリガーになるように少なくとも部分的に設計されている場合の良い指標が、プロパティ名の先頭が "Is" がどうかということです。  この名前付けがされたプロパティは、多くの場合、読み取り専用のブール型の依存関係プロパティです。このプロパティの主要なシナリオは、リアルタイム UI に影響を及ぼす可能性があるためにプロパティ トリガーの候補である、レポート コントロール ステートです。  
  
 これらのプロパティの一部は、専用のプロパティ変更イベントも持ちます。  たとえば、プロパティ <xref:System.Windows.UIElement.IsMouseCaptured%2A> は、プロパティ変更イベント <xref:System.Windows.UIElement.IsMouseCapturedChanged> を持ちます。  プロパティ自体は読み取り専用であり、その値は入力システムによって調整され、入力システムがリアルタイムの変更のたびに <xref:System.Windows.UIElement.IsMouseCapturedChanged> を発生します。  
  
 プロパティ トリガーを使用してプロパティの変更に対処する場合は、本当のプロパティ変更イベントに比べ、いくつかの制限があります。  
  
 プロパティ トリガーは、完全一致ロジックを通じて動作します。  プロパティと、トリガーが処理する特定の値を示す値を指定します。  次に例を示します。`<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>` この制限のため、ほとんどのプロパティ トリガーの使用は、ブール型のプロパティか、有効な値の範囲が管理可能で、各ケースに対してトリガーを定義できる専用の列挙値を使用するプロパティが対象です。  または、プロパティ トリガーは、項目のカウントがゼロに達した場合など、特別な値に対してのみ存在する可能性があります。プロパティ値がゼロから再び変更するケースに対処するトリガーはありません \(すべてのケースに対応するトリガーではなく、コード イベント ハンドラー、または、値がゼロ以外のときにトリガー状態を再び元に戻す既定の動作が必要です\)。  
  
 プロパティ トリガーの構文は、プログラミングの "if" ステートメントに似ています。  トリガー条件が true の場合、プロパティ トリガーの "本体" が "実行" されます。  プロパティ トリガーの "本体" はコードではなく、マークアップです。  そのマークアップは、1 つ以上の <xref:System.Windows.Setter> 要素を使用して、スタイルやテンプレートが適用されているオブジェクトの他のプロパティを設定するように制限されています。  
  
 さまざまな有効値から成るプロパティ トリガーの "if" 条件をオフセットするには、一般には、<xref:System.Windows.Setter> を使用して同じプロパティ値を既定値に設定することをお勧めします。  こうすることで、トリガー条件が true の場合は、<xref:System.Windows.Trigger> が含む setter が優先され、トリガー条件が false の場合は、<xref:System.Windows.Trigger> 内にない <xref:System.Windows.Setter> が優先されます。  
  
 プロパティ トリガーは、通常、1 つ以上の外観プロパティが、同じ要素の別のプロパティの状態に基づいて変更されるシナリオに適しています。  
  
 プロパティ トリガーの詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
## 参照  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)