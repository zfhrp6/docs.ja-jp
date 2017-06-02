---
title: "ドキュメントのシリアル化および保存 | Microsoft Docs"
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
  - "ドキュメント, シリアル化"
  - "ドキュメント, storage"
  - "シリアル化 (ドキュメントの)"
  - "保存 (ドキュメントを)"
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# ドキュメントのシリアル化および保存
[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] は、高品質なドキュメントを作成および表示するための強力な環境を提供します。  固定ドキュメントとフロー ドキュメントの両方をサポートする拡張機能、高度な表示コントロール、および 2D や 3D の強力なグラフィックス機能を組み合わせることにより、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] アプリケーションの品質とユーザー エクスペリエンスをさらに向上させることができます。  ドキュメントのメモリ内表現を柔軟に管理するための機能は [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] の重要な機能の 1 つであり、データ ストアからドキュメントを効率的に保存して読み込むための機能はほとんどのアプリケーションで必要になります。  内部のメモリ内表現から外部のデータ ストアにドキュメントを変換するプロセスは、[シリアル化](GTMT)と呼ばれます。  データ ストアを読み込んで元のメモリ内インスタンスを再作成する逆のプロセスは、逆シリアル化と呼ばれます。  
  
   
  
<a name="AboutSerialization"></a>   
## ドキュメントのシリアル化について  
 理想的には、メモリ内のドキュメントを[シリアル化](GTMT)および逆シリアル化してメモリに戻すプロセスは、アプリケーションから透過的に実行されます。  アプリケーションは、シリアライザーの "write" メソッドを呼び出してドキュメントを保存します。一方、デシリアライザーの "read" メソッドは、データ ストアにアクセスして元のインスタンスをメモリ内に再作成します。  シリアル化および逆シリアル化によってドキュメントが元の形式に再作成される限り、通常、データの特定の保存形式はアプリケーションにとって重要ではありません。  
  
 多くのアプリケーションには複数のシリアル化オプションが用意されています。これは、ドキュメントを異なるメディアや異なる形式に保存できるようにするためです。  たとえば、ディスク ファイル、データベース、または Web サービスにドキュメントを保存するための "名前を付けて保存" オプションがアプリケーションに用意されていることがあります。  同様に、複数のシリアライザーを使用することで、HTML、RTF、XML、XPS などさまざまな形式でドキュメントを保存できます。また、サードパーティの形式に保存することもできます。  シリアル化は、アプリケーションに対し、ストレージ メディアの詳細を各シリアライザーの実装内に分離するインターフェイスを定義します。  [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] <xref:System.Windows.Documents.Serialization> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] には、ストレージ詳細のカプセル化という利点に加えて、いくつかの重要な機能が用意されています。  
  
### .NET Framework 3.0 ドキュメント シリアライザーの機能  
  
-   高レベルのドキュメント オブジェクト \([論理ツリー](GTMT)およびビジュアル\) への直接アクセス。この機能により、自動修正されたコンテンツ、2D\/3D 要素、イメージ、メディア、ハイパーリンク、注釈、およびその他のサポート コンテンツを効率的に保存できます。  
  
-   [同期](GTMT)操作と[非同期](GTMT)操作。  
  
-   次の拡張機能を持つプラグイン シリアライザーのサポート。  
  
    -   すべての [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] アプリケーションで使用される、システム全体へのアクセス。  
  
    -   アプリケーション プラグインの簡単な検出。  
  
    -   サードパーティのカスタム プラグインの簡単な配置、インストール、および更新。  
  
    -   ランタイム設定およびオプションをカスタマイズするためのユーザー インターフェイス サポート。  
  
