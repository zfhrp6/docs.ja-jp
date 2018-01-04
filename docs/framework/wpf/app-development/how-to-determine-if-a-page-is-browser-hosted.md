---
title: "方法: ページは、ブラウザーでホストされているかどうかの判断"
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
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd8a8b8c3bea291afbe41e0c36e0d708bff3ef57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="c2b24-102">方法: ページは、ブラウザーでホストされているかどうかの判断</span><span class="sxs-lookup"><span data-stu-id="c2b24-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="c2b24-103">この例では、かどうかを<xref:System.Windows.Controls.Page>がブラウザーでホストされています。</span><span class="sxs-lookup"><span data-stu-id="c2b24-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2b24-104">例</span><span class="sxs-lookup"><span data-stu-id="c2b24-104">Example</span></span>  
 <span data-ttu-id="c2b24-105">A<xref:System.Windows.Controls.Page>できるホストに依存しませんでき、その結果などのホストのさまざまな種類に読み込まれ、 <xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Navigation.NavigationWindow>、またはブラウザー。</span><span class="sxs-lookup"><span data-stu-id="c2b24-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="c2b24-106">これは、1 つまたは複数のページを格納していると、これは複数のスタンドアロンによって参照されていると、参照可能なライブラリ アセンブリがある場合に発生することができます ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) アプリケーションをホストします。</span><span class="sxs-lookup"><span data-stu-id="c2b24-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) host applications.</span></span>  
  
 <span data-ttu-id="c2b24-107">次の例を使用する方法を示します<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>かどうかを<xref:System.Windows.Controls.Page>がブラウザーでホストされています。</span><span class="sxs-lookup"><span data-stu-id="c2b24-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="c2b24-108">参照</span><span class="sxs-lookup"><span data-stu-id="c2b24-108">See Also</span></span>  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
