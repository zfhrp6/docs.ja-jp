---
title: 既定の XAML スキーマ コンテキストと WPF XAML スキーマ コンテキスト
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 9ec161c3af3c2555e04e479fec85c48f90830a87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566029"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>既定の XAML スキーマ コンテキストと WPF XAML スキーマ コンテキスト
XAML スキーマ コンテキストが特定の XAML ボキャブラリを使用する XAML の運用環境が、オブジェクトの型マッピングが解決する方法、アセンブリが読み込まれているか、特定のリーダーとライターをなどの動作を記述とやり取りする方法を修飾するエンティティの概念設定が解釈されます。 このトピックでは、.NET Framework XAML サービスと関連付けられている既定の XAML スキーマ コンテキスト、CLR の型システムに基づくの機能について説明します。 このトピックでは、WPF に使用される、XAML スキーマ コンテキストも説明します。  
  
## <a name="default-xaml-schema-context"></a>既定の XAML スキーマ コンテキスト  
 .NET framework XAML サービス 両方を実装し、既定の XAML スキーマ コンテキストを使用します。 既定の XAML スキーマ コンテキストの動作が常の API で完全に表示されていない、<xref:System.Xaml.XamlSchemaContext>クラスです。 ただし、多くの場合、既定の XAML スキーマ コンテキストに影響を与える動作は、観測可能なオブジェクトのメンバーなど、XAML 型システムの一般的な API を介して<xref:System.Xaml.XamlMember>または<xref:System.Xaml.XamlType>、または XAML リーダーと XAML ライターを使用しているので公開されている Api を使用既定の XAML スキーマ コンテキスト。  
  
 作成することができます、<xref:System.Xaml.XamlSchemaContext>呼び出すことによって、既定の動作をカプセル化する、<xref:System.Xaml.XamlSchemaContext>コンス トラクターです。 これにより、既定の XAML スキーマ コンテキストが明示的に作成されます。 XAML リーダーまたは明示的に受け取らない Api を使用して XAML ライターを初期化する場合、同じ既定の XAML スキーマ コンテキストが暗黙的に、作成、<xref:System.Xaml.XamlSchemaContext>入力パラメーターです。  
  
 既定の XAML スキーマ コンテキストは、その型のマッピングの動作の CLR リフレクションに依存します。 これは、定義の CLR を調べることが含まれています。 <xref:System.Type>、および関連する<xref:System.Reflection.PropertyInfo>または<xref:System.Reflection.MethodInfo>です。 また、型またはメンバーの CLR 属性は、XAML の型または型のバッキング CLR を使用して XAML メンバーの情報の詳細を入力するために使用されます。 既定の XAML スキーマ コンテキストがなどの型システムの拡張機能の手法をしないため、`Invoker`パターン、CLR 型のシステムから、必要な情報があるためです。  
  
 アセンブリのロジックを読み込み、既定の XAML スキーマ コンテキストは XAML 名前空間のマッピングで提供されるすべてのアセンブリ値に主に依存します。 また、<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>アセンブリを読み込むには、内部型の読み込みなどのシナリオにヒントことができます。  
  
## <a name="wpf-xaml-schema-context"></a>WPF XAML スキーマ コンテキスト  
 WPF 実装には既定ではない XAML スキーマ コンテキストを実装することによってもたらされる機能の種類の興味深い例が用意されているために、WPF XAML スキーマ コンテキストはこのトピックで説明します。 また、XAML スキーマ コンテキストの概念では説明しません非常によく WPF XAML; に対応する WPF のドキュメントXAML スキーマ コンテキストが有効にする動作が完全に理解できるものの既定の XAML スキーマ コンテキストの動作方法の詳細については統合されている場合のみ可能性があります。 WPF XAML スキーマ コンテキストでは、次の動作を実装します。  
  
 **参照の上書き:** WPF が XAML のいくつかのコンテンツ モデルを持つが XAML のコンテンツ プロパティがない関数を<xref:System.Windows.Markup.ContentPropertyAttribute>に起因します。 <xref:System.Xaml.XamlType.LookupContentProperty%2A> WPF の上書きは、この動作を実装します。  
  
 **WPF の式の遅延:** WPF ランタイム コンテキストが利用可能になるまでの値を遅らせる式クラスがいくつかの機能です。 また、テンプレートの展開は、遅延手法に依存しているランタイムの動作です。  
  
 **入力システム参照の最適化:** WPF が広範な XAML ボキャブラリとオブジェクト モデルが文字どおり数百台の WPF 定義のクラスを継承する基底クラス メンバーの定義を含むです。 また、いくつかのアセンブリを WPF 自体に分散します。 WPF では、参照テーブルとその他の手法を使用してその型の検索を最適化します。 これは、既定の XAML スキーマ コンテキストとその型の CLR ベースの検索パフォーマンスの向上を提供します。 型が参照テーブルに存在しない場合の場合は、動作は、既定の XAML スキーマ コンテキストのような XAML スキーマ コンテキストのテクニックを使用します。  
  
 **XamlType と XamlMember の拡張機能:** WPF は、依存関係プロパティを持つプロパティの概念を拡張し、ルーティング イベントのイベントの概念とします。 WPF を拡張に、これらの概念をわかりやすくに対して XAML 処理操作、<xref:System.Xaml.XamlType>と<xref:System.Xaml.XamlMember>、依存関係プロパティをレポートおよびイベントの特性をルーティングする内部プロパティを追加します。  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>WPF XAML スキーマ コンテキストにアクセスします。  
 かどうかは、WPF に基づいている XAML の手法を使用している<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>または<xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>、WPF XAML スキーマ コンテキストは既にこれらの XAML リーダーと XAML ライターの実装に使用されています。  
  
 WPF XAML スキーマ コンテキストとその他の XAML リーダーまたは初期化しない XAML ライターの実装を使用している場合は、作業 WPF XAML スキーマ コンテキストを取得することがありますできる<xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>です。 初期化の他の API を使用すると、この値を使用することができますし、<xref:System.Xaml.XamlSchemaContext>です。 たとえば、でした呼び出して<xref:System.Xaml.XamlXmlReader.%23ctor%2A>初期化と WPF XAML スキーマ コンテキストのパス。 または、XAML 型システム操作に、WPF XAML スキーマ コンテキストを使用する可能性があります。 初期化を建設が挙げられます、<xref:System.Xaml.XamlType>または<xref:System.Xaml.XamlMember>、または呼び出し<xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>です。  
  
 WPF XAML の特定の側面は、純粋な XAML ノード ストリームの観点からアクセスする場合 WPF フレームワークの機能の一部が処理しなかったときがまだに注意してください。 たとえば、コントロールの WPF テンプレートはまだ適用されません。 したがって、実行時に完全ビジュアル ツリーに挿入される場合をプロパティにアクセスする可能性がありますのみが表示テンプレートが参照するプロパティ値。 WPF のマークアップ拡張機能を提供するサービス コンテキストはできない可能性がありますもランタイム以外の場合から提供される場合に正確なと、オブジェクト グラフを書き込もうとしているときに例外が発生できます。  
  
