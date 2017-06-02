---
title: "Default XAML Schema Context and WPF XAML Schema Context | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# Default XAML Schema Context and WPF XAML Schema Context
XAML スキーマ コンテキストは、型の対応付けの解決方法、アセンブリの読み込み方法、特定のリーダーとライターの設定を解釈する方法など、特定の XAML ボキャブラリを使用する XAML 稼働環境がオブジェクトの書き込み動作を操作する方法を修飾する、概念上のエンティティです。  ここでは、.NET Framework XAML サービスの機能と、関連付けられている既定の XAML スキーマ コンテキスト \(CLR 型システムに基づく\) について説明します。  また、WPF で使用される XAML スキーマ コンテキストについても説明します。  
  
## 既定の XAML スキーマ コンテキスト  
 .NET Framework XAML サービスは、既定の XAML スキーマ コンテキストを実装して使用します。  既定の XAML スキーマ コンテキストの動作は、<xref:System.Xaml.XamlSchemaContext> クラスの API で必ずしも完全に確認できるわけではありません。  ただし、多くの場合、既定の XAML スキーマ コンテキストの影響を受ける動作は、<xref:System.Xaml.XamlMember> や <xref:System.Xaml.XamlType> のメンバーなど、XAML 型システムの共通 API や、既定の XAML スキーマ コンテキストを使用する XAML リーダーと XAML ライターで公開される API を通じて確認できます。  
  
 <xref:System.Xaml.XamlSchemaContext> コンストラクターを呼び出して、既定の動作をカプセル化する <xref:System.Xaml.XamlSchemaContext> を作成できます。  これにより、既定の XAML スキーマ コンテキストが明示的に作成されます。  <xref:System.Xaml.XamlSchemaContext> 入力パラメーターを明示的に受け取らない API を使用して XAML リーダーまたは XAML ライターを初期化した場合は、同じ既定の XAML スキーマ コンテキストが暗黙的に作成されます。  
  
 既定の XAML スキーマ コンテキストは、型の対応付け動作について CLR リフレクションに依存します。  これには、CLR <xref:System.Type>、および関連する <xref:System.Reflection.PropertyInfo> または <xref:System.Reflection.MethodInfo> の定義の検証が含まれます。  また、型またはメンバーの CLR 属性は、CLR バッキング型を使用する XAML 型または XAML メンバー情報の詳細を指定するために使用されます。  既定の XAML スキーマ コンテキストには、`Invoker` パターンをはじめとする型システム拡張手法は必要ありません。CLR 型システムから必要な情報を得られるためです。  
  
 アセンブリ読み込みロジックの場合、既定の XAML スキーマ コンテキストは、主に XAML 名前空間のマッピングで提供されるアセンブリ値に依存します。  また、内部型の読み込みなどのシナリオでは、読み込むアセンブリを <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> が示します。  
  
## WPF XAML スキーマ コンテキスト  
 WPF の実装は、既定以外の XAML スキーマ コンテキストの実装により導入できるタイプの機能を示すうえで興味深いテーマであるため、WPF XAML スキーマ コンテキストについてはこのトピックで説明します。  また、XAML スキーマ コンテキストの概念は、WPF XAML に関する WPF のドキュメントではあまり詳しく説明されていません。XAML スキーマ コンテキストが実現する動作は、既定の XAML スキーマ コンテキストの動作と共に説明しなければ、十分に理解できない可能性があります。  WPF XAML スキーマ コンテキストは、次の動作を実装します。  
  
 **検索のオーバーライド:** WPF には、XAML 向けのコンテンツ モデルがいくつか存在します。これらのモデルでは、<xref:System.Windows.Markup.ContentPropertyAttribute> 属性がなくても機能する XAML コンテンツ プロパティが使用されます。  WPF の <xref:System.Xaml.XamlType.LookupContentProperty%2A> のオーバーライドがこの動作を実装します。  
  
 **WPF 式の遅延:** WPF には、ランタイム コンテキストが使用できるようになるまで値を遅延させる式クラスがいくつかあります。  また、テンプレートの拡張は遅延手法に依存するランタイム動作です。  
  
 **型システムの検索の最適化:** WPF には、WPF で定義されている何百ものクラスに継承される基本クラス メンバーの定義など、幅広い XAML ボキャブラリとオブジェクト モデルがあります。  また、WPF 自体も複数のアセンブリにまたがります。  WPF では、ルックアップ テーブルなどの手法を使用して型検索が最適化されます。  その結果、既定の XAML スキーマ コンテキストとその CLR ベースの型検索よりもパフォーマンスが向上します。  型がルックアップ テーブルに存在しない場合は、既定の XAML スキーマ コンテキストに似た XAML スキーマ コンテキストの手法が使用されます。  
  
 **XamlType および XamlMember の拡張:** WPF では、依存関係プロパティによりプロパティの概念が拡張され、ルーティング イベントによりイベントの概念が拡張されています。  XAML 処理操作に対するこれらの概念の可視性を高めるために、WPF では <xref:System.Xaml.XamlType> と <xref:System.Xaml.XamlMember> が拡張され、依存関係プロパティとルーティング イベントの特性を報告する内部プロパティが追加されています。  
  
