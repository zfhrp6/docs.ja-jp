---
title: "方法 : ListBoxItem を取得する"
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
- ListBox controls [WPF], getting a ListBoxItem
- ListBoxItem [WPF]
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e014dc05e24b5337e8e448451244633cb8ed0ff1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-a-listboxitem"></a>方法 : ListBoxItem を取得する
固有の仕様を取得する必要がある場合<xref:System.Windows.Controls.ListBoxItem>で特定のインデックス、 <xref:System.Windows.Controls.ListBox>、使用することができます、<xref:System.Windows.Controls.ItemContainerGenerator>です。  
  
## <a name="example"></a>例  
 次の例は、<xref:System.Windows.Controls.ListBox>とその項目。  
  
 [!code-xaml[ListBoxItems#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 次の例は、内の項目のインデックスを指定して、項目を取得する方法を示します、<xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A>のプロパティ、<xref:System.Windows.Controls.ItemContainerGenerator>です。  
  
 [!code-csharp[ListBoxItems#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 リスト ボックス項目を取得した後は、次の例で示すように、項目の内容を表示できます。  
  
 [!code-csharp[ListBoxItems#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]
