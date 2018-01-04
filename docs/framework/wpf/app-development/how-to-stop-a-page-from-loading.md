---
title: "方法: ページの読み込みの停止"
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
- pages [WPF], stopping from loading
- methods [WPF], Stoploading
- events [WPF], NavigationStopped
- NavigationStopped properties [WPF]
- stopping pages from loading [WPF]
- loading [WPF], stopping
ms.assetid: e2b695b0-517e-462c-8ccf-90cc8d6ba864
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6109a45f885a6a94a5785329d10bce52a0090802
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-stop-a-page-from-loading"></a><span data-ttu-id="3d464-102">方法: ページの読み込みの停止</span><span class="sxs-lookup"><span data-stu-id="3d464-102">How to: Stop a Page from Loading</span></span>
<span data-ttu-id="3d464-103">この例を呼び出す方法を示します、<xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A>ダウンロードが完了する前に、コンテンツへの移動を中断します。</span><span class="sxs-lookup"><span data-stu-id="3d464-103">This example shows how to call the <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> method to stop navigation to content before it has finished being downloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d464-104">例</span><span class="sxs-lookup"><span data-stu-id="3d464-104">Example</span></span>  
 <span data-ttu-id="3d464-105"><xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A>要求されたコンテンツのダウンロードを停止し、原因、<xref:System.Windows.Navigation.NavigationWindow.NavigationStopped>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="3d464-105"><xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> stops the download of the requested content, and causes the <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> event to be raised.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