### WPF XAML スキーマ コンテキストへのアクセス  
 WPF <xref:System.Windows.Markup.XamlReader?displayProperty=fullName> または <xref:System.Windows.Markup.XamlWriter?displayProperty=fullName> に基づく XAML 手法を使用している場合、それらの XAML リーダーと XAML ライターの実装で WPF XAML スキーマ コンテキストが既に使用されています。  
  
 WPF XAML スキーマ コンテキストを使用して初期化しないその他の XAML リーダーまたは XAML ライターの実装を使用している場合は、有効な WPF XAML スキーマ コンテキストを <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=fullName> から入手できます。  そのうえで、<xref:System.Xaml.XamlSchemaContext> を使用する他の API の初期化としてこの値を使用できます。  たとえば、初期化のために <xref:System.Xaml.XamlXmlReader.%23ctor%2A> を呼び出し、WPF XAML スキーマ コンテキストを渡すことができます。  または、XAML 型システムの操作のために WPF XAML スキーマ コンテキストを使用することもできます。  これには、<xref:System.Xaml.XamlType> または <xref:System.Xaml.XamlMember> の構造初期化、または <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=fullName> の呼び出しが含まれます。  
  
 純粋な XAML ノード ストリーム パースペクティブから WPF XAML の特定の要素にアクセスした場合、一部の WPF フレームワーク機能は動作していない可能性があります。  たとえば、コントロールの WPF テンプレートはまだ適用されていません。  したがって、実行時にビジュアル ツリー全体が設定されるプロパティにアクセスする場合は、テンプレートを参照するプロパティ値だけが表示される可能性があります。  WPF マークアップ拡張機能向けのサービス コンテキストも、実行時以外の状況で提供された場合は正確ではない場合があり、オブジェクト グラフを書き込もうとしたときに例外が発生する可能性があります。  
  
## XAML およびアセンブリの読み込み  
 XAML および .NET Framework XAML サービスのアセンブリの読み込みは、CLR で定義された <xref:System.AppDomain> の概念と統合されています。  XAML スキーマ コンテキストでは、<xref:System.AppDomain> およびその他の要素の使用に基づいて、実行時またはデザイン時にアセンブリの読み込みまたは型の検索を行う方法を解釈します。  XAML が XAML リーダーの Loose XAML であるか、`XamlBuildTask` によって DLL にコンパイルされる XAML であるか、WPF の `PresentationBuildTask` によって生成される BAML であるかによって、ロジックは若干異なります。  
  
 WPF の XAML スキーマ コンテキストは WPF アプリケーション モデルと統合され、<xref:System.AppDomain> や、WPF の実装の詳細である他の要素を使用します。  
  
#### XAML リーダーの入力 \(Loose XAML\)  
  
1.  XAML スキーマ コンテキストは、アプリケーションの <xref:System.AppDomain> を反復処理して、名前のすべての要素が一致する読み込み済みのアセンブリを、最も新しく読み込まれたアセンブリから順に検索します。  一致するアセンブリが見つかった場合、そのアセンブリが解決に使用されます。  
  
2.  一致するアセンブリが見つからなかった場合は、CLR <xref:System.Reflection.Assembly> API に基づく次の手法を使用してアセンブリが読み込まれます。  
  
    -   マッピングで名前が修飾されている場合は、修飾名で <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> を呼び出します。  
  
    -   前の手順に失敗した場合は、短い名前と公開キー トークン \(存在する場合\) を使用して <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> を呼び出します。  
  
    -   マッピングで名前が修飾されていない場合は、<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName> を呼び出します。  
  
#### XamlBuildTask  
 `XamlBuildTask` は、[!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)] と [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] で使用されます。  
  
 `XamlBuildTask` を通じたアセンブリ参照は、常に完全に修飾されます。  
  
1.  修飾名で <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> を呼び出します。  
  
2.  前の手順に失敗した場合は、短い名前と公開キー トークン \(存在する場合\) を使用して <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> を呼び出します。  
  
#### BAML \(PresentationBuildTask\)  
 BAML のアセンブリ読み込みには、BAML をコンポーネントとして内包する初期アセンブリの読み込みと、BAML 稼働環境で参照される任意の型の型バッキング アセンブリの読み込みという 2 つの側面があります。  
  
##### 初期マークアップのアセンブリ読み込み:  
 マークアップの読み込み元アセンブリへの参照は、常に修飾されません。  
  
1.  WPF XAML スキーマ コンテキストは、WPF アプリケーションの <xref:System.AppDomain> を反復処理して、名前のすべての要素が一致する読み込み済みのアセンブリを、最も新しく読み込まれたアセンブリから順に検索します。  一致するアセンブリが見つかった場合、そのアセンブリが解決に使用されます。  
  
2.  前の手順に失敗した場合は、短い名前と公開キー トークン \(存在する場合\) を使用して <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> を呼び出します。  
  
##### BAML 型によるアセンブリ参照:  
 BAML 稼働環境で使用される型のアセンブリ参照は、ビルド タスクの出力として常に完全に修飾されます。  
  
1.  WPF XAML スキーマ コンテキストは、WPF アプリケーションの <xref:System.AppDomain> を反復処理して、名前のすべての要素が一致する読み込み済みのアセンブリを、最も新しく読み込まれたアセンブリから順に検索します。  一致するアセンブリが見つかった場合、そのアセンブリが解決に使用されます。  
  
2.  一致するアセンブリが見つからなかった場合は、アセンブリの読み込みに次のいずれかの手法を使用します。  
  
    -   修飾名で <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> を呼び出します。  
  
    -   短い名前と公開キー トークンの組み合わせが、BAML の読み込み元であるアセンブリに一致する場合は、そのアセンブリを使用します。  
  
    -   短い名前と公開キー トークンを使用して、<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> を呼び出します。  
  
## 参照  
 [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)