### XPS 印刷パス  
 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 印刷パスもまた、印刷出力を介してドキュメントを書き込むための拡張性の高い機能を提供します。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] は、ドキュメントのファイル形式および [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] のネイティブな印刷スプール形式として使用されます。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ドキュメントは、[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 互換プリンターに直接送信できます。中間形式に変換する必要はありません。  印刷パスの出力オプションおよび機能の詳細については、「[印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)」を参照してください。  
  
<a name="PluginSerializers"></a>   
## プラグイン シリアライザー  
 <xref:System.Windows.Documents.Serialization> API は、プラグイン シリアライザーとリンクされたシリアライザーの両方をサポートします。これらのシリアライザーは、アプリケーションから別々にインストールされ、実行時にバインドされます。これらのシリアライザーにアクセスする際には、<xref:System.Windows.Documents.Serialization.SerializerProvider> の検出機構が使用されます。  プラグイン シリアライザーには、配置およびシステム全体での使用を容易にするための拡張機能が用意されています。  リンクされたシリアライザーは、プラグイン シリアライザーにアクセスできない [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] などの[部分信頼](GTMT)環境にも実装できます。  リンクされたシリアライザーは、<xref:System.Windows.Documents.Serialization.SerializerWriter> クラスの派生実装に基づいており、アプリケーション内に直接コンパイルおよびリンクされます。  プラグイン シリアライザーとリンクされたシリアライザーは、同一のパブリック メソッドおよびイベントを介して動作します。これにより、いずれかまたは両方のシリアライザーを同じアプリケーション内で容易に使用することができます。  
  
 プラグイン シリアライザーは、新しいストレージ設計およびファイル形式に拡張機能を提供します。これにより、ビルド時に使用される可能性があるすべての形式に対してコードを直接記述する必要がなくなるため、アプリケーション開発者の負担が軽減されます。  また、プラグイン シリアライザーでは、カスタム ファイル形式または専用のファイル形式のためのシステム アクセス可能なプラグインを標準的な方法で配置、インストール、および更新できます。これにより、サードパーティの開発者の負担も軽減されます。  
  
### プラグイン シリアライザーの使用  
 プラグイン シリアライザーは簡単に使用できます。  <xref:System.Windows.Documents.Serialization.SerializerProvider> クラスは、システムにインストールされている各プラグインの <xref:System.Windows.Documents.Serialization.SerializerDescriptor> オブジェクトを列挙します。  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> プロパティは、現在の構成に基づいてインストール済みのプラグインをフィルター処理し、アプリケーションによるシリアライザーの読み込みおよび使用が可能であるかどうかを検証します。  <xref:System.Windows.Documents.Serialization.SerializerDescriptor> は、<xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> や <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A> などその他のプロパティも提供します。アプリケーションは、これらのプロパティを使用して、使用可能な出力形式のシリアライザーの選択をユーザーに求めることができます。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] の既定のプラグイン シリアライザーは [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] によって提供されます。このシリアライザーは必ず列挙されます。  ユーザーが出力形式を選択したら、<xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> メソッドを使用してその形式に対応する <xref:System.Windows.Documents.Serialization.SerializerWriter> を作成します。  次に、<xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> メソッドを呼び出して、ドキュメント ストリームをデータ ストアに出力できます。  
  
 "PlugInFileFilter" プロパティ内で <xref:System.Windows.Documents.Serialization.SerializerProvider> メソッドを使用するアプリケーションの例を次に示します。  PlugInFileFilter は、インストール済みのプラグインを列挙し、使用可能なファイル オプションを使用してフィルター文字列を作成します。このフィルター文字列は <xref:Microsoft.Win32.SaveFileDialog> で使用されます。  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 ユーザーが出力ファイル名を選択した後、<xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> メソッドを使用して、指定したドキュメントを指定した形式で保存する例を次に示します。  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### プラグイン シリアライザーのインストール  
 <xref:System.Windows.Documents.Serialization.SerializerProvider> クラスは、プラグイン シリアライザーの検出およびアクセスに使用される、上位レベルのアプリケーション インターフェイスを提供します。  <xref:System.Windows.Documents.Serialization.SerializerProvider> は、システムにインストールされているアクセスできるシリアライザーを検索し、その一覧をアプリケーションに提供します。  インストール済みのシリアライザーの詳細は、レジストリ設定で定義されます。  <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> メソッドを使用すると、プラグイン シリアライザーをレジストリに追加することができます。[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がまだインストールされていない場合は、プラグインのインストール スクリプトでレジストリの値を直接設定できます。  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> メソッドを使用すると、以前にインストールされたプラグインを削除できます。アンインストール スクリプトでレジストリ設定をリセットすることもできます。  
  
### プラグイン シリアライザーの作成  
 プラグイン シリアライザーとリンクされたシリアライザーは、公開されている同一のパブリック メソッドおよびイベントを使用します。また、同様の方法で[同期的](GTMT)または[非同期的](GTMT)に動作するように設計できます。  プラグイン シリアライザーを作成する場合、通常は次の 3 つの基本手順に従います。  
  
1.  まず、リンクされたシリアライザーとしてシリアライザーを実装およびデバッグします。  最初にテスト アプリケーション内でシリアライザーを直接コンパイルおよびリンクして作成すると、ブレークポイントや、テストに役立つその他のデバッグ サービスへの完全なアクセスが提供されます。  
  
2.  シリアライザーのテストが完了したら、<xref:System.Windows.Documents.Serialization.ISerializerFactory> インターフェイスを追加してプラグインを作成します。  <xref:System.Windows.Documents.Serialization.ISerializerFactory> インターフェイスにより、論理ツリー、<xref:System.Windows.UIElement> オブジェクト、<xref:System.Windows.Documents.IDocumentPaginatorSource>、<xref:System.Windows.Media.Visual> 要素などすべての [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] オブジェクトへのフル アクセスが可能になります。  さらに、<xref:System.Windows.Documents.Serialization.ISerializerFactory> は、リンクされたシリアライザーによって使用される同一の同期および非同期のメソッドとイベントを提供します。  サイズの大きいドキュメントは出力に時間がかかる場合があるので、ユーザー操作の応答性を維持するために非同期操作を使用するようお勧めします。また、データ ストアに問題が発生した場合に備えて "キャンセル" オプションを用意してください。  
  
3.  プラグイン シリアライザーを作成したら、プラグインの配布、インストール、およびアンインストールのためのインストール スクリプトを実装します \(前の「[プラグイン シリアライザーのインストール](#InstallingPluginSerializers)」を参照してください\)。  
  
## 参照  
 <xref:System.Windows.Documents.Serialization>   
 <xref:System.Windows.Xps.XpsDocumentWriter>   
 <xref:System.Windows.Xps.Packaging.XpsDocument>   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [XML Paper Specification: 概要](http://go.microsoft.com/fwlink?LinkID=106246)