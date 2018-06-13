---
title: '方法: ナビゲーション履歴を後方に移動'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 9acbc5d3388a8df0ec7d7b5326f449f092f0cb03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546674"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="ff14b-102">方法: ナビゲーション履歴を後方に移動</span><span class="sxs-lookup"><span data-stu-id="ff14b-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="ff14b-103">この例では、ナビゲーション履歴を戻るのエントリに移動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ff14b-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff14b-104">例</span><span class="sxs-lookup"><span data-stu-id="ff14b-104">Example</span></span>  
 <span data-ttu-id="ff14b-105">ホストされているコンテンツから実行されているコード、 <xref:System.Windows.Navigation.NavigationWindow>、<xref:System.Windows.Controls.Frame>使用<xref:System.Windows.Navigation.NavigationService>、または[!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]ナビゲーション履歴に一度に 1 つのエントリを後方に移動できます。</span><span class="sxs-lookup"><span data-stu-id="ff14b-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> use <xref:System.Windows.Navigation.NavigationService>, or [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="ff14b-106">間を移動する 1 つ前のエントリは、エントリがあるナビゲーション履歴を調べることによってを最初に確認が必要です、 **CanGoBack**プロパティを 1 つのエントリを呼び出すことによってバックアップを移動する前に、 **GoBack**メソッド。</span><span class="sxs-lookup"><span data-stu-id="ff14b-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="ff14b-107">これは、次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ff14b-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="ff14b-108">**CanGoBack**と**GoBack**によって実装される<xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Frame>、および<xref:System.Windows.Navigation.NavigationService>です。</span><span class="sxs-lookup"><span data-stu-id="ff14b-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff14b-109">呼び出す場合**GoBack**、ナビゲーション履歴にエントリがないと、<xref:System.InvalidOperationException>が発生します。</span><span class="sxs-lookup"><span data-stu-id="ff14b-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
