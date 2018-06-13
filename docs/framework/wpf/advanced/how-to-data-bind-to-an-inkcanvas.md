---
title: '方法 : InkCanvas にデータをバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
ms.openlocfilehash: 4081ae7dd6854934804062cfce60d10106c1e1d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543171"
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
