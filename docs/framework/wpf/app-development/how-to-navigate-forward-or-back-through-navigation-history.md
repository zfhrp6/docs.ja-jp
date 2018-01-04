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
ms.workload: dotnet
ms.openlocfilehash: 78fd9fec6a93c100da6b4e7174376a963ae8beb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>方法: 移動履歴を前後へ移動する
この例では、ナビゲーション履歴のエントリに前後を移動する方法を示します。  
  
## <a name="example"></a>例  
 次のホストのコンテンツから実行されるコードは、ナビゲーション履歴、一度に 1 つのエントリを前後に移動できます。  
  
-   <xref:System.Windows.Navigation.NavigationWindow>使用します。<xref:System.Windows.Navigation.NavigationService>  
  
-   <xref:System.Windows.Controls.Frame>使用します。<xref:System.Windows.Navigation.NavigationService>  
  
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
