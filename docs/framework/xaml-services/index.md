---
title: "XAML サービス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
caps.latest.revision: "13"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 458b4c94d26b7bc083c5d31fcbccf05b42bba52e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-services"></a>XAML サービス
このトピックでは、サービスの .NET Framework XAML と呼ばれるテクノロジ一連の機能について説明します。 導入されたアセンブリである System.Xaml アセンブリに、ほとんどのサービスおよび説明する Api がある、 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] .NET core アセンブリのセット。 サービスには、リーダーとライター、スキーマのクラスおよびスキーマのサポートは、ファクトリ クラス、XAML 言語の組み込みサポート、およびその他の XAML 言語機能の属性です。  
  
## <a name="about-this-documentation"></a>このドキュメントについて  
 .NET Framework XAML サービスの概念に関するドキュメントでは、XAML 言語とその可能性がありますに適用する方法、特定のフレームワークなどの経験があると想定[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]または[!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]の特定のテクノロジの機能領域、またはビルドのカスタマイズの機能の使用例<xref:Microsoft.Build.Framework.XamlTypes>です。 このドキュメントは、マークアップ言語、XAML 構文の用語、またはその他の入門資料として XAML の基礎を説明しません。 代わりに、このドキュメントは、具体的には、System.Xaml アセンブリ ライブラリで有効になっている .NET Framework XAML サービスの使用について説明します。 これらの Api のほとんどは、XAML 言語の統合および拡張機能のシナリオには。 次のいずれかがあります。  
  
-   基本の XAML リーダーや XAML ライター (直接、XAML ノード ストリームを処理以外の場合は、独自の XAML リーダーや XAML ライターを派生) の機能を拡張します。  
  
-   特定のフレームワークの依存関係がない XAML 対応のカスタム型を定義して、XAML を伝えるために、型の属性は、.NET Framework XAML サービスのシステム特性を入力します。  
  
-   ビジュアル デザイナーの XAML マークアップのソースの対話型のエディターなど、アプリケーションのコンポーネントとしての XAML リーダーや XAML ライターをホストします。  
  
-   XAML 値コンバーター (マークアップ拡張機能、カスタム型の型コンバーターの) を記述します。  
  
-   カスタム XAML スキーマ コンテキストを定義する (バッキング型のソースの別のアセンブリの読み込みの手法を使用する以外の場合は常にではなく既知の型参照の手法を使用してアセンブリを反映した以外の場合は、CLR を使用して読み込まれたアセンブリの概念を使用して`AppDomain`と関連付けられているセキュリティ モデル)。  
  
-   基本の XAML 型システムを拡張します。  
  
-   使用して、`Lookup`または`Invoker`に影響を与える、XAML の手法は、システムと型 backings の評価方法を入力します。  
  
 言語としての XAML の入門資料を探してみてください[XAML の概要 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)です。 そのトピックについて説明します XAML は、新しいユーザー向けの両方に[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]と XAML マークアップと XAML 言語機能を使用して、さらにします。 別の役立つ文書は入門資料に、 [XAML 言語仕様](http://go.microsoft.com/fwlink/?LinkId=114525)です。  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET framework XAML サービスと System.Xaml に .NET アーキテクチャ  
 以前のバージョンの[!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)]、上に構築されたフレームワークによって実装されていた XAML 言語機能のサポートを[!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)]([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、[!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]と[!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)])、そのため、動作やによって使用される API でさまざまなと特定のフレームワークを使用していた。 これにより、XAML が含まれます。 パーサーと、オブジェクト グラフの作成メカニズム、XAML 言語の組み込み関数、シリアル化のサポート、およびなどです。  
  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]と System.Xaml アセンブリの .NET Framework XAML サービスの XAML 言語機能をサポートするために必要な量を定義します。 これには、XAML リーダーと XAML ライターの基本クラスが含まれます。 フレームワーク固有の XAML 実装のいずれかに存在していたいない .NET Framework XAML サービスに追加された最も重要な機能は、xaml 型システム表現です。 型システム表現は、フレームワークの特定の機能に依存することがなく XAML の機能に重点を置いたオブジェクト指向の方法で XAML を表示します。  
  
 XAML 型システムは、マークアップ形式または XAML の原点; の実行時の仕様によっては制限されません。またには、特定のバッキング型システムで制限。 XAML 型システムには、型、メンバー、XAML スキーマ コンテキスト、XML レベルの概念、およびその他の XAML 言語の概念または XAML の組み込みのオブジェクト表現が含まれています。 使用するか、XAML 型システムを拡張できるようになります XAML リーダーと XAML ライターなどのクラスから派生し、フレームワーク、テクノロジ、またはを使用するアプリケーションで有効になっている特定の機能に XAML 表現の機能を拡張またはXAML を出力します。 XAML スキーマ コンテキストの概念により、XAML オブジェクト ライターの実装を通じて、コンテキスト、および XAML ノードで、アセンブリ情報とテクノロジのバッキング型システムの組み合わせから実用的なオブジェクト グラフの書き込み操作ソースです。 XAML スキーマの概念の詳細についてはします。 参照してください[既定の XAML スキーマ コンテキストと WPF XAML スキーマ コンテキスト](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md)です。  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>XAML ノード ストリーム、XAML リーダーと XAML ライター  
 .NET Framework XAML サービスは、XAML 言語と言語としての XAML を使用して、特定のテクノロジ間のリレーションシップで果たす役割を理解するのには、XAML ノード ストリームとその概念図形の API の概念を理解しておいて、用語集。 XAML ノード ストリームは、XAML 言語表記と XAML を表すかを定義するオブジェクト グラフ間の中間概念です。  
  
