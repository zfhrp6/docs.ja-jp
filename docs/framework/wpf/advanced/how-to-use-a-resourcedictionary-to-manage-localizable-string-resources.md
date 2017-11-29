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
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="795f0-102">方法: ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する</span><span class="sxs-lookup"><span data-stu-id="795f0-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="795f0-103">この例を使用する方法を示しています、<xref:System.Windows.ResourceDictionary>のローカライズ可能な文字列リソースをパッケージ化[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="795f0-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="795f0-104">ResourceDictionary を使用してローカライズ可能な文字列リソースを管理するには</span><span class="sxs-lookup"><span data-stu-id="795f0-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1.  <span data-ttu-id="795f0-105">作成、<xref:System.Windows.ResourceDictionary>をローカライズするには、文字列を格納しています。</span><span class="sxs-lookup"><span data-stu-id="795f0-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="795f0-106">次のコードは一例を示しています。</span><span class="sxs-lookup"><span data-stu-id="795f0-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="795f0-107">このコードで定義された文字列リソース`localizedMessage`、型の<xref:System.String>から、 <xref:System> mscorlib.dll に名前空間。</span><span class="sxs-lookup"><span data-stu-id="795f0-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2.  <span data-ttu-id="795f0-108">追加、<xref:System.Windows.ResourceDictionary>のため、アプリケーションには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="795f0-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  <span data-ttu-id="795f0-109">マークアップの文字列リソースを使用してを使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]次と同様にします。</span><span class="sxs-lookup"><span data-stu-id="795f0-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  <span data-ttu-id="795f0-110">次のようなコードを使用して、コードビハインドから文字列リソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="795f0-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  <span data-ttu-id="795f0-111">アプリケーションをローカライズします。</span><span class="sxs-lookup"><span data-stu-id="795f0-111">Localize the application.</span></span> <span data-ttu-id="795f0-112">詳細については、次を参照してください。[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="795f0-112">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>
