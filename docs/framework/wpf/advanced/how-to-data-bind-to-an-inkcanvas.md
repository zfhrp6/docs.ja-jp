---
title: "方法 : InkCanvas にデータをバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c8c4f558386edd8da213f8a8af75b6a4c6a98b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a>方法 : InkCanvas にデータをバインドする
## <a name="example"></a>例  
 次の例では、バインド、<xref:System.Windows.Controls.InkCanvas.Strokes%2A>のプロパティ、<xref:System.Windows.Controls.InkCanvas>別<xref:System.Windows.Controls.InkCanvas>です。  
  
 [!code-xaml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 次の例では、バインド、<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>データ ソースへのプロパティです。  
  
 [!code-xaml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 次の例では、2 つ宣言<xref:System.Windows.Controls.InkCanvas>XAML 内のオブジェクトし、他のデータ ソース間のデータ バインディングを確立します。  最初の<xref:System.Windows.Controls.InkCanvas>という`ic`は 2 つのデータ ソースにバインドします。  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>と<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>プロパティを`ic`にバインドされた<xref:System.Windows.Controls.ListBox>オブジェクトで、さらに、XAML で定義されている配列にバインドされます。  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>、 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>、および<xref:System.Windows.Controls.InkCanvas.Strokes%2A>、2 番目のプロパティ<xref:System.Windows.Controls.InkCanvas>バインドは、最初に<xref:System.Windows.Controls.InkCanvas>、`ic`です。  
  
 [!code-xaml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
