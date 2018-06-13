---
title: '方法 : ListBoxItem を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox controls [WPF], getting a ListBoxItem
- ListBoxItem [WPF]
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
ms.openlocfilehash: f1e25ce60ff5feb8fd644a5864dbd762b4b5fa39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552728"
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
