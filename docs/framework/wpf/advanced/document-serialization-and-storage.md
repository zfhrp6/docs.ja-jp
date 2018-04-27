---
title: ドキュメントのシリアル化および保存
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e65a20323e3797d6d56ac7941e4ac9aeeb0ed473
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="document-serialization-and-storage"></a>ドキュメントのシリアル化および保存
Microsoft .NET Framework では、作成および高品質のドキュメントを表示するための強力な環境を提供します。  固定ドキュメントとフロー ドキュメントの両方および高度な表示コントロールをサポートし、強力な 2D および 3D グラフィックス機能と組み合わされた拡張機能により、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] アプリケーションの品質とユーザー エクスペリエンスは新しいレベルになります。  ドキュメントのメモリ内の表現を柔軟に管理できることは [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] の重要な機能であり、ほぼすべてのアプリケーションではデータ ストアのドキュメントを効率的に保存および読み込むことができる必要があります。  内部のメモリ内表現から外部のデータ ストアにドキュメントを変換するプロセスは、シリアル化と呼ばれます。  データ ストアを読み取って元のメモリ内インスタンスを再作成する逆のプロセスは、逆シリアル化と呼ばれます。  
  
 
  
<a name="AboutSerialization"></a>   
## <a name="about-document-serialization"></a>ドキュメントのシリアル化について  
 ドキュメントをメモリからシリアル化し、後で逆シリアル化してメモリに戻すプロセスは、アプリケーションに対して透過的に行われるのが理想的です。  アプリケーションは、シリアライザーの "書き込み" メソッドを呼び出してドキュメントを保存します。デシリアライザーの "読み取り" メソッドは、データ ストアにアクセスし、メモリ内の元のインスタンスを再作成します。  通常、シリアル化と逆シリアル化のプロセスで元の形式のドキュメントが再作成される限り、データが格納される特定の形式はアプリケーションにとって問題ではありません。  
  
 多くの場合、アプリケーションでは複数のシリアル化オプションが提供され、ユーザーは異なるメディアまたは異なる形式にドキュメントを保存できます。  たとえば、[名前を付けて保存] オプションでは、ドキュメントをディスク ファイル、データベース、Web サービスなどに保存できる場合があります。  同様に、別のシリアライザーでは、HTML、RTF、XML、XPS、サード パーティ形式などのさまざまな形式でドキュメントを格納できます。  アプリケーションに対して、シリアル化により、実装内のストレージ メディアの詳細を分離するインターフェイスが定義されます。  記憶域の詳細をカプセル化の利点に加え、 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] <xref:System.Windows.Documents.Serialization> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]他のいくつかの重要な機能を提供します。  
  
### <a name="features-of-net-framework-30-document-serializers"></a>.NET Framework 3.0 ドキュメント シリアライザーの機能  
  
-   上位レベルのドキュメント オブジェクト (論理ツリーとビジュアル) に直接アクセスすることにより、ページ分割されたコンテンツ、2D/3D 要素、イメージ、メディア、ハイパーリンク、注釈、およびその他のサポート コンテンツの効率的な保存が可能になります。  
  
-   同期操作と非同期操作。  
  
-   拡張機能でのプラグイン シリアライザーのサポート:  
  
    -   すべての [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] アプリケーションで使用するためのシステム全体のアクセス。  
  
    -   簡単なアプリケーション プラグインの検出。  
  
    -   カスタム サードパーティ プラグインの簡単な展開、インストール、更新。  
  
    -   カスタム実行時設定とオプションのユーザー インターフェイス サポート。  
  
