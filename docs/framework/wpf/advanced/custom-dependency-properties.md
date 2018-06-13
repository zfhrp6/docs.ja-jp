---
title: カスタム依存関係プロパティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- implementing [WPF], wrappers
- registering properties [WPF]
- properties [WPF], metadata
- metadata [WPF], for properties
- custom dependency properties [WPF]
- properties [WPF], registering
- wrappers [WPF], implementing
- dependency properties [WPF], custom
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
ms.openlocfilehash: 2623f34418aad7a0b29c52d1310fdc79afced790
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541964"
---
# <a name="custom-dependency-properties"></a>カスタム依存関係プロパティ
このトピックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーション開発者およびコンポーネントの作成者が、カスタム依存関係プロパティを作成したくなる理由を説明し、実装手順にくわえ、プロパティのパフォーマンス、使いやすさ、または多用性を向上させることができるいくつかの実装オプションについて説明します。  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスの既存の依存関係プロパティのコンシューマーの観点から依存関係プロパティを理解しており、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」というトピックを読んでいることを前提としています。 このトピックの例を理解するには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] について理解し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの作成方法に精通している必要があります。  
  
<a name="whatis"></a>   
## <a name="what-is-a-dependency-property"></a>依存関係プロパティとは  
 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティを依存関係プロパティとして実装することで、プロパティでスタイル設定、データ バインド、継承、アニメーション、および既定値のサポートを有効にすることができます。 依存関係プロパティに登録されているプロパティ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティ システムを呼び出して、<xref:System.Windows.DependencyProperty.Register%2A>メソッド (または<xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>) でバックアップされていると、<xref:System.Windows.DependencyProperty>識別子フィールドです。 依存関係プロパティをのみで使用できる<xref:System.Windows.DependencyObject>型が<xref:System.Windows.DependencyObject>で非常に高く、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クラス階層構造のほとんどのクラスで使用できるように[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]依存関係プロパティをサポートできます。 依存関係プロパティと、これらをこの [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] で説明するために使用されている用語と規則の詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