-   XAML リーダーは、何らかの形式で XAML を処理し、XAML ノード ストリームを生成するエンティティです。 API では、XAML リーダーは、基本クラスによって表される<xref:System.Xaml.XamlReader>です。  
  
-   XAML ライターは、XAML ノード ストリームを処理し、他のものを生成するエンティティです。 API では、XAML ライターが、基底クラスによって表される<xref:System.Xaml.XamlWriter>です。  
  
 XAML に関連する 2 つの最も一般的なシナリオは、オブジェクト グラフをインスタンス化する XAML を読み込んでアプリケーションまたはツールからのオブジェクト グラフの保存と (通常はテキスト ファイルとして保存されるマークアップ形式) で XAML 表現を生成します。 XAML を読み込むと、オブジェクト グラフの作成は、読み込みパスとしては、このドキュメントで多くの場合、呼ばれます。 保存または既存のオブジェクト グラフから XAML にシリアル化する多くの場合で参照されて保存先として、このドキュメントのパス。  
  
 読み込みパスの最も一般的な型を以下に説明することができます。  
  
-   UTF でエンコードされた XML 形式での XAML 表現でを起動し、テキスト ファイルとして保存します。  
  
-   その XAML を読み込む<xref:System.Xaml.XamlXmlReader>します。 <xref:System.Xaml.XamlXmlReader><xref:System.Xaml.XamlReader>サブクラスです。  
  
-   XAML ノード ストリームになります。 XAML ノード ストリームを使用して、個々 のノードにアクセスできる<xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> API です。 最も一般的な操作をここでは、XAML ノード ストリーム、「現在のレコード」を使用して各ノードの処理に進むには比喩します。  
  
-   XAML ノード ストリームからの結果として得られるノードを渡す、 <xref:System.Xaml.XamlObjectWriter> API です。 <xref:System.Xaml.XamlObjectWriter><xref:System.Xaml.XamlWriter>サブクラスです。  
  
-   <xref:System.Xaml.XamlObjectWriter>ソース XAML ノード ストリームを使用して進行状況をに従って、一度に 1 つのオブジェクト、オブジェクト グラフを書き込みます。 これは XAML スキーマ コンテキストと、アセンブリと、バッキング型システムおよびフレームワークの型にアクセスできる実装を使用します。  
  
-   呼び出す<xref:System.Xaml.XamlObjectWriter.Result%2A>オブジェクト グラフのルート オブジェクトを取得する XAML ノード ストリームの末尾にします。  
  
 保存パスの最も一般的な型を以下に説明することができます。  
  
-   オブジェクト グラフ全体のアプリケーションの実行時間を UI のコンテンツの実行時にアプリケーション全体のオブジェクト表現の小規模なセグメントまたは、実行時の状態で開始します。  
  
-   アプリケーション ルートまたはドキュメントのルートなどの論理的開始オブジェクトにオブジェクトを読み込む<xref:System.Xaml.XamlObjectReader>します。 <xref:System.Xaml.XamlObjectReader><xref:System.Xaml.XamlReader>サブクラスです。  
  
