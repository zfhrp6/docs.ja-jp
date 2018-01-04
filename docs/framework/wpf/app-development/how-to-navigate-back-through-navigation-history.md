---
title: "方法: ナビゲーション履歴を後方に移動"
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
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3bfc809dbe76c17859cb3fcd83f8a293a24b308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
