---
title: '方法: ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 70f8f02f315580c8056ee698b5e45b1a31a3dc74
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="ed974-102">方法: ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する</span><span class="sxs-lookup"><span data-stu-id="ed974-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="ed974-103">この例を使用する方法を示しています、 <xref:System.Windows.ResourceDictionary> Windows Presentation Foundation (WPF) アプリケーションのローカライズ可能な文字列リソースをパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="ed974-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for Windows Presentation Foundation (WPF) applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="ed974-104">ResourceDictionary を使用してローカライズ可能な文字列リソースを管理するには</span><span class="sxs-lookup"><span data-stu-id="ed974-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1.  <span data-ttu-id="ed974-105">作成、<xref:System.Windows.ResourceDictionary>をローカライズするには、文字列を格納しています。</span><span class="sxs-lookup"><span data-stu-id="ed974-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="ed974-106">次のコードは一例を示しています。</span><span class="sxs-lookup"><span data-stu-id="ed974-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="ed974-107">このコードで定義された文字列リソース`localizedMessage`、型の<xref:System.String>から、 <xref:System> mscorlib.dll に名前空間。</span><span class="sxs-lookup"><span data-stu-id="ed974-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2.  <span data-ttu-id="ed974-108">追加、<xref:System.Windows.ResourceDictionary>のため、アプリケーションには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ed974-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  <span data-ttu-id="ed974-109">マークアップの文字列リソースを使用してを使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]次と同様にします。</span><span class="sxs-lookup"><span data-stu-id="ed974-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  <span data-ttu-id="ed974-110">次のようなコードを使用して、コードビハインドから文字列リソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="ed974-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  <span data-ttu-id="ed974-111">アプリケーションをローカライズします。</span><span class="sxs-lookup"><span data-stu-id="ed974-111">Localize the application.</span></span> <span data-ttu-id="ed974-112">詳細については、次を参照してください。[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="ed974-112">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>
