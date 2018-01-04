---
title: "x:Name ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 676f7f696fda26ee9d86d14f06dc7b70e2565157
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xname-directive"></a>x:Name ディレクティブ
XAML 名前スコープ内の XAML で定義された要素を一意に識別します。 XAML 名前スコープとその一意性モデルは、フレームワーク Api を提供または実行時に、XAML で作成されたオブジェクト グラフにアクセスする動作を実装するときに、インスタンス化されたオブジェクトに適用できます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`XAMLNameValue`|制限に準拠している文字列、 [XamlName の文法](../../../docs/framework/xaml-services/xamlname-grammar.md)です。|  
  
## <a name="remarks"></a>コメント  
 後に`x:Name`に適用される、フレームワークは、プログラミング モデルをバックアップの場合、名前がオブジェクト参照またはコンス トラクターによって返されるインスタンスを保持する変数に相当します。  
  
 値、`x:Name`ディレクティブの使用法が XAML 名前スコープ内で一意でなければなりません。 既定で .NET Framework XAML サービス API を使用するときにプライマリの XAML 名前スコープは 1 つの XAML 稼働環境の XAML ルート要素で定義されて、その XAML の運用環境に含まれる要素が含まれます。 追加不連続の XAML 名前スコープ内、1 つの XAML 稼働環境で発生したは、特定のシナリオに対処するフレームワークで定義できます。 たとえば、WPF では、新しい XAML 名前スコープ定義され、XAML の運用環境でも定義されているすべてのテンプレートによって作成されました。 記述された WPF が XAML 名前スコープの多くの概念に関連する) の XAML 名前スコープの詳細については、次を参照してください。 [WPF XAML 名前スコープ](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)です。  
  
 一般に、`x:Name`を使用する場合に適用しない`x:Key`です。 既存の特定のフレームワークによって XAML の実装の間に代替の概念が導入`x:Key`と`x:Name`が、その推奨される方法ではありません。 .NET framework XAML サービスがこのような代替の概念をサポートしていませんなどの名前とキーの情報を処理するときに<xref:System.Windows.Markup.INameScope>または<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>です。  
  
 規則の permittance を`x:Name`と名前の一意性の強制が実装する特定のフレームワークによって定義可能性があります。 ただし、.NET Framework XAML サービスで使用可能な XAML 名前スコープの一意性のフレームワーク定義する必要がありますの定義と一貫性のある<xref:System.Windows.Markup.INameScope>については、このドキュメントの場所に関する規則と同じ規則を使用して、情報が適用されます。 たとえば、[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]実装がさまざまなマークアップ要素を個別に分割<xref:System.Windows.NameScope>範囲は、リソース ディクショナリなど、コンテンツ、ページ レベルの XAML、テンプレート、およびその他の遅延で作成される論理ツリーと XAML を強制これらの XAML 名前スコープのそれぞれの名前の一意性です。  
  
 .NET Framework XAML サービスの XAML オブジェクト ライターを使用するカスタム型のプロパティにマップされる`x:Name`で型を確立または変更できます。 マップするプロパティの名前を参照することでこの動作を定義する、<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>型定義のコードにします。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>型レベルの属性です。  
  
 Using.NET Framework XAML サービスの XAML 名前スコープのサポートのバッキング ロジックはフレームワークに依存しない方法で実装することによって、<xref:System.Windows.Markup.INameScope>インターフェイスです。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 標準的なビルド構成の下で、 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML、部分クラス、および分離コードで指定されたを使用するアプリケーション`x:Name`、基になるで作成されたフィールドの名前になりますときにコード[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]、マークアップによって処理されます。コンパイル ビルド タスクであり、そのフィールドは、オブジェクトへの参照を保持します。 既定では、作成されたフィールドは、内部です。 フィールド アクセスを変更するには指定することによって、 [X:fieldmodifier 属性](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)です。 WPF および Silverlight の場合は、シーケンスはことマークアップ コンパイルの定義名部分クラスですが、値のフィールドは、最初は空です。 という名前の生成されたメソッド、`InitializeComponent`クラスのコンス トラクター内から呼び出されます。 `InitializeComponent`成る`FindName`のそれぞれを使用してを呼び出す、`x:Name`部分クラスとしての XAML で定義された部分に存在する値が文字列を入力します。 戻り値は、解析 XAML から作成されたオブジェクトを持つフィールドの値を入力する、同じ名前のフィールド参照に割り当てられます。 実行`InitializeComponent`ランタイム オブジェクト グラフを使用して、参照できるように、`x:Name`フィールド名を直接呼び出すのではなく/`FindName`いつでも明示的にする必要があります、XAML で定義されたオブジェクトへの参照。  
  
 使用する WPF アプリケーションの[!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]を対象し、XAML ファイルが含まれます`Page`ビルド アクション、個別の参照プロパティが追加のコンパイル時に作成された、`WithEvents`キーワードを持つすべての要素を`x:Name`サポート`Handles`イベント ハンドラー デリゲートの構文。 このプロパティはパブリックでは常にします。 詳細については、「[Visual Basic と WPF のイベント処理](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)」を参照してください。  
  
 `x:Name`ページがない場合 (たとえば、loose XAML、リソース ディクショナリの) のビルド アクションによって、マークアップ コンパイルであっても、読み込み時に XAML 名前スコープに名前を登録する WPF XAML プロセッサによって使用されます。 この動作の 1 つの理由があるため、`x:Name`のために必要な可能性のある<xref:System.Windows.Data.Binding.ElementName%2A>バインドします。 詳細については、「[データ バインディングの概要](../../../docs/framework/wpf/data/data-binding-overview.md)です。  
  
 前に述べたよう`x:Name`(または`Name`) を使用する場合に適用しない`x:Key`です。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> XAML 名前スコープとして定義すること自体が実装されていませんかに null 値を返す、特別な動作を持つ<xref:System.Windows.Markup.INameScope>この動作を適用する方法として Api です。 WPF XAML パーサーが検出した場合`Name`または`x:Name`で XAML で定義された<xref:System.Windows.ResourceDictionary>名前は任意の XAML 名前スコープに追加されません。 XAML 名前スコープから名前を検索するには、`FindName`メソッドでは、有効な結果が返されません。  
  
