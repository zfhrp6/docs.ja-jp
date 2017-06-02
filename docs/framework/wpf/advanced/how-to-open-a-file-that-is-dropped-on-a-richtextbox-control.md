---
title: "方法: RichTextBox コントロール上にドロップしたファイルを開く | Microsoft Docs"
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
  - "ドラッグ アンド ドロップ [WPF], 開く (ドロップされたファイルを)"
  - "ドラッグ アンド ドロップ [WPF], RichTextBox"
  - "RichTextBox [WPF], ドラッグ アンド ドロップ"
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法: RichTextBox コントロール上にドロップしたファイルを開く
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、<xref:System.Windows.Controls.TextBox>、<xref:System.Windows.Controls.RichTextBox>、および <xref:System.Windows.Documents.FlowDocument> のすべてのコントロールにドラッグ アンド ドロップの機能が組み込まれています。  この組み込み機能により、コントロール内およびコントロール間でのテキストのドラッグ アンド ドロップが有効になります。  ただし、コントロールでファイルをドロップしても、そのファイルを開くことはできません。  また、これらのコントロールは、ドラッグ アンド ドロップ イベントを処理済みとしてマークします。  したがって、既定では、独自のイベント ハンドラーを追加して、ドロップしたファイルを開く機能を設定することはできません。  
  
 これらのコントロールでドラッグ アンド ドロップ イベントに関するその他の処理ができるようにするには、<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> メソッドを使用して、ドラッグ アンド ドロップ イベント用のイベント ハンドラーを追加します。  イベント ルート上の他の要素により既に処理済みとしてマークされているルーティング イベントに対し、指定したハンドラーが呼び出されるようにするには、`handledEventsToo` パラメーターを `true` に設定します。  
  
> [!TIP]
>  ドラッグ アンド ドロップ イベントのプレビュー バージョンを処理し、プレビュー イベントを処理済みとしてマークすることにより、<xref:System.Windows.Controls.TextBox>、<xref:System.Windows.Controls.RichTextBox>、および <xref:System.Windows.Documents.FlowDocument> に組み込まれたドラッグ アンド ドロップの機能を置き換えることができます。  ただし、この操作により組み込みのドラッグ アンド ドロップ機能が無効になるので、この操作はお勧めできません。  
  
## 使用例  
 次の例は、<xref:System.Windows.Controls.RichTextBox> で <xref:System.Windows.DragDrop.DragOver> イベントおよび <xref:System.Windows.DragDrop.Drop> イベント用のハンドラーを追加する方法を示します。  この例では、<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> メソッドを使用し、`handledEventsToo` パラメーターを `true` に設定することにより、<xref:System.Windows.Controls.RichTextBox> がこれらのイベントを処理済みとしてマークした場合でも、イベント ハンドラーが呼び出されるようにします。  イベント ハンドラーのコードにより、<xref:System.Windows.Controls.RichTextBox> でドロップしたテキスト ファイルを開く機能が加わります。  
  
 この例をテストするには、テキスト ファイルまたはリッチ テキスト形式 \(RTF\) のファイルを、Windows エクスプローラーから <xref:System.Windows.Controls.RichTextBox> にドラッグします。  ファイルが <xref:System.Windows.Controls.RichTextBox> で開きます。  ファイルをドロップする前に Shift キーを押すと、そのファイルはプレーンテキストとして開きます。  
  
 [!code-xml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]