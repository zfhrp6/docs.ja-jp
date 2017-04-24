---
title: "OpenType フォント パックのサンプル | Microsoft Docs"
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
  - "フォント, OpenType フォント パック"
  - "OpenType フォント パック"
  - "タイポグラフィ, OpenType フォント パック"
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# OpenType フォント パックのサンプル
ここでは、[!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] で配布されている、サンプルの [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントの概要について説明します。  サンプル フォントは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションで使用可能な拡張 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 機能をサポートしています。  
  
   
  
<a name="overview"></a>   
## OpenType フォント パックのフォント  
 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] には、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの作成に使用できる一連の [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントがサンプルとして用意されています。  サンプル フォントは、Ascender Corporation のライセンスを受けて提供されています。  これらのフォントには、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 形式で定義されているすべての機能のサブセットだけが実装されています。  次の表に、サンプルの [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォント名の一覧を示します。  
  
|**名前**|**File**|  
|------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles Light|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 次に示すのは、サンプルの [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントです。  
  
 ![サンプル フォント パック内のフォント名の一覧](../../../../docs/framework/wpf/advanced/media/samplefontpack01.png "samplefontpack01")  
OpenType フォント パックのフォント  
  
 サンプル フォントは、Ascender Corporation のライセンスを受けて提供されています。  Ascender は高度なフォント製品を提供する企業です。  サンプル フォントの拡張版またはカスタム版のライセンスを受けるには、[Ascender Corporation の Web サイト](http://go.microsoft.com/fwlink/?LinkId=182627)を参照してください。  
  
> [!NOTE]
>  アプリケーションに埋め込む、または別の方法で再頒布するフォントについて、必要なライセンス権限を取得することは、開発者であるユーザーの責任で行ってください。  
  
<a name="installing_the_fonts"></a>   
## フォントのインストール  
 サンプルの [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントは、既定の [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] フォント ディレクトリ **\\WINDOWS\\Fonts** にインストールできます。  フォントをインストールするには、コントロール パネルの \[フォント\] を使用します。  これらのフォントをコンピューターにインストールすると、既定の [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] フォントを参照するすべてのアプリケーションからアクセスできるようになります。フォント ファイルの名前をダブルクリックすることで、各フォントの文字をさまざまなサイズで表示して確認することができます。  次のスクリーン ショットは、Lindsey フォント ファイル \(Linds.ttf\) を表示したものです。  
  
 ![Lindsey フォント &#40;OpenType&#41;](../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF\_04")  
Lindsey フォントの表示  
  
<a name="using_the_fonts"></a>   
## フォントの使用  
 アプリケーションでフォントを使用するには、2 とおりの方法があります。  フォントは、アセンブリにリソースとして埋め込まれていないプロジェクト コンテンツ項目としてアプリケーションに追加できます。  フォントは、アプリケーションのアセンブリ ファイルに埋め込まれたプロジェクト リソース項目としてアプリケーションに追加することもできます。  詳細については、「[アプリケーションでのフォントのパッケージング](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Documents.Typography>   
 [OpenType フォントの機能](../../../../docs/framework/wpf/advanced/opentype-font-features.md)   
 [アプリケーションでのフォントのパッケージング](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)