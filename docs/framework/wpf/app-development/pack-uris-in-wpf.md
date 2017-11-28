---
title: "WPF におけるパッケージの URI"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05e13b8fc899b5cc6addb6d41db826f39b7528f0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="pack-uris-in-wpf"></a>WPF におけるパッケージの URI
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]、[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]を特定し、次を含む、さまざまな方法でファイルを読み込むために使用します。  
  
-   指定する、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]を表示するときに、アプリケーションを初めて起動します。  
  
-   イメージの読み込み。  
  
-   ページへの移動。  
  
-   実行可能でないデータ ファイルの読み込み。  
  
 さらに、[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]のため識別し、さまざまな場所、たとえば、次のファイルを読み込むことができます。  
  
-   現在のアセンブリ。  
  
-   参照アセンブリ。  
  
-   アセンブリに対して相対的な位置。  
  
-   アプリケーションの起点サイト。  
  
 指定して、これらの場所からその種類のファイルを読み込むのための一貫性のあるメカニズムを提供する[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の拡張性を活用して、*パック URI スキーム*です。 このトピックでは、スキームの概要を示します、パックを作成する方法について説明[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]さまざまなシナリオ、絶対パスと相対について説明[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]と[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]パックを使用する方法を表示する前に、解決[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]両方マークアップからコード。  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a>パック URI スキーム  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]してスキーマを使用、 [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) (OPC) の仕様は、整理、およびコンテンツを識別するためのモデルについて説明します。 このモデルの主要な要素は、パッケージとパーツ、場所、*パッケージ*は、論理的なコンテナーの 1 つ以上の論理*パーツ*です。 この概念を次の図に示します。  
  
 ![パッケージとパーツのダイアグラム](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")  
  
 部分を識別するため、OPC 仕様は RFC 2396 の拡張性を活用して (Uniform Resource Identifier (URI): 一般構文)、パックを定義する[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキームです。  
  
 指定されているスキーム、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]そのプレフィックスは http、ftp、およびファイルは、よく知られている例を示します。 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキームは、そのスキームとして"pack"を使用し、2 つのコンポーネントが含まれています: 証明機関とパス。 パックの形式は[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
 パック://*機関*/*パス*
  
 *機関*一部に含まれています、パッケージの種類を指定中に、*パス*パッケージ内の部分の場所を指定します。  
  
 この概念を次の図に示します。  
  
 ![パッケージ、オーソリティ、およびパスの関係](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")  
  
 パッケージとパーツは、アプリケーションとファイルに似ています。つまり、アプリケーション (パッケージ) は、次のような 1 つ以上のファイル (パーツ) を含むことができます。  
  
-   ローカル アセンブリにコンパイルされるリソース ファイル。  
  
-   参照センブリにコンパイルされるリソース ファイル。  
  
-   参照元センブリにコンパイルされるリソース ファイル。  
  
-   コンテンツ ファイル。  
  
-   起点サイト ファイル。  
  
 これらの種類のファイルにアクセスする[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]機関の 2 つのサポート: アプリケーション:///および siteoforigin:///です。 application:/// オーソリティは、リソース ファイルやコンテンツ ファイルなど、コンパイル時に既知のアプリケーション データ ファイルを識別します。 siteoforigin:/// オーソリティは、起点サイト ファイルを識別します。 各オーソリティのスコープを次の図に示します。  
  
 ![パック URI のダイアグラム](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  パックの機関コンポーネント[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]が埋め込まれた[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]するパッケージをポイントして、RFC 2396 に準拠する必要があります。 さらに、"/" 文字は "," 文字に置き換える必要があり、"%" や "?" などの予約文字はエスケープする必要があります。 詳細については、OPC を参照してください。  
  
 次のセクションでは、パックを作成する方法を説明する[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]リソース、コンテンツ、およびファイルの元のサイトを識別するため、適切なパスとを組み合わせてこれら 2 つの機関を使用します。  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a>リソース ファイルのパック URI  
 リソース ファイルとして構成されている[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource`項目し、アセンブリにコンパイルされます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]パックの構築をサポートしている[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]はローカルのアセンブリにコンパイルまたはローカル アセンブリから参照されるアセンブリにコンパイルするリソース ファイルの識別に使用できます。  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a>ローカル アセンブリ リソース ファイル  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]次の証明機関とパスのリソースのローカル アセンブリにコンパイルされたファイルを使用します。  
  
-   **オーソリティ**: application:///。  
  
-   **パス**: ローカル アセンブリのプロジェクト フォルダーのルートに対して相対的なパスを含むリソース ファイルの名前。  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローカル アセンブリのプロジェクト フォルダーのルートに配置されているリソース ファイル。  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローカル アセンブリのプロジェクト フォルダーのサブフォルダーに配置されているリソース ファイル。  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a>参照アセンブリ リソース ファイル  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]次機関とパスのリソースの参照アセンブリにコンパイルされたファイルを使用します。  
  
-   **オーソリティ**: application:///。  
  
-   **パス**: 参照アセンブリにコンパイルされるリソース ファイルの名前。 パスは、次の書式に従う必要があります。  
  
     *AssemblyShortName*{*です。バージョン*] {*です。公開鍵*]; component/*パス*  
  
    -   **AssemblyShortName**: 参照アセンブリの短い名前。  
  
    -   **;Version** (省略可能): リソース ファイルを含む参照アセンブリのバージョン。 これは、同じ短い名前を持つ 2 つ以上の参照アセンブリが読み込まれるときに使用されます。  
  
    -   **;PublicKey** (省略可能): 参照アセンブリの署名に使用された公開鍵。 これは、同じ短い名前を持つ 2 つ以上の参照アセンブリが読み込まれるときに使用されます。  
  
    -   **;component**: 参照されるアセンブリが、ローカル アセンブリから参照されることを指定します。  
  
    -   **/Path**: 参照アセンブリのプロジェクト フォルダーのルートに対して相対的なパスを含むリソース ファイルの名前。  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]参照アセンブリのプロジェクト フォルダーのルートに配置されているリソース ファイル。  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]参照アセンブリのプロジェクト フォルダーのサブフォルダーに配置されているリソース ファイル。  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、バージョン固有の参照先アセンブリのプロジェクト フォルダーのルート フォルダーに配置されているリソース ファイル。  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 なお、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]参照アセンブリ リソース ファイルの構文は、アプリケーションでのみ使用できます:///機関です。 たとえば、次はサポートされていません[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]です。  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a>コンテンツ ファイルのパック URI  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]コンテンツ ファイルを使用する、次の証明機関とパス。  
  
-   **オーソリティ**: application:///。  
  
-   **パス**: アプリケーションのメインの実行可能アセンブリのファイル システム位置に対して相対的なパスを含む、コンテンツ ファイルの名前。  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]実行可能アセンブリと同じフォルダーにあるコンテンツ ファイルです。  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コンテンツ ファイルをアプリケーションの実行可能アセンブリに対応するサブフォルダーにあります。  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] コンテンツ ファイルにナビゲートすることはできません。 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキームのみがサポートするナビゲーション[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]が元のサイトにあるファイルです。  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a>起点サイトのパック URI  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]次の証明機関とパスの元のサイトのファイルを使用します。  
  
-   **オーソリティ**: siteoforigin:///。  
  
-   **パス**: 実行可能アセンブリの起動元の位置に対して相対的なパスを含む起点サイト ファイルの名前。  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の元のファイル、実行可能アセンブリの起動元の場所に格納されているサイトです。  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の元のファイル、アプリケーションの実行可能アセンブリの起動元の場所に対応するサブフォルダーに格納されているサイトです。  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a>ページ ファイル  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]として構成されているファイル[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目は、リソース ファイルと同じ方法でアセンブリにコンパイルされます。 その結果、 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page`パックを使用して項目を識別できます[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]のリソース ファイル。  
  
 種類[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]として一般的に構成されているファイル[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目がある、ルート要素として、次のいずれか。  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a>絶対および相対パック URI  
 完全修飾パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、スキーム、権限、および、パスが含まれています、絶対パックと見なされます[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。 開発者は、簡略化バージョンとして[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素が通常相対パッケージに適切な属性を設定することを許可[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、パスのみが含まれます。  
  
 たとえば、次の絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]用ローカル アセンブリ内のリソース ファイル。  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]このリソースを参照するファイルは、次になります。  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  サイト配信元のファイルがアセンブリに関連付けられていないため、これらのみで参照できますを絶対パック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]です。  
  
 既定では、相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]マークアップまたは参照を含むコードの場所を基準としたと見なされます。 パック先頭にバック スラッシュを使用する場合、相対[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]参照がそのアプリケーションのルートを基準としたと見なされます。 たとえば、次のようなプロジェクト構造を考えてみます。  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Page1.xaml が含まれている場合、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を参照する*ルート*\SubFolder\Page2.xaml、参照は、次の相対パックを使用できます[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。  
  
 `Page2.xaml`  
  
 Page1.xaml が含まれている場合、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を参照する*ルート*\Page2.xaml、参照は、次の相対パックを使用できます[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a>パック URI の解決  
 パックの形式[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]パック可能であればにより[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]同じ外観にファイルの種類。 たとえば、次の絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 この絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]ローカル アセンブリのリソース ファイルや、コンテンツ ファイルを参照します。 次の相対パスの場合も同様です[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。  
  
 `/ResourceOrContentFile.xaml`  
  
 判断するための種類はファイルをパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]が参照する[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]解決[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]ローカル アセンブリと次のヒューリスティックを使用してコンテンツ ファイルのリソース ファイルを。  
  
1.  アセンブリ メタデータのプローブ、 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 、パックに一致する属性[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。  
  
2.  場合、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>属性が存在するパックのパス[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]はコンテンツ ファイルを参照します。  
  
3.  場合、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>属性が見つからない場合は、ローカルのアセンブリにコンパイルされるセットのリソース ファイルをプローブします。  
  
4.  場合、パックのパスに一致するリソース ファイル[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]が見つかると、パッケージのパス[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]はリソース ファイルを参照します。  
  
5.  リソースが見つからない場合、内部的に作成された<xref:System.Uri>が無効です。  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]解像度は適用されません[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]には、次を参照してください。  
  
-   参照されたアセンブリ内のコンテンツ ファイル: では、これらのファイル タイプはサポートされていない[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]です。  
  
-   参照されたアセンブリ内の埋め込みファイル:[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]それらを識別する参照アセンブリの両方に名前が含まれるためには、一意と`;component`サフィックス。  
  
-   配信元のファイルのサイト:[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]それらを識別するパックで指定できるファイルのみであるために、固有[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]siteoforigin が含まれている:///機関です。  
  
 パックの 1 つの単純化[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]解決によって、リソースやコンテンツのファイルの場所に依存するコードです。 たとえば、コンテンツ ファイルをパックするように再構成するローカル アセンブリのリソース ファイルがある場合[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、パックを使用するコードも、リソースは同じの[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a>パック URI を使用したプログラミング  
 多く[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]パックで設定できるプロパティを実装するクラス[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]など。  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 これらのプロパティは、マークアップとコードのどちらからでも設定できます。 このセクションでは、両方の基本構造について説明してから、一般的なシナリオの例を示します。  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a>マークアップでのパック URI の使用  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、パックを使用して属性の要素を設定して、マークアップで指定された[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。 例:  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 表 1 は、さまざまな絶対パックを示しています。[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]マークアップで指定することができます。  
  
 表 1: マークアップでの絶対パック URI  
  
|ファイル|絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|リソース ファイル - ローカル アセンブリ|`"pack://application:,,,/ResourceFile.xaml"`|  
|サブフォルダー内のリソース ファイル - ローカル アセンブリ|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|リソース ファイル - 参照アセンブリ|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|参照アセンブリのサブフォルダー内のリソース ファイル|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|バージョン管理された参照アセンブリ内のリソース ファイル|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|コンテンツ ファイル|`"pack://application:,,,/ContentFile.xaml"`|  
|サブフォルダー内のコンテンツ ファイル|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|起点サイト ファイル|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|サブフォルダー内の起点サイト ファイル|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 表 2 は、さまざまな相対パックを示しています。[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]マークアップで指定することができます。  
  
 表 2: マークアップでの相対パック URI  
  
|ファイル|相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|ローカル アセンブリ内のリソース ファイル|`"/ResourceFile.xaml"`|  
|ローカル アセンブリのサブフォルダー内のリソース ファイル|`"/Subfolder/ResourceFile.xaml"`|  
|参照アセンブリ内のリソース ファイル|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|参照アセンブリのサブフォルダー内のリソース ファイル|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|コンテンツ ファイル|`"/ContentFile.xaml"`|  
|サブフォルダー内のコンテンツ ファイル|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a>コードでのパック URI の使用  
 パックを指定する[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]をインスタンス化するコードの中で、<xref:System.Uri>クラスと、パックを渡す[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]コンス トラクターにパラメーターとして。 このコード例を次に示します。  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 既定では、<xref:System.Uri>クラス考慮パック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]絶対であります。 インスタンスの場合にその結果、例外が発生、<xref:System.Uri>相対パックのクラスが作成される[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 さいわい、<xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29>のオーバー ロード、<xref:System.Uri>クラスのコンス トラクターが型のパラメーターを受け入れる<xref:System.UriKind>を指定することをパックかどうか[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]は絶対的または相対的です。  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 のみを指定する必要があります<xref:System.UriKind.Absolute>または<xref:System.UriKind.Relative>されることを確認、指定されたパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]はどちらか一方です。 パックの種類がわからない場合[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、ユーザーがパッケージに入ったときなど、使用される[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、実行時に使用<xref:System.UriKind.RelativeOrAbsolute>代わりにします。  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 表 3 は、さまざまな相対パックを示しています。[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]を使用してコードで指定できる<xref:System.Uri?displayProperty=nameWithType>です。  
  
 表 3: コードでの絶対パック URI  
  
|ファイル|絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|リソース ファイル - ローカル アセンブリ|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|サブフォルダー内のリソース ファイル - ローカル アセンブリ|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|リソース ファイル - 参照アセンブリ|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|参照アセンブリのサブフォルダー内のリソース ファイル|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|バージョン管理された参照アセンブリ内のリソース ファイル|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|コンテンツ ファイル|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|サブフォルダー内のコンテンツ ファイル|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|起点サイト ファイル|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|サブフォルダー内の起点サイト ファイル|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 表 4 は、さまざまな相対パックを示しています。[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]を使用してコードで指定できる<xref:System.Uri?displayProperty=nameWithType>です。  
  
 表 4: コードでの相対パック URI  
  
|ファイル|相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|リソース ファイル - ローカル アセンブリ|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|サブフォルダー内のリソース ファイル - ローカル アセンブリ|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|リソース ファイル - 参照アセンブリ|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|サブフォルダー内のリソース ファイル - 参照アセンブリ|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|コンテンツ ファイル|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|サブフォルダー内のコンテンツ ファイル|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a>一般的なパック URI のシナリオ  
 前のセクションでは、パックを作成する方法を説明した[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]リソース、コンテンツ、およびファイルの元のサイトを識別します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]これらの構造は、さまざまな方法で使用される、および次のセクションでは、いくつかの一般的な使用法を説明します。  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>アプリケーションの起動時に表示する UI の指定  
 <xref:System.Windows.Application.StartupUri%2A>最初の指定[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]場合に表示する、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションを起動します。 スタンドアロン アプリケーションの場合、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]次の例で示すように、ウィンドウにすることができます。  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 スタンドアロン アプリケーションと[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]次の例で示すように、初期の UI とページを指定もできます。  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 アプリケーションがスタンドアロンのアプリケーションと、ページを指定したかどうか<xref:System.Windows.Application.StartupUri%2A>、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]開きます、<xref:System.Windows.Navigation.NavigationWindow>ページをホストします。 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]ホストのブラウザーで、ページが表示されます。  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a>ページへのナビゲート  
 次の例は、ページにナビゲートする方法を示しています。  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 内で移動するさまざまな方法について詳しく[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]を参照してください[ナビゲーション概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)です。  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a>ウィンドウ アイコンの指定  
 次の例は、URI を使用してウィンドウのアイコンを指定する方法を示しています。  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 詳細については、「<xref:System.Windows.Window.Icon%2A>」を参照してください。  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a>イメージ ファイル、オーディオ ファイル、およびビデオ ファイルの読み込み  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]により、さまざまなメディアの種類、すべて識別およびパックに読み込まれることができますを使用するアプリケーション[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]、次の例に示すようにします。  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 メディア コンテンツの操作の詳細については、次を参照してください。[グラフィックスとマルチ メディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)です。  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>起点サイトからのリソース ディクショナリの読み込み  
 リソース ディクショナリ (<xref:System.Windows.ResourceDictionary>) アプリケーションのテーマをサポートするために使用できます。 テーマを作成し、管理する方法の 1 つは、複数のテーマをリソース ディクショナリとして作成して、アプリケーションの起点サイトに配置することです。 これにより、アプリケーションを再コンパイルして再配置しなくても、テーマの追加と交信が可能です。 これらのリソース ディクショナリは、識別し、パックを使用して読み込まれた[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]、次の例で示したです。  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 テーマの概要については[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]を参照してください[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
