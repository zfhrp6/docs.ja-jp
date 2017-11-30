---
title: "方法: ScrollChanged イベントを処理する"
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
- ScrollViewer control [WPF], raising ScrollChanged events
- ScrollChanged events [WPF]
ms.assetid: 42c695d8-ee28-49d4-80fd-fc71e9be7f29
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b8a4f4831b8ed25eb900692e78b5e28bccb86a86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-the-scrollchanged-event"></a>方法: ScrollChanged イベントを処理する
## <a name="example"></a>例  
 この例では、処理、<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>のイベント、<xref:System.Windows.Controls.ScrollViewer>です。  
  
 A<xref:System.Windows.Documents.FlowDocument>を持つ要素<xref:System.Windows.Documents.Paragraph>部分がで定義されている[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。 ときに、<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>ユーザーとの対話のために発生するイベント、ハンドラーが呼び出されると、およびテキストを書き込む、<xref:System.Windows.Controls.TextBlock>イベントが発生したことを示します。  
  
 [!code-xaml[scrollchangedeventargsLayout#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#1)]  
[!code-xaml[scrollchangedeventargsLayout#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[scrollchangedeventargsLayout#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml.cs#3)]
 [!code-vb[scrollchangedeventargsLayout#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/scrollchangedeventargsLayout/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.ScrollViewer.ScrollChanged>  
 <xref:System.Windows.Controls.ScrollChangedEventHandler>  
 <xref:System.Windows.Controls.ScrollChangedEventArgs>
