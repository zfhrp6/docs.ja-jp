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
# <a name="how-to-get-all-windows-in-an-application"></a>方法: アプリケーションのすべてのウィンドウの取得
この例は、すべてを取得する方法を示しています。<xref:System.Windows.Window>アプリケーション内のオブジェクト。  
  
## <a name="example"></a>例  
 各インスタンス化<xref:System.Windows.Window>オブジェクトを表示するかどうかもそうでないで管理されているウィンドウの参照のコレクションが自動的に追加<xref:System.Windows.Application>から公開されていると<xref:System.Windows.Application.Windows%2A>です。  
  
 列挙できる<xref:System.Windows.Application.Windows%2A>を次のコードを使用してインスタンス化されたすべての windows を取得します。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