### <a name="xps-print-path"></a>XPS 印刷パス  
 Microsoft .NET Framework[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]印刷パスには、印刷出力を使用したドキュメントを書き込むために拡張可能機構も用意されています。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] は、ドキュメント ファイル形式と、[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] のネイティブ印刷スプール形式の両方として機能します。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] のドキュメントは [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 互換性のあるプリンターに直接送信でき、中間形式に変換する必要はありません。  印刷パス出力オプションと機能について詳しくは、「[印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)」をご覧ください。  
  
<a name="PluginSerializers"></a>   
## <a name="plug-in-serializers"></a>プラグイン シリアライザー  
 <xref:System.Windows.Documents.Serialization> Api は、プラグイン シリアライザーと、アプリケーションから個別にインストールされているリンクされたシリアライザーの両方のサポートを提供し、実行時に、バインドを使用してアクセス、<xref:System.Windows.Documents.Serialization.SerializerProvider>探索メカニズムです。  プラグイン シリアライザーには、簡単に展開でき、システム全体で使用できるという大きな利点があります。  プラグイン シリアライザーにアクセスできない [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] などの部分信頼環境には、リンクされたシリアライザーを実装することもできます。  派生の実装に基づいているシリアライザーのリンク、<xref:System.Windows.Documents.Serialization.SerializerWriter>クラス、コンパイルされ、アプリケーションに直接リンクされています。  プラグイン シリアライザーとリンクされたシリアライザーはどちらも同じパブリック メソッドとイベントを通じて動作するので、同じアプリケーションでどちらか一方でも両方のシリアライザーでも簡単に使うことができます。  
  
 アプリケーション開発者にとっての利点として、プラグイン シリアライザーは新しいストレージ設計およびファイル形式に対する拡張性を備え、ビルド時に可能性のあるすべての形式を直接コーディングする必要はありません。  また、サードパーティの開発者にとっても、プラグイン シリアライザーには、カスタムまたは独自のファイル形式のためのシステムでアクセス可能なプラグインを展開、インストール、更新する標準化された手段が提供されるというメリットがあります。  
  
### <a name="using-a-plug-in-serializer"></a>プラグイン シリアライザーの使用  
 プラグイン シリアライザーは簡単に使うことができます。  <xref:System.Windows.Documents.Serialization.SerializerProvider>クラスを列挙、<xref:System.Windows.Documents.Serialization.SerializerDescriptor>システムにインストールされている各プラグインのオブジェクトします。  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A>プロパティは、現在の構成に基づいたインストール済みのプラグインをフィルター処理し、シリアライザーの読み込まれ、アプリケーションで使用されることを確認します。  <xref:System.Windows.Documents.Serialization.SerializerDescriptor>などその他のプロパティの提供も<xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A>と<xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>、使用可能な出力形式のシリアライザーの選択にユーザー入力を求める、アプリケーションが使用できます。  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 用の既定のプラグイン シリアライザーは [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] で提供され、常に列挙されます。  ユーザーが、出力形式を選択した後、<xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A>メソッドの使用を作成、<xref:System.Windows.Documents.Serialization.SerializerWriter>の特定の形式です。  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> データ ストアにドキュメント ストリームを出力するメソッドを呼び出すことができます。  
  
 次の例では、使用するアプリケーションを<xref:System.Windows.Documents.Serialization.SerializerProvider>"PlugInFileFilter"プロパティのメソッドです。  PlugInFileFilter がインストールされているプラグインを列挙しの使用可能なファイルのオプションのフィルター文字列を構築、<xref:Microsoft.Win32.SaveFileDialog>です。  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 出力ファイル名がユーザーによって選択された後、次の例の使用、<xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A>指定の形式で、特定のドキュメントを格納する方法です。  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### <a name="installing-plug-in-serializers"></a>プラグイン シリアライザーのインストール  
 <xref:System.Windows.Documents.Serialization.SerializerProvider>クラスは、プラグイン シリアライザー探索およびアクセスの上位レベルのアプリケーション インターフェイスを提供します。  <xref:System.Windows.Documents.Serialization.SerializerProvider> 検索し、アプリケーションがインストールされ、システム上でアクセスするシリアライザーの一覧を示します。  インストールされているシリアライザーの詳細は、レジストリ設定によって定義されます。  プラグイン シリアライザーを使用して、レジストリに追加されることができます、<xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A>メソッド場合[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]がまだないインストールの場合は、一連のレジストリ値自体直接、プラグインのインストール スクリプトになります。  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A>以前にインストールを削除するメソッドを使用できるプラグイン、レジストリ設定は、アンインストール スクリプトによって同様にリセットすることもできます。  
  
### <a name="creating-a-plug-in-serializer"></a>プラグイン シリアライザーの作成  
 プラグイン シリアライザーとリンクされたシリアライザーはどちらも、同じ公開されたパブリック メソッドとイベントを使い、同期または非同期で動作するように同じように設計できます。  通常、プラグイン シリアライザーの作成には 3 つの基本的な手順があります。  
  
1.  最初に、シリアライザーをリンクされたシリアライザーとして実装してデバッグします。  コンパイルしてテスト アプリケーションに直接リンクするシリアライザーを最初に作成すると、テストに役立つブレークポイントや他のデバッグ サービスに完全にアクセスできます。  
  
2.  シリアライザーを完全にテストした後、<xref:System.Windows.Documents.Serialization.ISerializerFactory>プラグインを作成するインターフェイスを追加します。  <xref:System.Windows.Documents.Serialization.ISerializerFactory>インターフェイスによって、すべてへのフル アクセス[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]論理ツリーを含むオブジェクト<xref:System.Windows.UIElement>オブジェクト、 <xref:System.Windows.Documents.IDocumentPaginatorSource>、および<xref:System.Windows.Media.Visual>要素。  さらに<xref:System.Windows.Documents.Serialization.ISerializerFactory>同じ同期および非同期のメソッドとリンクされたシリアライザーで使用されるイベントを提供します。  サイズの大きいドキュメントの出力には時間がかかる場合があるため、ユーザーの操作に応答できる状態を維持し、データ ストアで問題が発生した場合の "キャンセル" オプションを提供できるよう、非同期操作を使うことをお勧めします。  
  
3.  プラグイン シリアライザーを作成した後、プラグインを配布してインストール (およびアンインストール) するためのインストール スクリプトを実装します (前の「[プラグイン シリアライザーのインストール](#InstallingPluginSerializers)」を参照)。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Documents.Serialization>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [XML Paper Specification: 概要](http://go.microsoft.com/fwlink?LinkID=106246)