<a name="example_dp"></a>   
## <a name="examples-of-dependency-properties"></a>依存関係プロパティの例  
 実装される依存関係プロパティの例[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クラスに含まれる、<xref:System.Windows.Controls.Control.Background%2A>プロパティ、<xref:System.Windows.FrameworkElement.Width%2A>プロパティ、および<xref:System.Windows.Controls.TextBox.Text%2A>他の多くのプロパティです。 クラスによって公開される各依存関係プロパティが型の対応するパブリックな静的フィールド<xref:System.Windows.DependencyProperty>その同じクラスで公開します。 これが依存関係プロパティの識別子です。 この識別子は規則を使用して命名されます。依存関係プロパティの名前と文字列 `Property` がこれに付加されます。 たとえば、対応する<xref:System.Windows.DependencyProperty>の識別子フィールド、<xref:System.Windows.Controls.Control.Background%2A>プロパティは<xref:System.Windows.Controls.Control.BackgroundProperty>します。 登録されているし、呼び出しなど、依存関係プロパティに関連するその他の操作の識別子は後で使用し、識別子に依存関係プロパティの情報が格納される<xref:System.Windows.DependencyObject.SetValue%2A>です。  
  
 「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」で説明したように、"ラッパー" の実装により、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内のすべての依存関係プロパティ (ほとんどの添付プロパティを除く) も [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティです。 そのため、他の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティで使用するのと同じ方法でラッパーを定義する [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] アクセサーを呼び出すことで、コードから依存関係プロパティを取得または設定できます。 確立された依存関係プロパティのコンシューマーであれば、通常は使用しない、<xref:System.Windows.DependencyObject>メソッド<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>、基になるプロパティ システムへの接続ポイントがあります。 既存の実装ではなく、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]プロパティが既に呼び出さが<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>内で、`get`と`set`識別子のフィールドを適切に使用する、プロパティのラッパーの実装. カスタム依存関係プロパティを自分で実装する場合、同様の方法でラッパーを定義します。  
  
<a name="backing_with_dp"></a>   
## <a name="when-should-you-implement-a-dependency-property"></a>依存関係プロパティを実装すべき状況  
 クラスのプロパティを実装する場合から派生していれば<xref:System.Windows.DependencyObject>を使用してプロパティをバックアップするオプションがある、<xref:System.Windows.DependencyProperty>識別子であるため、依存関係プロパティを作成します。 シナリオのニーズによっては、プロパティを依存関係プロパティにすることが必要ない場合や適切でない場合もあります。 場合によっては、プロパティをプライベート フィールドでバッキングする一般的な手法で十分な場合もあります。 ただし、プロパティで次の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 機能の 1 つ以上をサポートする場合には、常に依存関係プロパティとしてプロパティを実装する必要があります。  
  
-   プロパティをスタイルで設定可能にする。 詳しくは、「 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」をご覧ください。  
  
-   プロパティでデータ バインディングをサポートする。 データ バインディングの依存関係プロパティの詳細については、「[2 つのコントロールのプロパティをバインドする](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md)」を参照してください。  
  
-   プロパティを動的リソース参照で設定可能にする。 詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
-   要素ツリーの親要素からプロパティ値を自動的に継承する。 この場合、登録、<xref:System.Windows.DependencyProperty.RegisterAttached%2A>メソッド、プロパティのラッパーも作成する場合でも[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]アクセスします。 詳細については、「[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)」を参照してください。  
  
-   プロパティをアニメーション化できるようにする。 詳しくは、「 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」をご覧ください。  
  
-   プロパティの前の値が、プロパティ システム、環境、または、ユーザーによって行われたアクションによって変更された場合、または読み取りおよびスタイルの使用によって変更された場合に、プロパティ システムに報告させる。 プロパティのメタデータを使用すると、プロパティ システムがプロパティ値が明らかに変更されたと判断するたびに呼び出されるコールバック メソッドをプロパティで指定できます。 関連する概念は、プロパティ値の強制型変換です。 詳しくは、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」を参照してください。  
  
-   プロパティ値の変更に、要素のビジュアルを再構成するためのレイアウト システムが必要かどうかを報告するなど、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロセスでも使用されている確立されたメタデータ規則を使用する。 または、派生クラスが既定値などのメタデータに基づく特性を変更できるように、メタデータのオーバーライドを使用できるようする。  
  
-   カスタム コントロールのプロパティで、**[プロパティ]** ウィンドウの編集などの [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] のサポートを受ける。 詳しくは、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
 これらのシナリオを検討するときに、完全に新しいプロパティを実装するよりも、既存の依存関係プロパティのメタデータをオーバーライドすることで、シナリオを実現できるかどうかも考慮する必要があります。 メタデータのオーバーライドが実用的かどうかは、シナリオとそのシナリオが既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 依存関係プロパティとクラスでの実装にどのくらい似ているかによって異なります。 既存のプロパティでメタデータをオーバーライドする方法の詳細については、「[依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)」を参照してください。  
  
<a name="checklist"></a>   
## <a name="checklist-for-defining-a-dependency-property"></a>依存関係プロパティを定義するためのチェックリスト  
 依存関係プロパティの定義は、次の 4 つの異なる概念で構成されます。 これらの概念は、一部は実装で最終的に 1 行のコードとして結合されるため、必ずしも厳密な手順である必要はありません。  
  
-   (省略可能) 依存関係プロパティのプロパティ メタデータを作成します。  
  
-   所有者型とプロパティ値の型を指定して、プロパティ システムにプロパティ名を登録します。 プロパティのメタデータも指定します (使用している場合)。  
  
-   定義、<xref:System.Windows.DependencyProperty>と識別子、 `public` `static` `readonly`フィールドで、所有者型。  
  
-   名前が依存関係プロパティの名前と一致する [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "ラッパー" プロパティを定義します。 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "ラッパー" プロパティの `get` と `set` のアクセサーを実装して、バッキングする依存関係プロパティと接続します。  
  
<a name="registering"></a>   
### <a name="registering-the-property-with-the-property-system"></a>プロパティ システムにプロパティを登録する  
 プロパティを依存関係プロパティにするためには、そのプロパティをプロパティ システムが保持するテーブルに登録し、その後のプロパティ システム操作で修飾子として使用する一意の識別子をプロパティに設定します。 これらの操作は、内部操作にすることも、プロパティ システム [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] を呼び出す独自のコードにすることもできます。 プロパティを登録するを呼び出す、<xref:System.Windows.DependencyProperty.Register%2A>クラス (クラス内部では、メンバーの定義の外部で) の本文内のメソッドです。 識別子のフィールドがによって提供されるも、<xref:System.Windows.DependencyProperty.Register%2A>メソッドの呼び出し、戻り値として。 理由を<xref:System.Windows.DependencyProperty.Register%2A>呼び出しが完了の定義がこの戻り値を使用して作成するためには他のメンバーの外部で、 `public` `static` `readonly`型のフィールド<xref:System.Windows.DependencyProperty>クラスの一部として。 このフィールドは、依存関係プロパティの識別子になります。  
  
 [!code-csharp[WPFAquariumSln#RegisterAG](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
 [!code-vb[WPFAquariumSln#RegisterAG](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]  
  
<a name="nameconventions"></a>   
### <a name="dependency-property-name-conventions"></a>依存関係プロパティの命名規則  
 依存関係プロパティについては、確立されている命名規則があり、例外的な状況を除き、必ず従う必要があります。  
  
 依存関係プロパティ自体になります"AquariumGraphic"の最初のパラメーターとして指定された、この例のように、基本名前<xref:System.Windows.DependencyProperty.Register%2A>です。 この名前は、それぞれの登録型内で一意である必要があります。 基本型から継承された依存関係プロパティは、登録型の一部に既になっていると見なされ、継承されたプロパティの名前は、再度登録することはできません。 しかし、その依存関係プロパティが継承されていない場合でも、依存関係プロパティの所有者としてクラスを追加する方法があります。詳細については、「[依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)」を参照してください。  
  
 識別子フィールドを作成するときに、登録したプロパティの名前にサフィックス `Property` を付けて、このフィールドに名前を付けます。 このフィールドは、プロパティの識別子、依存関係、および用の入力として後で使用する、<xref:System.Windows.DependencyObject.SetValue%2A>と<xref:System.Windows.DependencyObject.GetValue%2A>ようにする、他のコードへのアクセスによって独自のコードでプロパティを外部コードのアクセスによって、ラッパーでする呼び出しを許可します。をプロパティ システムおよび場合によって[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ。  
  
> [!NOTE]
>  クラス本体で依存関係プロパティを定義することは一般的な実装ですが、クラスの静的コンストラクターで依存関係プロパティを定義することもできます。 依存関係プロパティを初期化するために複数行のコードが必要な場合には、このアプローチが適している場合があります。  
  
<a name="wrapper1"></a>   
### <a name="implementing-the-wrapper"></a>"ラッパー" を実装する  
 ラッパー実装を呼び出す必要があります<xref:System.Windows.DependencyObject.GetValue%2A>で、`get`実装と<xref:System.Windows.DependencyObject.SetValue%2A>で、 `set` (元の登録呼び出しとフィールドは、次に示すすぎるわかりやすくするため) の実装です。  
  
 以外のすべての例外のような状況で、ラッパーの実装をのみ実行する必要があります、<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>アクション、それぞれします。 この理由については、「[XAML 読み込みと依存関係プロパティ](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)」のトピックで説明しています。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスで提供されているすべての既存のパブリックな依存関係プロパティは、この単純なラッパー実装モデルを使用します。依存関係プロパティのしくみの複雑さの大部分は、本質的にプロパティ システムの動作であるか、強制変換やプロパティ メタデータを通じたプロパティ変更のコールバックなど、その他の概念を通じて実装されます。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
 もう一度、規則では、ラッパーのプロパティの名前があります選ばれの最初のパラメーターとして指定されている名前と同じ、<xref:System.Windows.DependencyProperty.Register%2A>プロパティを登録します。 プロパティが規則に従っていない場合、すべての可能な使用を無効にする必要はありませんが、次のような注目すべき問題がいくつか発生します。  
  
-   スタイルとテンプレートの一部が機能しない。  
  
-   ほとんどのツールとデザイナーは、適切に [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] をシリアル化するため、またはプロパティごとのレベルでのデザイナー環境のサポートを提供するために命名規則に依存する必要があります。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ローダーの現在の実装は、属性値を処理するときに、ラッパーを完全にバイパスして、命名規則に依存しています。 詳しくは、「[XAML 読み込みと依存関係プロパティ](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)」を参照してください。  
  
<a name="metadata"></a>   
### <a name="property-metadata-for-a-new-dependency-property"></a>新しい依存関係プロパティのプロパティ メタデータ  
 依存関係プロパティを登録するときに、プロパティ システムを通じて登録すると、プロパティの特性を格納するメタデータ オブジェクトが作成されます。 これらの特性の多くの設定の単純なシグネチャを持つプロパティが登録されている場合に設定されているデフォルト<xref:System.Windows.DependencyProperty.Register%2A>です。 その他のシグネチャ<xref:System.Windows.DependencyProperty.Register%2A>を使用するプロパティを登録すると、メタデータを指定できます。 依存関係プロパティに指定される最も一般的なメタデータは、プロパティを使用する新しいインスタンスに適用される既定値を与えるためのものです。  
  
 派生クラスに存在する依存関係プロパティを作成するかどうかは<xref:System.Windows.FrameworkElement>、特殊化のメタデータ クラスを使用して<xref:System.Windows.FrameworkPropertyMetadata>ベースではなく<xref:System.Windows.PropertyMetadata>クラスです。 コンス トラクター、<xref:System.Windows.FrameworkPropertyMetadata>クラスには複数の署名の組み合わせでメタデータのさまざまな特性を指定できます。 既定値のみを指定する場合は、型の 1 つのパラメーターを受け取る署名を使用して<xref:System.Object>です。 プロパティの種類に固有の既定値としてそのオブジェクトのパラメーターを渡す (指定された既定値として提供された型である必要があります、`propertyType`内のパラメーター、<xref:System.Windows.DependencyProperty.Register%2A>呼び出し)。  
  
 <xref:System.Windows.FrameworkPropertyMetadata>プロパティのメタデータ オプション フラグを指定することもできます。 これらのフラグは、登録後にプロパティ メタデータで個々のプロパティに変換され、特定の条件をレイアウト エンジンなどの他のプロセスに伝えるために使用されます。  
  
#### <a name="setting-appropriate-metadata-flags"></a>適切なメタデータ フラグの設定  
  
-   プロパティ (またはその値の変更) の影響、 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]、具体的には影響を与えますレイアウト システムのサイズまたはページで、要素のレンダリング方法を設定、次のフラグの 1 つ以上と: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>、 <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>、<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>です。  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> このプロパティを変更する変更が必要であることを示します[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を格納しているオブジェクト可能性があります多いまたは少ない親内の領域を表示します。 たとえば、"Width" プロパティには、このフラグが設定されている必要があります。  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> このプロパティを変更する変更が必要であることを示します[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]専用領域で、変更は必要ありませんが、領域内の位置が変更されたこと示すものでは通常表示されます。 たとえば、"Alignment" プロパティには、このフラグが設定されている必要があります。  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> 示す他のいくつかの変更が発生したことは影響しませんレイアウトと、メジャーが別のレンダリングでは必要です。 "Background" など、既存の要素の色を変更するプロパティはその一例です。  
  
    -   これらのフラグは、プロパティ システムやレイアウトのコールバックの独自のオーバーライド実装のためのメタデータのプロトコルとしてよく使用されます。 たとえば、する必要があります、<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>が呼び出すコールバック<xref:System.Windows.UIElement.InvalidateArrange%2A>インスタンスの任意のプロパティが値の変更が報告されがあるかどうか<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>として`true`のメタデータ。  
  
-   上記で説明した必要なサイズを変更する方法に加え、一部のプロパティは含まれる親要素のレンダリング特性に影響する場合があります。 例としては、<xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A>プロパティが、フロー ドキュメント モデルで使用される、そのプロパティへの変更が、フロー ドキュメントの段落を含むの全体的な表示を変更できます。 使用して<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange>または<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure>独自のプロパティのようなケースを特定します。  
  
-   既定では、依存関係プロパティはデータ バインディングをサポートします。 データ バインディングにとって現実的なシナリオがない場合や、大きなオブジェクトのデータ バインディングのパフォーマンスが問題として認識される場合には、意図的にデータ バインディングを無効にすることができます。  
  
-   既定では、データ バインディング<xref:System.Windows.Data.Binding.Mode%2A>に依存関係プロパティの既定の<xref:System.Windows.Data.BindingMode.OneWay>します。 バインドを変更することができます<xref:System.Windows.Data.BindingMode.TwoWay>バインディングのインスタンスごとです。 詳細については、を参照してください。[バインドの方向を指定する](../../../../docs/framework/wpf/data/how-to-specify-the-direction-of-the-binding.md)です。 作成者として、依存関係プロパティをプロパティを使用してを選択できますが、<xref:System.Windows.Data.BindingMode.TwoWay>既定では、バインディング モード。 既存の依存関係プロパティの例は<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; をこのプロパティのシナリオは、<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>ロジックおよびの複合設定<xref:System.Windows.Controls.MenuItem>既定のテーマ スタイルと対話します。 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>プロパティ ロジックを使用してデータ バインディング ネイティブに従って他の状態のプロパティおよびメソッドの呼び出しに、プロパティの状態を維持するためにします。 バインドの別の例プロパティ<xref:System.Windows.Data.BindingMode.TwoWay>既定では<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>します。  
  
-   設定して、カスタムの依存関係プロパティのプロパティの継承を有効にすることもできます、<xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits>フラグ。 プロパティの継承は、親要素と子要素に共通のプロパティがあるシナリオに便利で、子要素に、親に設定されたのと同じ値に設定した特定のプロパティ値を持たせることは理にかなっています。 例の継承可能なプロパティは<xref:System.Windows.FrameworkElement.DataContext%2A>、バインディング、データの表示重要なマスター/詳細シナリオを実現する操作に使用されます。 させて<xref:System.Windows.FrameworkElement.DataContext%2A>継承可能なすべての子要素を継承がデータ コンテキストもします。 プロパティ値の継承により、ページまたはアプリケーションのルートでデータ コンテキストを指定できます。すべての使用可能な子要素内のバインディングに再度指定する必要はありません。 <xref:System.Windows.FrameworkElement.DataContext%2A> 継承が既定値をオーバーライドしますが常に設定することがローカルで; 任意の特定の子要素でを示す良い例ではも詳細については、「[階層データをマスター/詳細形式のパターンを使用して](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)です。 プロパティ値の継承にはパフォーマンスが低下する可能性があるため、控え目に使用する必要があります。詳細については、「[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)」を参照してください。  
  
-   設定、<xref:System.Windows.FrameworkPropertyMetadataOptions.Journal>依存関係プロパティを検出するか、ナビゲーション履歴サービスによって使用されるかどうかを示すフラグ。 例としては、<xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>プロパティです。 選択範囲で選択された項目コントロールは、ジャーナル履歴の移動が永続化する必要があります。  
  
<a name="RODP"></a>   
## <a name="read-only-dependency-properties"></a>読み取り専用の依存関係プロパティ  
 読み取り専用の依存関係プロパティを定義することができます。 ただし、読み取り専用としてプロパティを定義する理由のシナリオには、プロパティ システムに登録して、識別子を公開するための手順が異なるため、若干の違いがあります。 詳細については、「[読み取り専用の依存関係プロパティ](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)」を参照してください。  
  
<a name="CTDP"></a>   
## <a name="collection-type-dependency-properties"></a>コレクション型依存関係プロパティ  
 コレクション型依存関係プロパティには、考慮すべき実装問題が他にもいくつかあります。 詳細については、「[コレクション型依存関係プロパティ](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)」を参照してください。  
  
<a name="SecurityC"></a>   
## <a name="dependency-property-security-considerations"></a>依存関係プロパティのセキュリティに関する考慮事項  
 依存関係プロパティは、パブリック プロパティとして宣言する必要があります。 依存関係プロパティ識別子フィールドは、パブリック静的フィールドとして宣言する必要があります。 他のアクセス レベル (プロテクトなど) を宣言しようとした場合でも、依存関係プロパティには、プロパティ システム [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] と組み合わせた識別子を通じて、常にアクセスできます。 保護された識別子のフィールドでもはメタデータのレポートまたは値の決定のため可能性のあるアクセス可能な[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]などプロパティ システムの一部である<xref:System.Windows.LocalValueEnumerator>です。 詳細については、「[依存関係プロパティのセキュリティ](../../../../docs/framework/wpf/advanced/dependency-property-security.md)」を参照してください。  
  
<a name="DPCtor"></a>   
## <a name="dependency-properties-and-class-constructors"></a>依存関係プロパティとクラス コンストラクター  
 マネージ コード プログラミングでは、クラス コンストラクターが仮想メソッドを呼び出さないという一般的な方針があります (多くの場合は FxCop などのコード分析ツールによって適用されます)。 これは、派生クラスのコンストラクターの基本の初期化としてコンストラクターを呼び出すことができ、コンストラクターから仮想メソッドを入力することで、構築されるオブジェクトのインスタンスの初期化が不完全な状態で行われる可能性があるためです。 既にから派生したクラスから派生したときに<xref:System.Windows.DependencyObject>、ことに注意プロパティ システム自体を呼び出す内部仮想メソッドを公開する必要があります。 これらの仮想メソッドは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システム サービスの一部です。 メソッドをオーバーライドすることで、派生クラスが値の決定に参加できるようになります。 ランタイムの初期化の潜在的な問題を回避するには、非常に特殊なコンストラクター パターンに従っている場合を除き、依存関係プロパティの値をクラスのコンストラクター内で設定しないでください。 詳細については、「[DependencyObject の安全なコンストラクター パターン](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [コレクション型依存関係プロパティ](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [依存関係プロパティのセキュリティ](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [XAML 読み込みと依存関係プロパティ](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)  
 [DependencyObject の安全なコンストラクター パターン](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