## <a name="xaml-and-assembly-loading"></a>XAML およびアセンブリの読み込み  
 アセンブリの XAML と .NET Framework XAML サービスの読み込み 'æ˜aœg' の CLR で定義された概念<xref:System.AppDomain>です。 XAML スキーマ コンテキストでアセンブリを読み込むかの使用状況に基づいて実行時またはデザイン時に、型を検出する方法は、解釈<xref:System.AppDomain>およびその他の要因です。 ロジックは、XAML が XAML リーダーの loose XAML がかどうかによって多少異なりますは、DLL にコンパイルされた XAML `XamlBuildTask`、WPF のによって生成された BAML または`PresentationBuildTask`です。  
  
 WPF の XAML スキーマ コンテキストが順番に使用して、WPF アプリケーション モデルと統合し、 <xref:System.AppDomain> WPF 実装の詳細については、その他の要因とします。  
  
#### <a name="xaml-reader-input-loose-xaml"></a>XAML リーダー入力 (loose XAML)  
  
1.  反復処理、XAML スキーマ コンテキスト、<xref:System.AppDomain>名前のすべての側面に一致する読み込み済みアセンブリを探して、アプリケーションのアセンブリを読み込みました最近、最もから開始します。 一致が見つかった場合、そのアセンブリが解像度を使用します。  
  
2.  それ以外の場合、次の手法のに基づいて CLR <xref:System.Reflection.Assembly> API は、アセンブリの読み込みに使用します。  
  
    -   名前修飾する場合は、マッピングで、呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名にします。  
  
    -   前の手順に失敗した場合は、短い名前 (および存在する場合の公開キー トークン) を使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>です。  
  
    -   名前が、マッピング内で修飾でない場合を呼び出す<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>です。  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask` Windows Communication Foundation (WCF) および Windows Workflow Foundation の使用されます。  
  
 アセンブリが参照するを通じて注`XamlBuildTask`は常に完全修飾します。  
  
1.  呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名にします。  
  
2.  前の手順に失敗した場合は、短い名前 (および存在する場合の公開キー トークン) を使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>です。  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 BAML のアセンブリの読み込みに 2 つの側面があります。 コンポーネントとして BAML を含む最初のアセンブリの読み込みと BAML 生産によって参照されている型の型のバッキング アセンブリを読み込みます。  
  
##### <a name="assembly-load-for-initial-markup"></a>初期のマークアップのアセンブリの読み込み:  
 マークアップを読み込むアセンブリ参照は常に修飾ではありません。  
  
1.  反復処理して、WPF XAML スキーマ コンテキスト、<xref:System.AppDomain>名前のすべての側面に一致する読み込み済みアセンブリを探して、WPF アプリケーションのアセンブリを読み込みました最近、最もから開始します。 一致が見つかった場合、そのアセンブリが解像度を使用します。  
  
2.  前の手順に失敗した場合は、短い名前 (および存在する場合の公開キー トークン) を使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>です。  
  
##### <a name="assembly-references-by-baml-types"></a>BAML 型でアセンブリ参照。  
 BAML 実稼働環境で使用される型のアセンブリ参照は、ビルド タスクの出力として、完全修飾では常にします。  
  
1.  反復処理して、WPF XAML スキーマ コンテキスト、<xref:System.AppDomain>名前のすべての側面に一致する読み込み済みアセンブリを探して、WPF アプリケーションのアセンブリを読み込みました最近、最もから開始します。 一致が見つかった場合、そのアセンブリが解像度を使用します。  
  
2.  それ以外の場合、アセンブリの読み込み、次の手法のいずれかを使用します。  
  
    -   呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名にします。  
  
    -   A の短い名前 + パブリック キー トークンの組み合わせ、BAML から読み込まれたアセンブリと一致する場合は、そのアセンブリを使用します。  
  
    -   短い名前と公開キー トークンを使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>です。  
  
## <a name="see-also"></a>関連項目  
 [XAML ノード ストリームの構造と概念について](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
