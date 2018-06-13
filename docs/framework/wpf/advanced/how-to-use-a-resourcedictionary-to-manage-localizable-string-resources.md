---
title: '方法: ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
ms.openlocfilehash: 76ff3f688b5d3e7122254990076edb21fe6ae119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544499"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>方法: ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する
この例を使用する方法を示しています、 <xref:System.Windows.ResourceDictionary> Windows Presentation Foundation (WPF) アプリケーションのローカライズ可能な文字列リソースをパッケージ化します。  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>ResourceDictionary を使用してローカライズ可能な文字列リソースを管理するには  
  
1.  作成、<xref:System.Windows.ResourceDictionary>をローカライズするには、文字列を格納しています。 次のコードは一例を示しています。  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     このコードで定義された文字列リソース`localizedMessage`、型の<xref:System.String>から、 <xref:System> mscorlib.dll に名前空間。  
  
2.  追加、<xref:System.Windows.ResourceDictionary>のため、アプリケーションには、次のコードを使用します。  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  マークアップの文字列リソースを使用してを使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]次と同様にします。  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  次のようなコードを使用して、コードビハインドから文字列リソースを使用します。  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  アプリケーションをローカライズします。 詳細については、次を参照してください。[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)です。
