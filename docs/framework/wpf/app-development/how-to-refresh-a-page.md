---
title: '方法: ページを更新'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], refreshing
- refreshing pages [WPF]
ms.assetid: 06dd1bbd-81c4-40ad-ac0d-7a5b326b1465
ms.openlocfilehash: 27735450360206e0a15ecae00cc9d45f93e4e838
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546531"
---
# <a name="how-to-refresh-a-page"></a><span data-ttu-id="f6807-102">方法: ページを更新</span><span class="sxs-lookup"><span data-stu-id="f6807-102">How to: Refresh a Page</span></span>
<span data-ttu-id="f6807-103">この例を呼び出す方法を示します、<xref:System.Windows.Navigation.NavigationWindow.Refresh%2A>で現在のコンテンツを更新する方法、<xref:System.Windows.Navigation.NavigationWindow>です。</span><span class="sxs-lookup"><span data-stu-id="f6807-103">This example shows how to call the <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> method to refresh the current content in a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6807-104">例</span><span class="sxs-lookup"><span data-stu-id="f6807-104">Example</span></span>  
 <span data-ttu-id="f6807-105"><xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> 現在のコンテンツを更新、<xref:System.Windows.Navigation.NavigationWindow>のソースから再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="f6807-105"><xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> refreshes the current content in a <xref:System.Windows.Navigation.NavigationWindow> to be reloaded from its source.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigaterefreshcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigaterefreshcode)]
