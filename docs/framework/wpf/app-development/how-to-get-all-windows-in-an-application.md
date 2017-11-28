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
# <a name="how-to-get-all-windows-in-an-application"></a>方法: アプリケーションのすべてのウィンドウの取得
この例は、すべてを取得する方法を示しています。<xref:System.Windows.Window>アプリケーション内のオブジェクト。  
  
## <a name="example"></a>例  
 各インスタンス化<xref:System.Windows.Window>オブジェクトを表示するかどうかもそうでないで管理されているウィンドウの参照のコレクションが自動的に追加<xref:System.Windows.Application>から公開されていると<xref:System.Windows.Application.Windows%2A>です。  
  
 列挙できる<xref:System.Windows.Application.Windows%2A>を次のコードを使用してインスタンス化されたすべての windows を取得します。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