### <a name="xname-and-name"></a>x: 名前と名前  
 WPF アプリケーションの多くのシナリオで使用されるすべてを回避できます、`x:Name`属性があるため、`Name`としての依存関係プロパティの既定の XAML 名前空間などの指定されたいくつか重要な基本クラスの<xref:System.Windows.FrameworkElement>と<xref:System.Windows.FrameworkContentElement>この目的を満たします。 一般的な XAML と WPF のシナリオは引き続きコードのない要素へのアクセスの場所`Name`フレームワーク レベルのプロパティは、重要です。 たとえば、特定アニメーションとストーリー ボードのサポート クラスをサポートしていない、`Name`プロパティがアニメーションを制御するためにコードで参照する必要があります。 指定する必要があります`x:Name`タイムラインと後でコードからそれらを参照する場合、XAML で作成される変換の属性として。  
  
 場合<xref:System.Windows.FrameworkElement.Name%2A>は、クラスのプロパティとして利用できる<xref:System.Windows.FrameworkElement.Name%2A>と`x:Name`属性として同じ意味で使用できますが、両方を同じ要素に対して指定した場合に解析例外が発生します。 XAML マークアップ コンパイルされる場合は、それ以外の場合の負荷が発生した例外がマークアップ コンパイル時に発生します。  
  
 <xref:System.Windows.FrameworkElement.Name%2A>XAML 属性の構文を使用して設定できますとコードを使用して<xref:System.Windows.DependencyObject.SetValue%2A>ですただしその設定、<xref:System.Windows.FrameworkElement.Name%2A>コード内のプロパティは、XAML が既にほとんどの状況で XAML 名前スコープ内で代表的なフィールドの参照を作成できません。読み込まれます。 設定しようとしてではなく<xref:System.Windows.FrameworkElement.Name%2A>コードでは、次のように使用します。<xref:System.Windows.NameScope>適切なスコープに対して、コードからメソッドです。  
  
 <xref:System.Windows.FrameworkElement.Name%2A>内部テキ ストにプロパティ要素構文を使用して設定することもできますが、一般的なことはありません。 これに対し、 `x:Name` XAML プロパティ要素構文でまたはを使用してコードに設定することはできません<xref:System.Windows.DependencyObject.SetValue%2A>; のみ設定できますディレクティブであるために、オブジェクトの属性の構文を使用します。  
  
## <a name="silverlight-usage-notes"></a>Silverlight の使用上の注意  
 Silverlight 用の `x:Name` に関しては、別途ドキュメントが用意されています。 詳細については、次を参照してください[XAML Namespace (x:)。言語機能 (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>  
 [WPF のツリー](../../../docs/framework/wpf/advanced/trees-in-wpf.md)
