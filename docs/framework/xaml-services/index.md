---
title: "XAML Services | Microsoft Docs"
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
  - "XAML [XAML Services], System.Xaml concepts"
  - "XAML Services in WPF [XAML Services]"
  - "System.Xaml [XAML Services], conceptual documentation"
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
caps.latest.revision: 13
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 13
---
# XAML Services
このトピックでは、.NET Framework XAML サービスと呼ばれる一連の技術の機能について説明します。  説明するサービスや API の大半は、.NET コア アセンブリの [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] セットで導入された System.Xaml アセンブリ内に存在します。  サービスには、リーダーとライター、スキーマ クラスとスキーマ サポート、ファクトリ、クラスの属性、組み込み XAML 言語サポート、その他の XAML 言語機能などが含まれます。  
  
## ドキュメントの内容  
 .NET Framework XAML サービスの概念説明のドキュメントは、読者が XAML 言語の経験があり、[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] や [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] などの特定のフレームワークに対して、または <xref:Microsoft.Build.Framework.XamlTypes> のビルド カスタマイズ機能など、特定の技術機能領域に対して XAML 言語がどのように適用されるかを知っていることを想定しています。  このドキュメントでは、マークアップ言語としての XAML の基礎、XAML 構文の用語、またはその他の基本的な内容については説明するのではなく、  System.Xaml アセンブリ ライブラリで有効になっている .NET Framework XAML サービスの使用方法について詳しく説明します。  これらの API の大半は、XAML 言語の統合および拡張性に伴うシナリオで使用されます。  具体的には、次のような例が挙げられます。  
  
-   基本的な XAML リーダーまたは XAML ライターの機能の拡張 \(XAML ノード ストリームの直接処理、独自の XAML リーダーまたは XAML ライターの派生\)。  
  
-   特定のフレームワークの依存関係がない XAML 対応のカスタム型の定義、XAML 型システムの特性を .NET Framework XAML サービスに伝達するための型の属性設定。  
  
-   XAML マークアップ ソース用のビジュアルなデザイナーや対話形式エディターなど、アプリケーションのコンポーネントとしての XAML リーダーまたは XAML ライターのホスティング。  
  
-   XAML 値コンバーターの記述 \(マークアップ拡張機能、カスタム型用の型コンバーター\)。  
  
-   カスタム XAML スキーマ コンテキストの定義 \(バッキング型ソースに対応するアセンブリ読み込みの代替方法の使用、アセンブリを常に反映する代わりに既知の型をルックアップする方法の使用、CLR `AppDomain` とその関連付けられたセキュリティ モデルを使用しない、読み込まれたアセンブリ概念の使用\)。  
  
-   基本的な XAML 型システムの拡張。  
  
