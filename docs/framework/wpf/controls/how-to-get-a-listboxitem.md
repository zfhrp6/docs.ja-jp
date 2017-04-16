---
title: "方法 : ListBoxItem を取得する | Microsoft Docs"
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
  - "ListBox コントロール, 取得 (ListBoxItem を)"
  - "ListBoxItem"
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : ListBoxItem を取得する
<xref:System.Windows.Controls.ListBox> の特定のインデックス位置にある特定の <xref:System.Windows.Controls.ListBoxItem> を取得する必要がある場合は、<xref:System.Windows.Controls.ItemContainerGenerator> を使用できます。  
  
## 使用例  
 <xref:System.Windows.Controls.ListBox> とその項目の例を次に示します。  
  
 [!code-xml[ListBoxItems#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 次の例では、<xref:System.Windows.Controls.ItemContainerGenerator> の <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> プロパティ内項目のインデックスを指定してアイテムを取得する方法を示しています。  
  
 [!code-csharp[ListBoxItems#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 リスト ボックスの項目を取得したら、次の例に示すように、項目のコンテンツを表示できます。  
  
 [!code-csharp[ListBoxItems#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]