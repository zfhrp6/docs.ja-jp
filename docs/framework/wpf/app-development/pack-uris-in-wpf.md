---
title: "WPF におけるパッケージの URI | Microsoft Docs"
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
  - "アプリケーション管理 [WPF]"
  - "読み込み (埋め込みリソースを)"
  - "読み込み (非リソース ファイルを)"
  - "パック URI スキーム"
  - "Uniform Resource Identifier (URI)"
  - "URI (Uniform Resource Identifier)"
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# WPF におけるパッケージの URI
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] において、[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] は次のようなさまざまな用途でファイルを指定し、読み込むために使用されます。  
  
-   アプリケーションの起動時に表示する [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] の指定。  
  
-   イメージの読み込み。  
  
-   ページへの移動。  
  
-   実行可能ファイルではないデータ ファイルの読み込み。  
  
 また、[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を使用して、次に示すようなさまざまな場所にあるファイルを指定し、読み込むことができます。  
  
-   現在のアセンブリ。  
  
-   参照アセンブリ。  
  
-   アセンブリを基準とした場所。  
  
-   アプリケーションの起点サイト。  
  
 こうした場所にある各種ファイルを指定して読み込むため、一貫性のある仕組みの提供を目的として、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では*パッケージの URI スキーム*を採用しています。  このトピックでは、このスキームの概要、さまざまなシナリオでのパッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] の作成方法、絶対および相対 [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] と [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の解決について説明した後、マークアップやコードでパッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を使用する方法について説明します。  
  
   
  
<a name="The_Pack_URI_Scheme"></a>   
## パッケージの URI スキーム  
 パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] スキームは、[Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) \(OPC\) 仕様で使用されています。この仕様は、コンテンツの編成および特定について規定します。  このモデルの主な要素はパッケージとパーツです。*パッケージ*は、1 つ以上の論理*パーツ*の論理コンテナーです。  この概念を次の図に示します。  
  
 ![パッケージとパーツのダイアグラム](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.png "WPFPackURISchemeFigure1")  
  
 パーツの識別を目的として、OPC 仕様では、パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] スキームを定義するために、RFC 2396 \(Uniform Resource Identifiers \(URI\): Generic Syntax\) の拡張機能を利用しています。  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] で指定されるスキームは、そのプレフィックスで定義されます。http、ftp、file などがよく知られています。  パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] スキームは、スキームとして pack を使用し、証明機関とパスの 2 つのコンポーネントが含まれます。  パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の書式は次のとおりです。  
  
 pack:\/\/*authority*\/*path*  
  
 *authority* は、パーツが格納されているパッケージの種類を指定し、*path* は、パッケージ内のパーツの場所を指定します。  
  
 この概念を次の図に示します。  
  
 ![パッケージ、権限、およびパスの間のリレーションシップ](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.png "WPFPackURISchemeFigure2")  
  
 パッケージとパーツは、アプリケーションとアプリケーション データ ファイルに似ています。つまり、アプリケーション \(パッケージ\) には、次のような 1 つ以上のファイル \(パーツ\) を含めることができます。  
  
-   ローカル アセンブリにコンパイルされるリソース ファイル。  
  
-   参照アセンブリにコンパイルされるリソース ファイル。  
  
-   参照元のアセンブリにコンパイルされるリソース ファイル。  
  
-   コンテンツ ファイル。  
  
-   起点サイト ファイル。  
  
 これらのファイルにアクセスするために、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、application:\/\/\/ と siteoforigin:\/\/\/ という 2 つの証明機関をサポートします。  application:\/\/\/ 証明機関は、リソース ファイルやコンテンツ ファイルなど、コンパイル時に既知のアプリケーション データ ファイルを示すために使用されます。  siteoforigin:\/\/\/ 証明機関は、起点サイト ファイルの指定に使用されます。  各証明機関のスコープを、次の図に示します。  
  
 ![Pack URI のダイアグラム](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の証明機関コンポーネントは、パッケージを指す埋め込みの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] で、RFC 2396 に準拠する必要があります。  また、"\/" 文字は "," 文字に置き換え、"%" や "?" などの予約文字はエスケープする必要があります。  詳細については、OPC を参照してください。  
  
 以下のセクションでは、2 つの証明機関と、リソース ファイル、コンテンツ ファイル、および起点サイト ファイルの適切なパスとを組み合わせて使用して、パッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を構築する方法について説明します。  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## リソース ファイル パッケージの URI  
 リソース ファイルは [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` 項目として構成され、コンパイルされてアセンブリに変換されます。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、ローカル アセンブリに変換されたリソース ファイルの指定やローカル アセンブリから参照されるアセンブリに変換されたリソース ファイルの指定に使用できるパッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] の構築をサポートしています。  
  
<a name="Local_Assembly_Resource_File"></a>   
### ローカル アセンブリ リソース ファイル  
 ローカル アセンブリにコンパイルされるリソース ファイルのパッケージ [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] は、次の証明機関とパスを使用します。  
  
-   **証明機関** : application:\/\/\/。  
  
-   **パス** : ローカル アセンブリ プロジェクト フォルダーのルートを基準とするパスを含む、リソース ファイルの名前。  
  
 ローカル アセンブリのプロジェクト フォルダーのルートにある [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リソース ファイルのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の例を次に示します。  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 ローカル アセンブリのプロジェクト フォルダーのサブフォルダーにある [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リソース ファイルのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の例を次に示します。  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### 参照アセンブリ リソース ファイル  
 参照アセンブリにコンパイルされるリソース ファイルのパッケージ [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] は、次の証明機関とパスを使用します。  
  
-   **証明機関** : application:\/\/\/。  
  
-   **パス** : コンパイルされて参照アセンブリに変換されるリソース ファイルの名前。  パスは、次の書式に従う必要があります。  
  
     *AssemblyShortName*\[*;Version*\]\[*;PublicKey*\];component\/*Path*  
  
    -   **AssemblyShortName** : 参照アセンブリの短い名前。  
  
    -   **;Version** \(省略可能\): リソース ファイルを含む参照アセンブリのバージョン。  これは、同じ短い名前を持つ 2 つ以上の参照アセンブリを読み込む場合に使用されます。  
  
    -   **;PublicKey** \(省略可能\): 参照アセンブリの署名に使用された公開キー。  これは、同じ短い名前を持つ 2 つ以上の参照アセンブリを読み込む場合に使用されます。  
  
    -   **;component**: 参照アセンブリがローカル アセンブリから参照されることを指定します。  
  
    -   **\/Path**: 参照アセンブリのプロジェクト フォルダーのルートを基準とするパスを含む、リソース ファイルの名前。  
  
 参照アセンブリのプロジェクト フォルダーのルートにある [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リソース ファイルのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の例を次に示します。  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 参照アセンブリのプロジェクト フォルダーのサブフォルダーにある [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リソース ファイルのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の例を次に示します。  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 バージョン固有の参照アセンブリのプロジェクト フォルダーのルート フォルダーにある [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リソース ファイルのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の例を次に示します。  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 参照アセンブリ リソース ファイルのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 構文は、application:\/\/\/ 証明機関と組み合わせる場合のみ使用できます。  たとえば、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では次はサポートされません。  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## コンテンツ ファイルのパッケージの URI  
 コンテンツ ファイルのパッケージ [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] は、次の証明機関とパスを使用します。  
  
-   **証明機関** : application:\/\/\/。  
  
-   **パス** : アプリケーションのメインの実行可能アセンブリのファイル システムの場所を基準とするパスを含む、コンテンツ ファイルの名前。  
  
 実行可能アセンブリと同じフォルダーにある [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] コンテンツ ファイルのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の例を次に示します。  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 アプリケーションの実行可能アセンブリを基準とするサブフォルダーにある [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] コンテンツ ファイルのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の例を次に示します。  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] コンテンツ ファイルは、移動先にはできません。  [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] スキームは、起点サイトにある [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] ファイルへの移動のみをサポートします。  
  
<a name="The_siteoforigin_____Authority"></a>   
## 起点サイトのパッケージの URI  
 起点サイト ファイルのパッケージ [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] は、次の証明機関とパスを使用します。  
  
-   **証明機関** : siteoforigin:\/\/\/。  
  
-   **パス** : 実行可能アセンブリが起動される場所を基準とするパスを含む、起点サイト ファイルの名前。  
  
 実行可能アセンブリが起動される場所に格納されている、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 起点サイト ファイルのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の例を次に示します。  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 アプリケーションの実行可能アセンブリが起動される場所を基準とするサブフォルダーに格納されている、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 起点サイト ファイルのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の例を次に示します。  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## パッケージ ファイル  
 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` 項目として構成されている [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルは、リソース ファイルと同じようにしてコンパイルされ、アセンブリに変換されます。  したがって、[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` 項目は、リソース ファイルのパッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を使用して指定できます。  
  
 一般的に [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` 項目として構成される [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルの種類には、ルート要素として次のいずれかが含まれます。  
  
-   <xref:System.Windows.Window?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=fullName>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=fullName>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=fullName>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=fullName>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## 絶対パッケージの URI と相対パッケージの URI  
 完全修飾パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] にはスキーム、証明機関、パスが含まれ、絶対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] と見なされます。  開発者にとっての簡便さを考慮して、通常、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 要素では、パスだけを含む相対パッケージ [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] で適切な属性を設定できます。  
  
 たとえば、ローカル アセンブリ内のリソース ファイルに対する次の絶対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を考えてみます。  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 このリソース ファイルを参照する相対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] は、次のようになります。  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  起点サイト ファイルはアセンブリに関連付けられていないため、絶対パッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を使用した参照のみ可能です。  
  
 既定では、相対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] は、参照を含むマークアップまたはコードの位置を基準にしていると見なされます。  ただし、先頭にバックスラッシュを使用すると、相対パッケージ [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 参照はアプリケーションのルートに対して相対的であると見なされます。  たとえば、次のプロジェクト構造を考えます。  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Page1.xaml に *Root*\\SubFolder\\Page2.xaml を参照する [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] が含まれている場合、参照で次の相対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を使用できます。  
  
 `Page2.xaml`  
  
 Page1.xaml に *Root*\\Page2.xaml を参照する [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] が含まれている場合、参照で次の相対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を使用できます。  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## パッケージの URI の解決  
 パッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] の形式は、さまざまな種類のファイルのパッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] が同じに見えるようになっています。  たとえば、次の絶対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] について検討してみます。  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 この絶対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] は、ローカル アセンブリ内のリソース ファイルまたはコンテンツ ファイルを参照できます。  同じことは、次の相対 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] にも当てはまります。  
  
 `/ResourceOrContentFile.xaml`  
  
 パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] が参照しているファイルの種類を特定するために、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、次のヒューリスティックを使用して、ローカル アセンブリ内のリソース ファイルとコンテンツ ファイルの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を解決します。  
  
1.  アセンブリ メタデータに、パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] に一致する <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 属性があるかどうかを調べます。  
  
2.  <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 属性が見つかった場合は、パッケージ [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] のパスはコンテンツ ファイルを参照しています。  
  
3.  <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 属性が見つからない場合、コンパイルされてローカル アセンブリに変換された設定リソース ファイルを調べます。  
  
4.  パッケージ [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] のパスに一致するリソース ファイルが見つかると、パッケージ [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] のパスはリソース ファイルを参照しています。  
  
5.  リソースが見つからない場合、内部で作成された <xref:System.Uri> は無効です。  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 解決は、次を参照する [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] には適用されません。  
  
-   参照アセンブリ内のコンテンツ ファイル : この種類のファイルは [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] でサポートされません。  
  
-   参照アセンブリに埋め込まれたファイル : これらを指定する [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] は、参照アセンブリの名前と `;component` サフィックスの両方が含まれているため、一意です。  
  
-   起点サイト ファイル : これらを指定する [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] は、siteoforigin:\/\/\/ 証明機関を含むパッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] で指定できる唯一の種類のファイルあるため、一意です。  
  
 パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 解決によってもたらされる 1 つの単純化は、コードがリソース ファイルやコンテンツ ファイルの場所に依存しなくなることです。  たとえば、コンテンツ ファイルに再構成されたリソース ファイルがローカル アセンブリにある場合、そのリソースのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] は変わらず、そのパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を使用するコードも変わりません。  
  
<a name="Programming_with_Pack_URIs"></a>   
## パッケージの URI を使用したプログラミング  
 多くの [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] クラスは、パッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を使用して設定できる次のようなプロパティを実装します。  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=fullName>  
  
 これらのプロパティは、マークアップとコードのどちらからも設定できます。  ここでは、両方の構造と共通シナリオについて説明します。  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### マークアップでのパッケージの URI の使用  
 マークアップでパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を指定するには、パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を使用する属性の要素を設定します。  次に例を示します。  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 表 1 は、マークアップで指定できるさまざまな絶対パッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を示しています。  
  
 表 1 : マークアップでの絶対パッケージの URI  
  
|File|絶対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|---------------------------------------------------------------------------|  
|リソース ファイル \- ローカル アセンブリ|`"pack://application:,,,/ResourceFile.xaml"`|  
|サブフォルダー内のリソース ファイル \- ローカル アセンブリ|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|リソース ファイル \- 参照アセンブリ|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|参照アセンブリのサブフォルダー内のリソース ファイル|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|バージョン管理された参照アセンブリ内のリソース ファイル|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|コンテンツ ファイル|`"pack://application:,,,/ContentFile.xaml"`|  
|サブフォルダー内のコンテンツ ファイル|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|起点サイト ファイル|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|サブフォルダー内の起点サイト ファイル|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 表 2 は、マークアップで指定できるさまざまな相対パッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を示しています。  
  
 表 2 : マークアップでの相対パッケージの URI  
  
|File|相対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|---------------------------------------------------------------------------|  
|ローカル アセンブリ内のリソース ファイル|`"/ResourceFile.xaml"`|  
|ローカル アセンブリのサブフォルダー内のリソース ファイル|`"/Subfolder/ResourceFile.xaml"`|  
|参照アセンブリ内のリソース ファイル|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|参照アセンブリのサブフォルダー内のリソース ファイル|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|コンテンツ ファイル|`"/ContentFile.xaml"`|  
|サブフォルダー内のコンテンツ ファイル|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### コードでのパッケージの URI の使用  
 コードでパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を指定するには、<xref:System.Uri> クラスをインスタンス化し、パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] をパラメーターとしてコンストラクターに渡します。  このコード例を次に示します。  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 既定では、<xref:System.Uri> クラスは、パッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を絶対と見なします。  そのため、<xref:System.Uri> クラスのインスタンスが相対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を使用して作成されると、例外が発生します。  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 しかし、<xref:System.Uri> クラスのコンストラクターの <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> オーバーロードは、<xref:System.UriKind> 型のパラメーターを受け取ります。これを使用すると、パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] が絶対または相対のどちらであるかを指定できます。  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml", UriKind.Relative);  
```  
  
 提供されたパッケージ [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] が <xref:System.UriKind> と <xref:System.UriKind> のどちらであるかわかっている場合は、それだけを指定します。  使用されているパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の種類がわからない場合、たとえばユーザーがパッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を実行時に入力する場合は、代わりに <xref:System.UriKind> を使用します。  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 表 3 は、<xref:System.Uri?displayProperty=fullName> を使用してコードで指定できるさまざまな絶対パッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を示しています。  
  
 表 3 : コードでの絶対パッケージの URI  
  
|File|絶対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|---------------------------------------------------------------------------|  
|リソース ファイル \- ローカル アセンブリ|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|サブフォルダー内のリソース ファイル \- ローカル アセンブリ|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|リソース ファイル \- 参照アセンブリ|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|参照アセンブリのサブフォルダー内のリソース ファイル|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|バージョン管理された参照アセンブリ内のリソース ファイル|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|コンテンツ ファイル|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|サブフォルダー内のコンテンツ ファイル|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|起点サイト ファイル|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|サブフォルダー内の起点サイト ファイル|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 表 4 は、<xref:System.Uri?displayProperty=fullName> を使用してコードで指定できるさまざまな相対パッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を示しています。  
  
 表 4 : コードでの相対パッケージの URI  
  
|File|相対パッケージの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|---------------------------------------------------------------------------|  
|リソース ファイル \- ローカル アセンブリ|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|サブフォルダー内のリソース ファイル \- ローカル アセンブリ|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|リソース ファイル \- 参照アセンブリ|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|サブフォルダー内のリソース ファイル \- 参照アセンブリ|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|コンテンツ ファイル|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|サブフォルダー内のコンテンツ ファイル|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### パッケージの URI 関連の一般的なシナリオ  
 ここまで、リソース ファイル、コンテンツ ファイル、および起点サイト ファイルを指定するためにパッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を構築する方法を説明してきました。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、こうした構造はさまざまな方法で使用されています。以下のセクションでは、いくつかの一般的な用途について説明します。  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### アプリケーションの起動時に表示する UI の指定  
 <xref:System.Windows.Application.StartupUri%2A> は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの起動時に表示する最初の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を指定します。  スタンドアロン アプリケーションでは、次の例に示すように、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] としてウィンドウを使用できます。  
  
 [!code-xml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 スタンドアロン アプリケーションおよび [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] では、次の例に示すように、初期 UI としてページを指定することもできます。  
  
 [!code-xml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 アプリケーションがスタンドアロン アプリケーションであり、ページが <xref:System.Windows.Application.StartupUri%2A> を使用して指定されている場合、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は <xref:System.Windows.Navigation.NavigationWindow> を開いてページをホストします。  [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] の場合、ページはホスト ブラウザーに表示されます。  
  
<a name="Navigating_to_a_Page"></a>   
#### ページへの移動  
 ページへの移動方法を次の例に示します。  
  
 [!code-xml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] で移動に使用できるさまざまな方法の詳細については、「[ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)」を参照してください。  
  
<a name="Specifying_a_Window_Icon"></a>   
#### ウィンドウ アイコンの指定  
 URI を使用してウィンドウのアイコンを指定する方法を次の例に示します。  
  
 [!code-xml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 詳細については、「<xref:System.Windows.Window.Icon%2A>」を参照してください。  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### イメージ ファイル、オーディオ ファイル、およびビデオ ファイルの読み込み  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用すると、アプリケーションでさまざまな種類のメディアを使用できます。次の例に示すように、それらはどれもパッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を使用して指定し、読み込むことができます。  
  
 [!code-xml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 メディア コンテンツの操作方法の詳細については、「[グラフィックスとマルチメディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)」を参照してください。  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### 起点サイトからのリソース ディクショナリの読み込み  
 リソース ディクショナリ \(<xref:System.Windows.ResourceDictionary>\) は、アプリケーション テーマのサポートに使用できます。  テーマを作成および管理する 1 つの方法は、複数のテーマをリソース ディクショナリとして作成し、アプリケーションの起点サイトに配置することです。  これにより、アプリケーションを再コンパイルして再配置することなく、テーマを追加および更新できます。  これらのリソース ディクショナリは、次の例に示すように、パッケージの [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] を使用して指定し、読み込むことができます。  
  
 [!code-xml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] でのテーマの概要については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
## 参照  
 [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)