-   XAML ノード ストリームになります。 XAML ノード ストリームを使用して、個々 のノードにアクセスできる<xref:System.Xaml.XamlObjectReader>と<xref:System.Xaml.XamlReader>API です。 最も一般的な操作をここでは、XAML ノード ストリーム、「現在のレコード」を使用して各ノードの処理に進むには比喩します。  
  
-   XAML ノード ストリームからの結果として得られるノードを渡す、 <xref:System.Xaml.XamlXmlWriter> API です。 <xref:System.Xaml.XamlXmlWriter><xref:System.Xaml.XamlWriter>サブクラスです。  
  
-   <xref:System.Xaml.XamlXmlWriter>エンコード XML UTF で XAML を書き込みます。 これは、ストリーム、またはその他の形式でテキスト ファイルとして保存できます。  
  
-   呼び出す<xref:System.Xaml.XamlXmlWriter.Flush%2A>最終的な出力を取得します。  
  
 XAML ノード ストリームの概念の詳細については、次を参照してください。 [Understanding XAML ノード ストリームの構造と概念](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)です。  
  
### <a name="the-xamlservices-class"></a>XamlServices クラス  
 常に XAML ノード ストリームを処理するために必要です Api を使用する場合は、基本的な読み込みパスまたは保存パスの基本的な場合は、<xref:System.Xaml.XamlServices>クラスです。  
  
-   さまざまなシグニチャ<xref:System.Xaml.XamlServices.Load%2A>読み込みパスの実装です。 ファイルまたはストリームを読み込むことができますか、または、読み込むことができます、 <xref:System.Xml.XmlReader>、<xref:System.IO.TextReader>または<xref:System.Xaml.XamlReader>そのリーダーの Api を使用して読み込むによって、XAML 入力をラップします。  
  
-   さまざまなシグニチャ<xref:System.Xaml.XamlServices.Save%2A>オブジェクト グラフを保存し、出力をストリームとして生成されるファイル、または<xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter>インスタンス。  
  
-   <xref:System.Xaml.XamlServices.Transform%2A>XAML を変換、読み込みパスと保存をリンクして単一の操作としてのパス。 異なるスキーマ コンテキストまたは異なるバッキング型システムを使用でした<xref:System.Xaml.XamlReader>と<xref:System.Xaml.XamlWriter>、これは、生成される XAML がどのように変換される新機能に影響します。  
  
 使用する方法の詳細についての<xref:System.Xaml.XamlServices>を参照してください[XAMLServices クラスおよび基本的な XAML の読み取りまたは書き込み](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md)です。  
  
## <a name="xaml-type-system"></a>XAML 型システム  
 XAML 型システムでは、XAML ノード ストリームの特定の各ノードを使用するために必要な Api を提供します。  
  
 <xref:System.Xaml.XamlType>開始オブジェクト ノードと end のオブジェクト ノード間で処理しているを使用するオブジェクトの表現です。  
  
 <xref:System.Xaml.XamlMember>メンバー ノードの開始と終了メンバー ノードの間で処理しているを使用するオブジェクトのメンバーの表現です。  
  
 などの Api<xref:System.Xaml.XamlType.GetAllMembers%2A>と<xref:System.Xaml.XamlType.GetMember%2A>と<xref:System.Xaml.XamlMember.DeclaringType%2A>間の関係をレポート、<xref:System.Xaml.XamlType>と<xref:System.Xaml.XamlMember>です。  
  
 .NET Framework XAML サービスによって実装される XAML 型システムの既定の動作をリフレクションを使用して、共通言語ランタイム (CLR) とアセンブリの CLR 型の静的分析に基づきます。 そのため、特定の CLR 型の XAML 型システムの既定の実装を型とそのメンバーの XAML スキーマを公開でき XAML 型システムの観点からレポートできます。 既定の XAML 型システムでの型の割り当ての概念は CLR の継承に対応しているし、インスタンス、値型の概念がサポートする動作と CLR の機能にもマップされます。  
  
## <a name="reference-for-xaml-language-features"></a>XAML 言語機能のリファレンス  
 XAML をサポートするためには、.NET Framework XAML サービスは、XAML 言語の XAML 名前空間に定義されている XAML 言語の概念の特定の実装を提供します。 これらは、特定のリファレンス ページとして記載されています。 XAML リーダーまたは .NET Framework XAML サービスで定義されている XAML ライターによって処理されるときに、これらの言語機能がどのように動作するかの観点からは、言語の機能が記載されています。 詳細については、「 [XAML Namespace (x:) Language Features](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)」を参照してください。
