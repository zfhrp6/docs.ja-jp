---
title: "方法 : カスタム コンテキスト メニューを RichTextBox に配置する | Microsoft Docs"
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
  - "配置のカスタム コンテキスト メニュー"
  - "配置 (カスタム コンテキスト メニューを)"
  - "RichTextBox コントロール、カスタム コンテキスト メニューの配置"
  - "配置のコンテキスト メニュー"
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : カスタム コンテキスト メニューを RichTextBox に配置する
この例では、カスタム コンテキスト メニューの配置、 <xref:System.Windows.Controls.RichTextBox>します。  
  
 カスタム コンテキスト メニューを実装する場合、 **RichTextBox**、コンテキスト メニューの配置を処理を担当します。  中央に既定では、カスタム コンテキスト メニューを開く、 **RichTextBox**します。  
  
## <a name="example"></a>例  
 既定の配置の動作を上書きするには、追加のリスナー、 <xref:System.Windows.FrameworkContentElement.ContextMenuOpening>イベントです。  次の例では、このプログラムで実行する方法を示します。  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>例  
 次の例は、対応する実装を示します<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>イベント リスナー。  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>関連項目  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)