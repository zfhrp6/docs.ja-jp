---
title: "方法 : ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する | Microsoft Docs"
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
  - "ローカリゼーション [WPF], パッケージ化 (文字列リソースを)"
  - "パッケージ化 (文字列リソースを)"
  - "ResourceDictionary [WPF]"
  - "リソース [WPF], パッケージ化 (文字列リソースを)"
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する
この例では、<xref:System.Windows.ResourceDictionary> を使用して、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 用にローカライズ可能な文字列リソースをパッケージ化する方法を示します。  
  
### ResourceDictionary を使用してローカライズ可能な文字列リソースを管理するには  
  
1.  ローカライズする文字列を含む <xref:System.Windows.ResourceDictionary> を作成します。  次に例を示します。  
  
     [!code-xml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     このコードでは、mscorlib.dll の <xref:System> 名前空間で <xref:System.String> 型の文字列リソース `localizedMessage` を定義しています。  
  
2.  次のコードを使用して、<xref:System.Windows.ResourceDictionary> をアプリケーションに追加します。  
  
     [!code-xml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を次のように使用して、文字列リソースをマークアップから使用します。  
  
     [!code-xml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  次のようなコード使用して、文字列リソースを分離コードから使用します。  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  アプリケーションをローカライズします。  詳細については、「[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)」を参照してください。