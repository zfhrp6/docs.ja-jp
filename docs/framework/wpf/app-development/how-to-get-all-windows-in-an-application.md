---
title: "方法: アプリケーションのすべてのウィンドウの取得"
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
helpviewer_keywords: window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8577817f62ece1465f9c7577f3e1b7ff5ecefe44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="69763-102">方法: アプリケーションのすべてのウィンドウの取得</span><span class="sxs-lookup"><span data-stu-id="69763-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="69763-103">この例は、すべてを取得する方法を示しています。<xref:System.Windows.Window>アプリケーション内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="69763-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69763-104">例</span><span class="sxs-lookup"><span data-stu-id="69763-104">Example</span></span>  
 <span data-ttu-id="69763-105">各インスタンス化<xref:System.Windows.Window>オブジェクトを表示するかどうかもそうでないで管理されているウィンドウの参照のコレクションが自動的に追加<xref:System.Windows.Application>から公開されていると<xref:System.Windows.Application.Windows%2A>です。</span><span class="sxs-lookup"><span data-stu-id="69763-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="69763-106">列挙できる<xref:System.Windows.Application.Windows%2A>を次のコードを使用してインスタンス化されたすべての windows を取得します。</span><span class="sxs-lookup"><span data-stu-id="69763-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
