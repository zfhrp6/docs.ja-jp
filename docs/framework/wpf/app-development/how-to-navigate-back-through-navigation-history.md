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
---
# <a name="how-to-navigate-back-through-navigation-history"></a>方法: ナビゲーション履歴を後方に移動
この例では、ナビゲーション履歴を戻るのエントリに移動する方法を示します。  
  
## <a name="example"></a>例  
 ホストされているコンテンツから実行されているコード、 <xref:System.Windows.Navigation.NavigationWindow>、<xref:System.Windows.Controls.Frame>使用<xref:System.Windows.Navigation.NavigationService>、または[!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]ナビゲーション履歴に一度に 1 つのエントリを後方に移動できます。  
  
 間を移動する 1 つ前のエントリは、エントリがあるナビゲーション履歴を調べることによってを最初に確認が必要です、 **CanGoBack**プロパティを 1 つのエントリを呼び出すことによってバックアップを移動する前に、 **GoBack**メソッド。 これは、次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack**と**GoBack**によって実装される<xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Frame>、および<xref:System.Windows.Navigation.NavigationService>です。  
  
> [!NOTE]
>  呼び出す場合**GoBack**、ナビゲーション履歴にエントリがないと、<xref:System.InvalidOperationException>が発生します。