-   XAML 型システムや型バッキングの評価方法に影響を与える `Lookup` 手法または `Invoker` 手法の使用。  
  
 言語としての XAML の入門資料が必要な場合は、「[XAML の概要 \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)」を参照してください。  このトピックでは、[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] と XAML マークアップおよび XAML 言語機能を初めて使用するユーザー向けに、XAML を解説します。  「[XAML language specification \(XAML 言語仕様\)](http://go.microsoft.com/fwlink/?LinkId=114525)」の入門資料も有用です。  
  
## .NET アーキテクチャの .NET Framework XAML サービスおよび System.Xaml  
 以前のバージョンの [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] では、XAML 言語機能のサポートは [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] \([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、[!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]、および [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)]\) に構築されたフレームワークによって実装されていたので、使用されるフレームワークによって、それぞれの動作と API が異なっていました。  これには、XAML のパーサーとそのオブジェクト グラフの作成機構、組み込み XAML 言語、シリアル化のサポートなどが含まれます。  
  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、.NET Framework XAML サービスと System.Xaml アセンブリによって、XAML 言語機能のサポートに必要な要素の大半が定義されます。  たとえば、XAML リーダーと XAML ライターの基本クラスなどです。  他のフレームワーク固有の XAML 実装には存在しなかった機能で、.NET Framework XAML サービスに追加された最も重要な機能とは、XAML の型システム表現です。  型システム表現では、フレームワークの特定の機能に依存することなく、XAML の機能に重点を置いたオブジェクト指向の方法で XAML を記述できます。  
  
 XAML 型システムは、XAML の起点のマークアップ形式やランタイムの詳細にも、特定のバッキング型システムにも制約されません。  XAML 型システムには、型、メンバー、XAML スキーマ コンテキスト、XML レベルの概念、およびその他の XAML 言語概念や組み込みの XAML オブジェクト表現が含まれます。  XAML 型システムを使用または拡張することにより、XAML リーダーや XAML ライターなどのクラスから派生したり、XAML を消費または生成するフレームワーク、技術、またはアプリケーションによって有効化される特定の機能に XAML 表現の機能を拡張したりできます。  XAML スキーマ コンテキストの概念に基づいて、XAML オブジェクト ライターの実装、コンテキストのアセンブリ情報で受け渡される技術のバッキング型システム、および XAML ノード ソースの組み合わせから、実用的なオブジェクト グラフの書き込み操作を実行できます。  XAML スキーマの概念の詳細については、  「[Default XAML Schema Context and WPF XAML Schema Context](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md)」を参照してください。  
  
## XAML ノード ストリーム、XAML リーダー、および XAML ライター  
 XAML 言語と、XAML を言語として使用する特定の技術との関係において .NET Framework XAML サービスが担う役割を理解するには、XAML ノード ストリームの概念と、その概念に基づいて API や用語がどのように形成されるかを理解しておくと便利です。  XAML ノード ストリームとは、XAML 言語表現と、XAML が表現または定義するオブジェクト グラフ間の中間概念です。  
  
-   XAML リーダーとは、なんらかの形で XAML を処理し、XAML ノード ストリームを生成するエンティティです。  API では、XAML リーダーは基本クラス <xref:System.Xaml.XamlReader> で表されます。  
  
-   XAML ライターとは、XAML ノード ストリームを処理し、他のものを生成するエンティティです。  API では、XAML ライターは基本クラス <xref:System.Xaml.XamlWriter> で表されます。  
  
 XAML に関する 2 つの最も一般的なシナリオとは、XAML を読み込んでオブジェクト グラフをインスタンス化することと、アプリケーションまたはツールからオブジェクト グラフを保存して XAML 表現を作成することです \(通常は、テキスト ファイルとして保存されるマークアップ形式\)。  このドキュメントでは通常、XAML の読み込みとオブジェクト グラフの作成を、読み込みパスと呼びます。  このドキュメントでは通常、既存のオブジェクト グラフを XAML に保存、またはシリアル化することを、保存パスと呼びます。  
  
 最も一般的な種類の読み込みパスは、次のように説明できます。  
  
-   UTF エンコードされた XML 形式をテキスト ファイルとして保存した XAML 表現から開始します。  
  
-   その XAML を <xref:System.Xaml.XamlXmlReader> に読み込みます。  ここで <xref:System.Xaml.XamlXmlReader> は、<xref:System.Xaml.XamlReader> のサブクラスです。  
  
-   その結果、XAML ノード ストリームが生成されます。  <xref:System.Xaml.XamlXmlReader> \/ <xref:System.Xaml.XamlReader> API を使用し、XAML ノード ストリームの個別のノードにアクセスできます。  ここで最も一般的な操作とは、"現在のレコード" 比喩を使用し、各ノードを処理しながら XAML ノード ストリーム内の先に進むことです。  
  
-   結果として生成されるノードを XAML ノード ストリームから <xref:System.Xaml.XamlObjectWriter> API に渡します。  ここで <xref:System.Xaml.XamlObjectWriter> は、<xref:System.Xaml.XamlWriter> のサブクラスです。  
  
-   <xref:System.Xaml.XamlObjectWriter> は、ソース XAML ノード ストリーム内を進みながらオブジェクトを 1 つずつ記述し、オブジェクト グラフを作成します。  この処理は、XAML スキーマ コンテキストと、バッキング型システムおよびフレームワークのアセンブリと型にアクセスできる実装によって行われます。  
  
-   XAML ノード ストリームの最後で <xref:System.Xaml.XamlObjectWriter.Result%2A> を呼び出して、オブジェクト グラフのルート オブジェクトを取得します。  
  
 最も一般的な種類の保存パスは、次のように説明できます。  
  
-   アプリケーション ランタイム全体のオブジェクト グラフ、UI コンテンツおよびランタイムの状態、またはランタイム時のアプリケーション全体のオブジェクト表現の小規模なセグメントから開始します。  
  
-   アプリケーション ルート、ドキュメント ルートなどの論理的な開始オブジェクトから <xref:System.Xaml.XamlObjectReader> にオブジェクトを読み込みます。  ここで <xref:System.Xaml.XamlObjectReader> は、<xref:System.Xaml.XamlReader> のサブクラスです。  
  
-   その結果、XAML ノード ストリームが生成されます。  <xref:System.Xaml.XamlObjectReader> および <xref:System.Xaml.XamlReader> API を使用して、XAML ノード ストリームの個別のノードにアクセスできます。  ここで最も一般的な操作とは、"現在のレコード" 比喩を使用し、各ノードを処理しながら XAML ノード ストリーム内の先に進むことです。  
  
-   結果として生成されるノードを XAML ノード ストリームから <xref:System.Xaml.XamlXmlWriter> API に渡します。  ここで <xref:System.Xaml.XamlXmlWriter> は、<xref:System.Xaml.XamlWriter> のサブクラスです。  
  
-   <xref:System.Xaml.XamlXmlWriter> は、XML UTF エンコードで XAML を記述します。  これをテキスト ファイル、ストリーム、またはその他のフォームで保存できます。  
  
-   <xref:System.Xaml.XamlXmlWriter.Flush%2A> を呼び出して、最終的な出力を取得します。  
  
 XAML ノード ストリームの概念の詳細については、「[Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)」を参照してください。  
  
### XamlServices クラス  
 XAML ノード ストリームは、必ずしも処理する必要はありません。  基本的な読み込みパスまたは基本的な保存パスが必要な場合は、<xref:System.Xaml.XamlServices> クラスの API を使用できます。  
  
-   <xref:System.Xaml.XamlServices.Load%2A> のさまざまなシグネチャは、読み込みパスを実装しています。  ファイルまたはストリームを読み込むか、リーダーの API で読み込むことによって XAML 入力をラップする <xref:System.Xml.XmlReader>、<xref:System.IO.TextReader>、または <xref:System.Xaml.XamlReader> を読み込むことができます。  
  
-   <xref:System.Xaml.XamlServices.Save%2A> のさまざまなシグネチャがオブジェクト グラフを保存し、ストリーム、ファイル、または <xref:System.Xml.XmlWriter>\/<xref:System.IO.TextWriter> インスタンスとして出力を生成します。  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> は、読み込みパスと保存パスを単独の操作としてリンクすることによって、XAML を変換します。  <xref:System.Xaml.XamlReader> および <xref:System.Xaml.XamlWriter> に対して異なるスキーマ コンテキスト、または異なるバッキング型システムを使用できます。これによって、結果として生成される XAML がどのように変換されるかが影響を受けます。  
  
 <xref:System.Xaml.XamlServices> の使用方法の詳細については、「[XAMLServices Class and Basic XAML Reading or Writing](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md)」を参照してください。  
  
## XAML 型システム  
 XAML 型システムには、XAML ノード ストリームにおいて指定された個別ノードで作業するために必要となる API が用意されています。  
  
 <xref:System.Xaml.XamlType> はオブジェクトの表現であり、開始オブジェクト ノードと終了オブジェクト ノード間で処理されます。  
  
 <xref:System.Xaml.XamlMember> はオブジェクトのメンバーの表現で、開始メンバー ノードと終了メンバー ノード間で処理されます。  
  
 <xref:System.Xaml.XamlType.GetAllMembers%2A>、<xref:System.Xaml.XamlType.GetMember%2A>、<xref:System.Xaml.XamlMember.DeclaringType%2A> のような API は、<xref:System.Xaml.XamlType> と <xref:System.Xaml.XamlMember> との関係を報告します。  
  
 .NET Framework XAML サービスで実装される XAML 型システムの既定の動作は、共通言語ランタイム \(CLR\) と、リフレクションを使用する、アセンブリの CLR 型のスタティック分析に基づいて実装されます。  したがって、特定の CLR 型について、XAML 型システムの既定の実装はその型の XAML スキーマとメンバーを公開し、それを XAML 型システムに基づいて報告できます。  既定の XAML 型システムでは、型が割り当てできるかどうかの概念は CLR の継承にマッピングされ、インスタンスや値の型などの概念も、CLR をサポートする動作や機能にマッピングされます。  
  
## XAML 言語機能のリファレンス  
 XAML をサポートするため、.NET Framework XAML サービスには、XAML 言語の XAML 名前空間に対する定義として、XAML 言語概念の特定の実装が用意されています。  具体的には、固有のリファレンス ページで説明しています。  言語機能については、.NET Framework XAML サービスで定義された XAML リーダーまたは XAML ライターによって処理される際に、各言語機能がどのように動作するかという視点から説明しています。  詳細については、「[XAML Namespace \(x:\) Language Features](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)」を参照してください。