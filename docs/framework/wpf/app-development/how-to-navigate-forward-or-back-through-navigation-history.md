---
title: '方法: 移動履歴を前後へ移動する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: ac3b8b71b6adf04d71cf35edbb042b82c57d8e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546267"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>方法: 移動履歴を前後へ移動する
この例では、ナビゲーション履歴のエントリに前後を移動する方法を示します。  
  
## <a name="example"></a>例  
 次のホストのコンテンツから実行されるコードは、ナビゲーション履歴、一度に 1 つのエントリを前後に移動できます。  
  
-   <xref:System.Windows.Navigation.NavigationWindow> 使用します。 <xref:System.Windows.Navigation.NavigationService>  
  
-   <xref:System.Windows.Controls.Frame> 使用します。 <xref:System.Windows.Navigation.NavigationService>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 前方の 1 つのエントリを移動することができます、前にする必要があります最初ことを確認エントリ"進む"ナビゲーション履歴を調べることによって、 **CanGoForward**プロパティです。 転送の 1 つのエントリを移動するを呼び出す、 **GoForward**メソッドです。 これは、次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 移動する前に 1 つのエントリには、する必要がありますまずことを確認エントリ ナビゲーション履歴を調べることによって、 **CanGoBack**プロパティです。 バックアップ 1 つのエントリを移動するを呼び出す、 **GoBack**メソッドです。 これは、次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**、 **GoForward**、 **CanGoBack**、および**GoBack**によって実装される<xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Frame>、および<xref:System.Windows.Navigation.NavigationService>です。  
  
> [!NOTE]
>  呼び出す場合**GoForward**、ナビゲーション履歴にエントリがないとを呼び出す場合、または**GoBack**、ナビゲーション履歴にエントリがないと、<xref:System.InvalidOperationException>がスローされます。
