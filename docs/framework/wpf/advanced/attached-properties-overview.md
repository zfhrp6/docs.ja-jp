---
title: 添付プロパティの概要
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ceba94d80ca66ab228804ffff2a5b8f89a68d7c4
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="attached-properties-overview"></a>添付プロパティの概要
添付プロパティは、XAML によって定義された概念です。 添付プロパティは、任意のオブジェクトに設定可能なグローバル プロパティの型として使用されることを意図しています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では通常、添付プロパティは従来のプロパティ "ラッパー" を含まない依存関係プロパティの特殊な形式として定義されています。  
  
   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティのコンシューマーの観点から依存関係プロパティを理解しており、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を読んでいることを前提としています。 このトピックの例について理解するには、XAML および [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの記述方法について知っておく必要もあります。  
  
<a name="attached_properties_usage"></a>   
## <a name="why-use-attached-properties"></a>添付プロパティを使用する理由  
 添付プロパティの目的の 1 つは、親要素に実際に定義されているプロパティに対する一意の値を、異なる子要素が指定できるようにすることです。 このシナリオの適用例として、子要素から親要素に、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] での表示方法を通知させることがあります。 1 つの例は、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>プロパティです。 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>内に含まれる要素に設定することは想定されているために、プロパティが添付プロパティとして作成、<xref:System.Windows.Controls.DockPanel>ではなく <xref:System.Windows.Controls.DockPanel>自体です。 <xref:System.Windows.Controls.DockPanel>クラス定義、静的な<xref:System.Windows.DependencyProperty>という名前のフィールド<xref:System.Windows.Controls.DockPanel.DockProperty>、し、説明、<xref:System.Windows.Controls.DockPanel.GetDock%2A>と<xref:System.Windows.Controls.DockPanel.SetDock%2A>添付プロパティのパブリック アクセサーとしてメソッドです。  
  
<a name="attached_properties_xaml"></a>   
## <a name="attached-properties-in-xaml"></a>XAML の添付プロパティ  
 XAML では、構文 *AttachedPropertyProvider*.*PropertyName* を使用して添付プロパティを設定します  
  
 設定する方法の例を次に示します<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>XAML で。  
  
 [!code-xaml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]  
  
 使用法と静的なプロパティに類似したことに注意してください。常に、型を参照する<xref:System.Windows.Controls.DockPanel>を所有しているし、添付プロパティを登録する名前で指定された任意のインスタンスを参照するのではなくです。  
  
 さらに、XAML の添付プロパティはマークアップに設定する属性であるため、設定操作にのみ関連性があります。 XAML でプロパティを直接取得することはできませんが、スタイルのトリガー (詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照) などの値を比較するための間接的な機構があります。  
  
### <a name="attached-property-implementation-in-wpf"></a>WPF での添付プロパティの実装  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、UI プレゼンテーションに関連する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 型に存在する添付プロパティの多くが依存関係プロパティとして実装されます。 添付プロパティは XAML の概念であり、依存関係プロパティは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の概念です。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の添付プロパティは依存関係プロパティであるため、プロパティのメタデータ、そしてその既定値といった依存関係プロパティの概念をサポートします。  
  
<a name="howused"></a>   
## <a name="how-attached-properties-are-used-by-the-owning-type"></a>所有する型による添付プロパティの使用方法  
 添付プロパティはどのオブジェクトにも設定できますが、プロパティを設定したことによって自動的に意味のある結果が得られるわけでも、値が別のオブジェクトによって使用されるわけでもありません。 一般に、添付プロパティの目的は、想定されるさまざまなクラス階層または論理関係から生じるオブジェクトが、添付プロパティを定義する型に共通する情報をレポートできるようにすることです。 添付プロパティを定義する型は、一般的に次のいずれかのモデルに従っています。  
  
-   添付プロパティを定義する型が、添付プロパティの値を設定する要素の親要素になるように設計されている。 この型の子オブジェクトは、一部のオブジェクト ツリー構造で内部ロジックを反復し、値を取得して、その値に対する処理を実行します。  
  
-   添付プロパティを定義する型が、想定されるさまざまな親要素およびコンテンツ モデルの子要素として使用される。  
  
-   添付プロパティを定義する型が、サービスを表す。 その他の型は、添付プロパティの値を設定します。 プロパティを設定する要素がサービスのコンテキストで評価されると、添付プロパティの値がサービス クラスの内部ロジックにより取得されます。  
  
