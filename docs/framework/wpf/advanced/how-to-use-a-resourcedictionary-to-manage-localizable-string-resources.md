---
title: "方法: ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 38cfd687eadf31cc94dfdd2cbbf082bf80424cba
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>方法: ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する
この例を使用する方法を示しています、<xref:System.Windows.ResourceDictionary>のローカライズ可能な文字列リソースをパッケージ化[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]アプリケーションです。  
  
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
