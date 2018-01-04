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
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>方法: ページは、ブラウザーでホストされているかどうかの判断
この例では、かどうかを<xref:System.Windows.Controls.Page>がブラウザーでホストされています。  
  
## <a name="example"></a>例  
 A<xref:System.Windows.Controls.Page>できるホストに依存しませんでき、その結果などのホストのさまざまな種類に読み込まれ、 <xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Navigation.NavigationWindow>、またはブラウザー。 これは、1 つまたは複数のページを格納していると、これは複数のスタンドアロンによって参照されていると、参照可能なライブラリ アセンブリがある場合に発生することができます ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) アプリケーションをホストします。  
  
 次の例を使用する方法を示します<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>かどうかを<xref:System.Windows.Controls.Page>がブラウザーでホストされています。  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
