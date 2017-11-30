---
title: "OpenType フォント パックのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbc5caeab5a77518e160bacb9722e50ff7abbfb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sample-opentype-font-pack"></a>OpenType フォント パックのサンプル
このトピックでは、[!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] で配布されている [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントのサンプルの概要を説明します。 サンプル フォントは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションで使用可能な拡張 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 機能をサポートしています。  
  
  
<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>OpenType フォント パックのフォント  
 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] には、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの作成に使用できる [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォント サンプルのセットが用意されています。 サンプル フォントは、Ascender Corporation のライセンスを受けて提供されています。 これらのフォントには、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォーマットで定義されている機能全体のサブセットだけが実装されています。 サンプルの [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォント名の一覧を次の表に示します。  
  
|**名前**|**ファイル**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles Light|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 次の図は [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントのサンプルが、どのように表示されるかを示しています。  
  
 ![サンプル フォント パック内のフォント名のリスト](../../../../docs/framework/wpf/advanced/media/samplefontpack01.gif "samplefontpack01")  
OpenType フォント パックのフォント  
  
 サンプル フォントは、Ascender Corporation のライセンスを受けて提供されています。 Ascender は、高度なフォント製品を提供する企業です。 サンプル フォントの拡張版またはカスタム版のライセンスを受けるには、[Ascender Corporation の Web サイト](http://go.microsoft.com/fwlink/?LinkId=182627)を参照してください。  
  
> [!NOTE]
>  アプリケーションに埋め込む、または別の方法で再頒布するフォントについて、必要なライセンス権限を取得することは、開発者であるユーザーの責任で行ってください。  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>フォントのインストール  
 サンプルの [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントを、既定の [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] フォント ディレクトリである **\WINDOWS\Fonts** にインストールできます。 フォントをインストールするには、コントロール パネルの [フォント] を使用します。 これらのフォントをコンピューターにインストールすると、既定の [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] フォントを参照するすべてのアプリケーションからアクセスできるようになります。 フォント ファイルをダブルクリックして、各フォントの文字を異なるいくつかのフォント サイズで表示できます。 次のスクリーン ショットは、Lindsey フォント ファイル (Linds.ttf) を表示したものです。  
  
 ![Lindsey フォント &#40;OpenType&#41;] (../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF_04")  
Lindsey フォントの表示  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>フォントの使用  
 アプリケーションでフォントを使用するには、2 とおりの方法があります。 アセンブリ内にリソースとして埋め込まれていないプロジェクト コンテンツ項目として、フォントをアプリケーションに追加できます。 あるいは、アプリケーションのアセンブリ ファイル内に埋め込まれたプロジェクト リソース項目として、フォントをアプリケーションに追加できます。 詳細については、「[アプリケーションでのフォントのパッケージング](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Documents.Typography>  
 [OpenType フォントの機能](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [アプリケーションでのフォントのパッケージング](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
