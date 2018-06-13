---
title: '方法: アプリケーションのすべてのウィンドウの取得'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 476905899f5f7d573a16ba876c72f28ea34bbf9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545492"
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="0d94b-102">方法: アプリケーションのすべてのウィンドウの取得</span><span class="sxs-lookup"><span data-stu-id="0d94b-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="0d94b-103">この例は、すべてを取得する方法を示しています。<xref:System.Windows.Window>アプリケーション内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0d94b-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d94b-104">例</span><span class="sxs-lookup"><span data-stu-id="0d94b-104">Example</span></span>  
 <span data-ttu-id="0d94b-105">各インスタンス化<xref:System.Windows.Window>オブジェクトを表示するかどうかもそうでないで管理されているウィンドウの参照のコレクションが自動的に追加<xref:System.Windows.Application>から公開されていると<xref:System.Windows.Application.Windows%2A>です。</span><span class="sxs-lookup"><span data-stu-id="0d94b-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="0d94b-106">列挙できる<xref:System.Windows.Application.Windows%2A>を次のコードを使用してインスタンス化されたすべての windows を取得します。</span><span class="sxs-lookup"><span data-stu-id="0d94b-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
