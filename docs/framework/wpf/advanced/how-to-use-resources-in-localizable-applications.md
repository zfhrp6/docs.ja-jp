---
title: '方法: ローカライズ可能アプリケーションでリソースを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 82a24feb4008b6cfd7c1751c6449c0d8515ffe87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544704"
---
# <a name="how-to-use-resources-in-localizable-applications"></a>方法: ローカライズ可能アプリケーションでリソースを使用する
ローカライズとは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を異なるカルチャ。 そのためには、タイトル、キャプション、リスト ボックス項目などのテキストを翻訳する必要があります。 翻訳しやすいように、翻訳される項目はリソース ファイルにまとめられています。 参照してください[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)のローカライズ用リソース ファイルを作成する方法についてはします。 させる、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションのローカライズ可能な開発者は、すべてのローカライズ可能なリソースをリソース アセンブリに組み込む必要があります。 リソース アセンブリは、異なる言語にローカライズし、分離コードがリソースの管理を使用して[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]を読み込めません。 必要なファイルのいずれか、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、プロジェクト ファイル (.proj)。 アプリケーションで使用するすべてのリソースをプロジェクト ファイルに含める必要があります。 このコード例を次に示します。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 インスタンス化するアプリケーションで、リソースを使用する<xref:System.Resources.ResourceManager>し、使用するリソースを読み込みます。 その方法を次に示します。  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
