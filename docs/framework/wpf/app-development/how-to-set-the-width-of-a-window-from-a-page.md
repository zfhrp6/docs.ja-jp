---
title: "方法: ページから、ウィンドウの幅を設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc9843d4a0f76547b76698a9686b5c4936baa322
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="ff20b-102">方法: ページから、ウィンドウの幅を設定</span><span class="sxs-lookup"><span data-stu-id="ff20b-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="ff20b-103">この例から、ウィンドウの幅を設定する方法を示しています、<xref:System.Windows.Controls.Page>です。</span><span class="sxs-lookup"><span data-stu-id="ff20b-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff20b-104">例</span><span class="sxs-lookup"><span data-stu-id="ff20b-104">Example</span></span>  
 <span data-ttu-id="ff20b-105">A<xref:System.Windows.Controls.Page>を設定して、そのホスト ウィンドウの幅を設定できます<xref:System.Windows.Controls.Page.WindowWidth%2A>です。</span><span class="sxs-lookup"><span data-stu-id="ff20b-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="ff20b-106">このプロパティにより、<xref:System.Windows.Controls.Page>をホストするウィンドウの種類の明示的な知識がないようにします。</span><span class="sxs-lookup"><span data-stu-id="ff20b-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff20b-107">使用してウィンドウの幅を設定する<xref:System.Windows.Controls.Page.WindowWidth%2A>、<xref:System.Windows.Controls.Page>ウィンドウの子でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ff20b-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
