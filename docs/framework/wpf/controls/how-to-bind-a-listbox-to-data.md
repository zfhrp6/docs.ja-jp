---
title: "方法 : ListBox にデータをバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4701fe99231e115eb8cb14f7c1e5e003928bc5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-listbox-to-data"></a>方法 : ListBox にデータをバインドする
アプリケーション開発者が作成できる<xref:System.Windows.Controls.ListBox>コントロールの内容を指定しないで<xref:System.Windows.Controls.ListBoxItem>とは別にします。 データ バインディングを使用すると、個々 の項目にデータをバインドします。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.ListBox>に適用する、<xref:System.Windows.Controls.ListBoxItem>要素と呼ばれるデータ ソースへのデータ バインディングによって*色*です。 ここで使用する必要はありません<xref:System.Windows.Controls.ListBoxItem>タグを各項目のコンテンツを指定します。  
  
## <a name="example"></a>例  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [コントロール](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
