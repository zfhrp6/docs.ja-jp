---
title: "方法 : InkCanvas にデータをバインドする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "InkCanvas へのデータ バインディング"
  - "InkCanvas へのデータ バインディング"
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : InkCanvas にデータをバインドする
## <a name="example"></a>例  
 次の例では、バインド、<xref:System.Windows.Controls.InkCanvas.Strokes%2A>のプロパティ、 <xref:System.Windows.Controls.InkCanvas>間<xref:System.Windows.Controls.InkCanvas>します。  
  
 [!code-xml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 次の例では、バインド、 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>プロパティをデータ ソース。  
  
 [!code-xml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 次の例で&2; つ<xref:System.Windows.Controls.InkCanvas> XAML 内のオブジェクトし、他のデータ ソース間のデータ バインドを確立します。  最初の<xref:System.Windows.Controls.InkCanvas>という`ic`、2 つのデータ ソースにバインドします。  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>と<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>プロパティを`ic`にバインドされた<xref:System.Windows.Controls.ListBox>さらに、XAML で定義されている配列にバインドされているオブジェクト。  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>、 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>と<xref:System.Windows.Controls.InkCanvas.Strokes%2A>、2 番目のプロパティ<xref:System.Windows.Controls.InkCanvas>バインドは、最初に<xref:System.Windows.Controls.InkCanvas>、`ic`です。  
  
 [!code-xml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]