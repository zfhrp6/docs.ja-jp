---
title: "マージされたリソース ディクショナリ | Microsoft Docs"
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
  - "マージされたリソース ディクショナリ"
  - "マージされたリソース ディクショナリ"
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# マージされたリソース ディクショナリ
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]リソースでは、マージされたリソース ディクショナリ機能をサポートします。 この機能の resources の部分を定義する方法を提供する、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、コンパイル済みの外部でアプリケーション[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アプリケーションです。 アプリケーション間でリソースを共有することができますしもより簡単に分離ローカリゼーション用です。  
  
## <a name="introducing-a-merged-resource-dictionary"></a>マージされたリソース ディクショナリの概要  
 マークアップでは、次の構文を使用して、ページにマージされたリソース ディクショナリを導入します。  
  
 [!code-xml[ResourceMergeDictionary#MergedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 注意してください、 <xref:System.Windows.ResourceDictionary>要素がありません、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)が、一般に必要なリソース コレクション内のすべての項目。 なく他<xref:System.Windows.ResourceDictionary>内を参照、 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクションは特別な場合は、このマージされたリソース ディクショナリのシナリオ用に予約されています。 <xref:System.Windows.ResourceDictionary>マージを導入するリソース ディクショナリを使用できない、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)します。 通常、各<xref:System.Windows.ResourceDictionary>内で、 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクションの指定、<xref:System.Windows.ResourceDictionary.Source%2A>属性です。 値<xref:System.Windows.ResourceDictionary.Source%2A>する必要があります、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]マージするリソース ファイルの場所を解決します。 保存先[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]別にする必要があります[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルと<xref:System.Windows.ResourceDictionary>ルート要素です。  
  
> [!NOTE]
>  内のリソースを定義することは、 <xref:System.Windows.ResourceDictionary>のいずれかを指定する代わりとして、マージされたディクショナリとして指定されている<xref:System.Windows.ResourceDictionary.Source%2A>、またはネイティブ コードに加えて、指定されたソースからすべてのリソースが含まれています。 ただし、これは一般的なシナリオマージされたディクショナリの主なシナリオでは、外部ファイルの場所からリソースをマージします。 ページのマークアップ内のリソースを指定する場合は、する必要があります通常これら定義のメイン<xref:System.Windows.ResourceDictionary>マージされたディクショナリではなく。  
  
## <a name="merged-dictionary-behavior"></a>マージされたディクショナリの動作  
 マージされたディクショナリ内のリソースは、直後にマージされますメイン リソース ディクショナリのスコープには、リソースの検索スコープ内の位置を占有します。 リソース キーは、個々 のディクショナリ内で一意であるが、キーは、マージされたディクショナリのセットに複数回を配置できます。 返されるリソースは最後のディクショナリで順が見つかりませんでしたから取得する場合は、 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクションです。 場合、 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクションが定義された[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップで提供されているため、マージされたディクショナリ コレクション内の順序は、要素の順序。 キーは、プライマリ辞書およびマージされたディクショナリに定義されているが場合、返されるリソースは、プライマリ ディクショナリから取得されます。 これらのスコープ規則に同じように適用静的リソース参照と動的なリソースの両方の参照。  
  
### <a name="merged-dictionaries-and-code"></a>マージされたディクショナリとコード  
 マージされたディクショナリに追加できる、`Resources`ディクショナリをコードします。 既定値、最初は空<xref:System.Windows.ResourceDictionary>のいずれかに存在する`Resources`プロパティにも既定では、最初は空<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクション プロパティです。 コードをマージされたディクショナリを追加するには、目的のプライマリへの参照を取得<xref:System.Windows.ResourceDictionary>、取得、 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>プロパティの値、および呼び出し`Add`のジェネリック`Collection`に格納されている<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>します。 新しいオブジェクトを追加する必要があります<xref:System.Windows.ResourceDictionary>します。 コードでは、設定しない、<xref:System.Windows.ResourceDictionary.Source%2A>プロパティです。 代わりに、取得する必要があります、 <xref:System.Windows.ResourceDictionary>をいずれか&1; つを作成するか、読み込むオブジェクト。 既存のロードに&1; つの方法<xref:System.Windows.ResourceDictionary>を呼び出す<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=fullName> 、既存の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル ストリームを持つ、 <xref:System.Windows.ResourceDictionary>キャストし、ルート、 <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=fullName>に値を返す<xref:System.Windows.ResourceDictionary>します。  
  
### <a name="merged-resource-dictionary-uris"></a>マージされたリソース ディクショナリの Uri  
 示される、マージされたリソース ディクショナリをインクルードする方法のいくつかの手法がある、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]が使用する形式。 大まかに言えば、これらの手法に分類できます&2; つのカテゴリ: リソース、プロジェクトの一部としてコンパイルされますと、プロジェクトの一部としてコンパイルされません。  
  
 リソースについては、プロジェクトの一部としてコンパイルされるリソースの場所を参照する相対パスを使用することができます。 相対パスは、コンパイル時に評価されます。 リソースは、ビルド アクションがリソースとしてプロジェクトの一部として定義する必要があります。 リソースとしてプロジェクトにリソースの .xaml ファイルを含める場合リソース ファイルを出力ディレクトリにコピーする必要はありません、リソースが、コンパイルされたアプリケーション内に含まれています。 コンテンツのビルド アクションを使用することもできますが、出力ディレクトリにファイルをコピーし、実行可能ファイルにも同じパスのリレーションシップのリソース ファイルを展開する必要があります。  
  
> [!NOTE]
>  埋め込まれたリソースのビルド アクションを使用しないでください。 ビルド アクション自体はサポートされて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、アプリケーションがの解像度<xref:System.Windows.ResourceDictionary.Source%2A>取り込みません<xref:System.Resources.ResourceManager>、し、そのため、ストリームから個々 のリソースを分離することはできません。 その他の目的でも使用される限り、埋め込まれたリソースを引き続き使用できます<xref:System.Resources.ResourceManager>リソースにアクセスします。  
  
 関連する手法は、パック URI を使用する、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルを開き、ソースとしてそれを参照してください。 パック URI には、参照アセンブリおよびその他の手法のコンポーネントへの参照ができるようにします。 パッケージの Uri の詳細については、次を参照してください。 [WPF アプリケーションのリソース、コンテンツ、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)します。  
  
 プロジェクトの一部としてコンパイルされないリソースの URI は実行時に評価されます。 ファイルなど、共通の URI トランスポートを使用することができます。 または http: リソース ファイルを参照します。 コンパイルされないリソース方法を使用する欠点は、そのファイル: その他の展開手順、および http アクセスが必要です: へのアクセスは、インターネット セキュリティ ゾーンを意味します。  
  
### <a name="reusing-merged-dictionaries"></a>マージされたディクショナリを再利用します。  
 再利用したりを通じて参照できるリソース ディクショナリをマージするために、アプリケーション間でマージされたリソース ディクショナリを共有できる有効な[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]です。 この方法は、アプリケーションの展開戦略に依存しているアプリケーション モデルと正確に従います。 前述の Pack URI の方法でソースとしてマージされたリソースの複数のプロジェクト間で開発中にアセンブリ参照を共有することによってする手段を提供します。 このシナリオでは、リソースはまだ、クライアントによって配布され、少なくとも&1; つのアプリケーションの参照先アセンブリを展開する必要があります。 Http プロトコルを使用して配布 URI によってマージされたリソースを参照することもできます。  
  
 ローカル アプリケーションは、ファイルや、ローカルの共有記憶域にもう&1; つの可能なマージされたディクショナリは、マージされたディクショナリを作成/アプリケーション展開シナリオです。  
  
### <a name="localization"></a>ローカリゼーション  
 リソースをローカライズする必要がある場合はプライマリ ディクショナリにマージされ、緩やかな保持されているディクショナリに分離して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、これらのファイルを個別にローカライズすることができます。 この手法は、サテライト リソース アセンブリをローカライズする代わりに軽量です。 詳細については、「 [WPF のグローバリゼーションおよびローカリゼーションの概要](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.ResourceDictionary>   
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [リソースとコード](../../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [WPF アプリケーションのリソース、コンテンツ、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)