### <a name="an-example-of-a-parent-defined-attached-property"></a>親定義の添付プロパティの例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が添付プロパティを定義する最も一般的なシナリオは、親要素が子要素のコレクションをサポートし、さらに動作の詳細が子要素ごとにレポートされるような動作を実装する場合です。  
  
 <xref:System.Windows.Controls.DockPanel> 定義、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>添付プロパティ、および<xref:System.Windows.Controls.DockPanel>、レンダリング ロジックの一部として、クラス レベルのコードを持つ (具体的には、<xref:System.Windows.Controls.DockPanel.MeasureOverride%2A>と<xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>)。 A<xref:System.Windows.Controls.DockPanel>が常にインスタンスを確認するかどうかの値を設定その直接の子要素が<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>です。 設定されている場合は、その値が、その子要素に適用されるレンダリング ロジックの入力になります。 入れ子になった<xref:System.Windows.Controls.DockPanel>各インスタンスは、独自の直接の子要素のコレクションを扱うが実装に固有の動作は方法<xref:System.Windows.Controls.DockPanel>プロセス<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>値。 直接の親以外の要素に影響を与える添付プロパティを所有することは、理論上は可能です。 場合、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>を持たない要素で添付プロパティを設定<xref:System.Windows.Controls.DockPanel>が、エラーなし、または例外に対して操作を実行する親要素が発生します。 単につまり、グローバル プロパティの値が設定されたが、現在を持たない<xref:System.Windows.Controls.DockPanel>情報を利用できる親。  
  
