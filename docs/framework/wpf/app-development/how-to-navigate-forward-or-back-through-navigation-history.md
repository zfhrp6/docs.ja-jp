---
title: "方法: 移動履歴を前後へ移動する"
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
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ad909af071d4006346d64ad8e4bd7b57c4eefad
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="5b8ea-102">方法: 移動履歴を前後へ移動する</span><span class="sxs-lookup"><span data-stu-id="5b8ea-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="5b8ea-103">この例では、ナビゲーション履歴のエントリに前後を移動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5b8ea-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b8ea-104">例</span><span class="sxs-lookup"><span data-stu-id="5b8ea-104">Example</span></span>  
 <span data-ttu-id="5b8ea-105">次のホストのコンテンツから実行されるコードは、ナビゲーション履歴、一度に 1 つのエントリを前後に移動できます。</span><span class="sxs-lookup"><span data-stu-id="5b8ea-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
-   <span data-ttu-id="5b8ea-106"><xref:System.Windows.Navigation.NavigationWindow>使用します。<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="5b8ea-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   <span data-ttu-id="5b8ea-107"><xref:System.Windows.Controls.Frame>使用します。<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="5b8ea-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="5b8ea-108">前方の 1 つのエントリを移動することができます、前にする必要があります最初ことを確認エントリ"進む"ナビゲーション履歴を調べることによって、 **CanGoForward**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5b8ea-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="5b8ea-109">転送の 1 つのエントリを移動するを呼び出す、 **GoForward**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5b8ea-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="5b8ea-110">これは、次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5b8ea-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="5b8ea-111">移動する前に 1 つのエントリには、する必要がありますまずことを確認エントリ ナビゲーション履歴を調べることによって、 **CanGoBack**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5b8ea-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="5b8ea-112">バックアップ 1 つのエントリを移動するを呼び出す、 **GoBack**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5b8ea-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="5b8ea-113">これは、次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5b8ea-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="5b8ea-114">**CanGoForward**、 **GoForward**、 **CanGoBack**、および**GoBack**によって実装される<xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Frame>、および<xref:System.Windows.Navigation.NavigationService>です。</span><span class="sxs-lookup"><span data-stu-id="5b8ea-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b8ea-115">呼び出す場合**GoForward**、ナビゲーション履歴にエントリがないとを呼び出す場合、または**GoBack**、ナビゲーション履歴にエントリがないと、<xref:System.InvalidOperationException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5b8ea-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
