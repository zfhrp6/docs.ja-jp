---
title: "方法 : カスタム コンテキスト メニューを RichTextBox に配置する"
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
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1c0a4fd8d2df15dcca2d9d1751f3089922d9a5ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a>方法 : カスタム コンテキスト メニューを RichTextBox に配置する
この例では、配置用のカスタムのコンテキスト メニュー、<xref:System.Windows.Controls.RichTextBox>です。  
  
 **RichTextBox** のカスタム コンテキスト メニューを実装する場合、コンテキスト メニューの配置の処理を行う必要があります。  既定では、**RichTextBox** の中央でカスタム コンテキスト メニューが開きます。  
  
## <a name="example"></a>例  
 既定の配置の動作を無効にする追加のリスナーを<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>イベント。  次の例では、プログラムによってこれを実行する方法を説明します。  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>例  
 次の例は、対応する実装を示します<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>イベント リスナー。  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>関連項目  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)