<a name="attached_properties_code"></a>   
## <a name="attached-properties-in-code"></a>コードの添付プロパティ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の添付プロパティには、取得/設定アクセスを簡単にする、一般的な [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] の "ラッパー" メソッドが含まれていません。 これは、添付プロパティが、プロパティが設定されているインスタンスの [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 名前空間の一部とは限らないためです。 ただし、XAML の解析時に XAML プロセッサがその値を設定できる必要があります。 有効な添付プロパティの使用をサポートするには、添付プロパティの所有者の種類ごとに `Get`*PropertyName* および `Set`*PropertyName* の形式で専用のアクセサー メソッドを実装する必要があります。 この専用のアクセサー メソッドは、コード内の添付プロパティの取得/設定でも役立ちます。 コードの観点では、添付プロパティはプロパティ アクセサーではなくメソッド アクセサーを含むバッキング フィールドに似ており、そのバッキング フィールドは特に定義することなくすべてのオブジェクトに存在することができます。  
  
 次の例は、コードに添付プロパティを設定する方法を示しています。 この例では`myCheckBox`のインスタンス、<xref:System.Windows.Controls.CheckBox>クラスです。  
  
 [!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
 [!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]  
  
 同様に XAML 場合は、`myCheckBox`の子要素として既に追加されていなかった`myDockPanel`によってコードの 3 行目は、コードの 4 行目は例外を発生させないが、プロパティの値がないとの対話、<xref:System.Windows.Controls.DockPanel>親およびこのインターフェイス機能しません。 のみ、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>値のセットの存在と組み合わせて、子要素で、<xref:System.Windows.Controls.DockPanel>親要素には、レンダリングされたアプリケーションで効果的な動作が発生します。 (この場合、添付プロパティを設定してからツリーに接続するか、 ツリーに接続してから添付プロパティを設定することができます。 どちらの操作でも、結果は同じです。)  
  
<a name="attached_properties_metadata"></a>   
## <a name="attached-property-metadata"></a>添付プロパティのメタデータ  
 プロパティを登録するときに<xref:System.Windows.FrameworkPropertyMetadata>プロパティがレンダリングや測定に影響を与えるかどうかなどのプロパティの特性を指定する設定。 添付プロパティのメタデータは、一般的に依存関係プロパティとの違いがありません。 オーバーライドの既定値を添付プロパティのメタデータに指定すると、その値がオーバーライドするクラスのインスタンスの暗黙的な添付プロパティの既定値になります。 具体的には、一部のプロセスが添付プロパティの `Get` メソッド アクセサーを使用してそのプロパティの値のクエリを行った場合に、メタデータを指定したクラスのインスタンスが指定されており、その添付プロパティの値が設定されていないと、既定値がレポートされます。  
  
 プロパティでプロパティ値の継承を有効にする場合は、未接続の依存関係プロパティではなく添付プロパティを使用する必要があります。 詳細については、「[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)」を参照してください。  
  
<a name="custom"></a>   
## <a name="custom-attached-properties"></a>カスタム添付プロパティ  
  
<a name="create_attached_properties"></a>   
### <a name="when-to-create-an-attached-property"></a>添付プロパティを作成するタイミング  
 添付プロパティは、定義クラスではないクラスで使用できるプロパティ設定機構を用意する理由がある場合に作成できます。 この最も一般的なシナリオが、レイアウトです。 既存のレイアウト プロパティの例としては<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>、および<xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>です。 これによって実現するシナリオは、レイアウト制御要素の子要素として存在する要素が、レイアウト親要素に対して個別にレイアウト要件を表現するというものです。親が添付プロパティとして定義したプロパティ値を、個々の子要素が設定します。  
  
 クラスがサービスを表しており、クラスでサービスをより透過的に統合できるようにしたい場合にも、添付プロパティを使用します。  
  
 ただし、このシナリオでは、**プロパティ** ウィンドウの編集などの、[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] サポートを受け取ります。 詳しくは、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
 前述のように、プロパティ値の継承を使用する場合には、添付プロパティを登録する必要があります。  
  
<a name="how_do_i_create_attached_properties"></a>   
### <a name="how-to-create-an-attached-property"></a>添付プロパティの作成方法  
 クラスが他の種類で使用するためにのみ添付プロパティを定義するかどうかは、クラスがから派生する必要はありません<xref:System.Windows.DependencyObject>です。 派生する必要は<xref:System.Windows.DependencyObject>全体に従う場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]添付プロパティのモデルは、依存関係プロパティもあります。  
  
 依存関係プロパティとして宣言することにより、添付プロパティを定義、 `public` `static` `readonly`型のフィールド<xref:System.Windows.DependencyProperty>です。 戻り値を使用して、このフィールドを定義する、<xref:System.Windows.DependencyProperty.RegisterAttached%2A>メソッドです。 識別フィールドとそれが表すプロパティの名前付けに関して確立されている [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のパターンに従うには、`Property` の文字列が付加され、フィールド名が添付プロパティ名と一致している必要があります。 添付プロパティのプロバイダーは、添付プロパティのアクセサーとして `Get`*PropertyName* および `Set`*PropertyName* の静的メソッドを指定する必要があります。これを行わないと、プロパティ システムが添付プロパティを使用できません。  
  
> [!NOTE]
>  添付プロパティの get アクセサーを省略すると、データ バインディング プロパティでは Visual Studio や Expression Blend などのデザイン ツールでは機能しません。  
  
#### <a name="the-get-accessor"></a>Get アクセサー  
 `Get`*PropertyName* アクセサーのシグネチャは次の形式にする必要があります。  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` オブジェクトは、実装のより具体的な型として指定することができます。 たとえば、<xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType>メソッド型パラメーターとして<xref:System.Windows.UIElement>添付プロパティに設定する目的のみであるため、<xref:System.Windows.UIElement>インスタンス。  
  
-   戻り値は、実装のより具体的な型として指定することができます。 たとえば、<xref:System.Windows.Controls.DockPanel.GetDock%2A>メソッドの型として<xref:System.Windows.Controls.Dock>値は、その列挙体にのみ設定できます。  
  
#### <a name="the-set-accessor"></a>Set アクセサー  
 `Set`*PropertyName* アクセサーのシグネチャは次の形式にする必要があります。  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target` オブジェクトは、実装のより具体的な型として指定することができます。 たとえば、<xref:System.Windows.Controls.DockPanel.SetDock%2A>メソッドの型として<xref:System.Windows.UIElement>添付プロパティに設定する目的のみであるため、<xref:System.Windows.UIElement>インスタンス。  
  
-   `value` オブジェクトは、実装のより具体的な型として指定することができます。 たとえば、<xref:System.Windows.Controls.DockPanel.SetDock%2A>メソッドの型として<xref:System.Windows.Controls.Dock>値は、その列挙体にのみ設定できます。 このメソッドの値は、マークアップの添付プロパティの使用で添付プロパティが検出されたときに XAML ローダーから生じる入力であることに注意してください。 この入力はマークアップの XAML 属性値として指定された値です。 したがって、適切な型を属性値 (最終的には単なる文字列) から作成できるように、使用する型の型変換、値シリアライザー、またはマークアップ拡張サポートが必要です。  
  
 次の例では、依存関係プロパティの登録 (を使用して、<xref:System.Windows.DependencyProperty.RegisterAttached%2A>メソッド)、だけでなく`Get` *PropertyName*と`Set` *PropertyName*アクセサー. この例では、添付プロパティ名は `IsBubbleSource` です。 したがって、アクセサーの名前は `GetIsBubbleSource` および `SetIsBubbleSource` である必要があります。  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
#### <a name="attached-property-attributes"></a>添付プロパティの属性  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は複数の [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)]を定義します。これは添付プロパティに関する情報をリフレクション プロセス、リフレクションおよびプロパティ情報の一般的なユーザー (デザイナーなど) に提供することを目的としています。 添付プロパティに含まれる型は膨大な範囲に及ぶため、デザイナーには XAML を使用する特定のテクノロジの実装に定義されたすべての添付プロパティのグローバル リストがユーザーに表示されないようにするための手段が必要となります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が添付プロパティに対して定義する [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)]を使用すると、指定した添付プロパティのみをプロパティ ウィンドウに表示することができます。 また、この属性をカスタム添付プロパティに適用するという選択肢もあります。 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)]の目的および構文は、次の参照ページに記載されています。  
  
-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>  
  
<a name="more"></a>   
## <a name="learning-more-about-attached-properties"></a>添付プロパティの詳細情報  
  
-   添付プロパティの作成の詳細については、「[方法: 添付プロパティを登録する](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)」を参照してください。  
  
-   依存関係プロパティおよび添付プロパティの高度な使用シナリオについては、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
-   プロパティは添付プロパティとしても依存関係プロパティとしても登録できますが、"ラッパー" 実装は公開したままにすることができます。 この場合、プロパティをその要素に設定することも、XAML の添付プロパティの構文を使用して任意の要素に設定することもできます。 標準と接続の両方の使用状況を適切なシナリオのプロパティの例は<xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.DependencyProperty>  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [方法: 添付プロパティを登録する](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)
