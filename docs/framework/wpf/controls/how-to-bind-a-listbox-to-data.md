---
title: "方法 : ListBox にデータをバインドする | Microsoft Docs"
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
  - "バインド (データを), ListBox コントロール"
  - "データ バインディング, ListBox コントロール"
  - "ListBox コントロール, バインド (データを)"
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : ListBox にデータをバインドする
アプリケーション開発者は、各 <xref:System.Windows.Controls.ListBoxItem> のコンテンツを個別に指定することなく、<xref:System.Windows.Controls.ListBox> コントロールを作成することができます。  データ バインディングを使用して、個々の項目にデータをバインドできます。  
  
 *Colors* というデータ ソースにデータをバインドすることにより、<xref:System.Windows.Controls.ListBoxItem> 要素を設定する <xref:System.Windows.Controls.ListBox> の作成方法を次の例に示します。  この場合、<xref:System.Windows.Controls.ListBoxItem> タグを使用して各項目のコンテンツを指定する必要はありません。  
  
## 使用例  
 [!code-xml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## 参照  
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.Controls.ListBoxItem>   
 [コントロール](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)