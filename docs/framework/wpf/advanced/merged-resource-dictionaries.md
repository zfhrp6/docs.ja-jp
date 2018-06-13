---
title: マージされたリソース ディクショナリ
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: f2dc5bbb96d74533e8e77251185a0b105fc55746
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548055"
---
# <a name="merged-resource-dictionaries"></a>マージされたリソース ディクショナリ
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] リソースでは、マージされたリソース ディクショナリ機能がサポートされます。 この機能を使用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのリソース部分を、コンパイル済み [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] アプリケーションの外部で定義できます。 その後、リソースをアプリケーション間で共有できます。また、ローカライズ用に簡単に切り分けることができます。  
  
## <a name="introducing-a-merged-resource-dictionary"></a>マージされたリソース ディクショナリの導入  
 マークアップでは、マージされたリソース ディクショナリをページに導入するために次の構文を使います。  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 なお、<xref:System.Windows.ResourceDictionary>要素がありません、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)、一般に、リソース コレクションのすべてのアイテムに必要なです。 別<xref:System.Windows.ResourceDictionary>内で参照、<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクションは特別な場合は、このシナリオでマージされたリソース ディクショナリに予約されています。 <xref:System.Windows.ResourceDictionary>マージを導入するリソース ディクショナリを持つことはできません、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)です。 通常、各<xref:System.Windows.ResourceDictionary>内で、<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクションを指定します、<xref:System.Windows.ResourceDictionary.Source%2A>属性。 値<xref:System.Windows.ResourceDictionary.Source%2A>する必要があります、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]マージするリソース ファイルの場所に解決されます。 その送信先[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]別にする必要があります[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルで<xref:System.Windows.ResourceDictionary>のルート要素として。  
  
> [!NOTE]
>  内のリソースを定義することは、<xref:System.Windows.ResourceDictionary>かを指定する代わりに、マージされたディクショナリとして指定されている<xref:System.Windows.ResourceDictionary.Source%2A>、またはネイティブ コードに加えて、指定したソースからどのようなリソースが含まれます。 ただし、これは一般的なシナリオではありません。マージされたディクショナリの主要なシナリオは、外部ファイルの場所からリソースをマージすることです。 ページのマークアップ内のリソースを指定する場合は、定義するようにしてこれらのメイン<xref:System.Windows.ResourceDictionary>マージされたディクショナリではなく、します。  
  
## <a name="merged-dictionary-behavior"></a>マージされたディクショナリの動作  
 マージされたディクショナリ内のリソースは、それらのリソースがマージされる先のメイン リソース ディクショナリのスコープの直後のリソース参照スコープの場所全体を占めます。 リソース キーは個々のディクショナリ内で一意である必要がありますが、マージされたディクショナリのセット内に 1 つのキーが複数回存在してもかまいません。 この場合、返されるリソースは、最後のディクショナリで順が見つかりませんでしたから得られます、<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクション。 場合、<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>でコレクションが定義されている[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップで提供される、コレクション内でマージされたディクショナリの順序は、要素の順序。 プライマリ ディクショナリ内とマージされたディクショナリ内の両方でキーが定義されている場合、返されるリソースはプライマリ ディクショナリから取られます。 これらのスコープ規則は、静的なリソース参照と動的なリソース参照の両方に等しく適用されます。  
  
### <a name="merged-dictionaries-and-code"></a>マージされたディクショナリとコード  
 マージされたディクショナリは、コードを使って `Resources` ディクショナリに追加できます。 既定値、最初は空<xref:System.Windows.ResourceDictionary>のいずれかに存在する`Resources`プロパティが既定では、最初は空にも<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクション プロパティです。 目的のプライマリへの参照を取得するコードをマージされたディクショナリを追加する<xref:System.Windows.ResourceDictionary>、取得、<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>プロパティの値、および呼び出し`Add`、汎用`Collection`に含まれる<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>です。 新しいオブジェクトを追加する必要があります<xref:System.Windows.ResourceDictionary>です。 コードでは、設定しない、<xref:System.Windows.ResourceDictionary.Source%2A>プロパティです。 代わりに、取得する必要があります、<xref:System.Windows.ResourceDictionary>によって 1 つを作成するか、1 つを読み込むオブジェクト。 読み込む既存の 1 つの方法<xref:System.Windows.ResourceDictionary>を呼び出す<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>、既存の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル ストリームを持つ、<xref:System.Windows.ResourceDictionary>キャストし、ルート、<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>に値を返す<xref:System.Windows.ResourceDictionary>です。  
  
### <a name="merged-resource-dictionary-uris"></a>マージされたリソース ディクショナリの URI  
 マージされたリソース ディクショナリを組み込むには、いくつかの手法があります。マージされたリソース ディクショナリは、お使いの [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 形式で示されます。 大まかに言えば、これらの手法は 2 つのカテゴリに分類できます。プロジェクトの一部としてコンパイルされるリソースと、プロジェクトの一部としてコンパイルされないリソースです。  
  
 プロジェクトの一部としてコンパイルされるリソースの場合は、リソースの場所を参照する相対パスを使うことができます。 相対パスは、コンパイル中に評価されます。 リソースは、リソースのビルド アクションでプロジェクトの一部として定義する必要があります。 リソースの .xaml ファイルをリソースとしてプロジェクトに組み込む場合は、リソース ファイルを出力ディレクトリにコピーする必要がありません。リソースは、コンパイルされたアプリケーション内にあらかじめ組み込まれます。 コンテンツのビルド アクションを使うこともできますが、その場合は、ファイルを出力ディレクトリにコピーして、実行可能ファイルに対して同じパスにリソース ファイルを配置する必要があります。  
  
> [!NOTE]
>  埋め込みリソースのビルド アクションは使用しないでください。 ビルド操作自体はサポートされて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、アプリケーションがの解像度<xref:System.Windows.ResourceDictionary.Source%2A>を取り込みません<xref:System.Resources.ResourceManager>、し、そのため、ストリームから個々 のリソースを分割することはできません。 引き続き使用できます埋め込まれたリソースも使用する限り、その他の目的で<xref:System.Resources.ResourceManager>のリソースにアクセスします。  
  
 これと関連して、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルに対するパック URI を使い、その URI をソースとして参照する手法もあります。 パック URI を使用すると、参照したアセンブリのコンポーネントを参照したり、その他の手法を利用したりできます。 パック URI の詳細については、「[WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)」を参照してください。  
  
 プロジェクトの一部としてコンパイルされないリソースでは、URI が実行時に評価されます。 リソース ファイルを参照するために、file: や http: などの一般的な URI トランスポートを使うことができます。 コンパイルされないリソースの手法を使うことの欠点は、file: アクセスには追加の配置手順が必要になることと、http: アクセスはインターネット セキュリティ ゾーンを意味することです。  
  
### <a name="reusing-merged-dictionaries"></a>マージされたディクショナリの再利用  
 マージするリソース ディクショナリは、すべての有効な [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] を使って参照できるため、マージされたリソース ディクショナリをアプリケーション間で再利用または共有することができます。 これを行うための具体的な方法は、アプリケーションの配置方法と、採用するアプリケーション モデルによって異なります。 前述のパック URI の手法を使うと、開発中にアセンブリ参照を共有することにより、マージされたリソースを複数のプロジェクトから取得する一般的な方法を利用することができます。 このシナリオでは、リソースはまだクライアントによって配布されるため、少なくとも 1 つのアプリケーションで参照先のアセンブリを配置する必要があります。 また、http プロトコルを使う分散 URI によって、マージされたリソースを参照することもできます。  
  
 マージされたディクショナリ/アプリケーションの配置で考えられる別のシナリオは、マージされたディクショナリをローカル アプリケーション ファイルとして、またはローカルの共有記憶域に書き出すことです。  
  
### <a name="localization"></a>ローカリゼーション  
 ローカライズする必要のあるリソースが、プライマリ ディクショナリにマージされたディクショナリに分離されて、Loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルとして保持されている場合、これらのファイルを別個にローカライズすることができます。 これは、サテライト リソース アセンブリをローカライズするよりも簡易な手法です。 詳細については、「[WPF のグローバリゼーションおよびローカリゼーションの概要](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.ResourceDictionary>  
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [リソースとコード](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
