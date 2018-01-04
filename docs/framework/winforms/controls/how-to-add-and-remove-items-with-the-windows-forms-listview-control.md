---
title: "方法 : Windows フォーム ListView コントロールで項目を追加および削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a66d0da6e010efbad77e9544267d1b6af9d1233
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>方法 : Windows フォーム ListView コントロールで項目を追加および削除する
Windows フォームに項目を追加するプロセス<xref:System.Windows.Forms.ListView>コントロールは、主にアイテムを指定して、プロパティを割り当てます。 追加またはリスト項目の削除は、いつでも実行できます。  
  
### <a name="to-add-items-programmatically"></a>プログラムからアイテムを追加するには  
  
1.  使用して、<xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A>のメソッド、<xref:System.Windows.Forms.ListView.Items%2A>プロパティです。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>項目をプログラムで削除するには  
  
1.  使用して、<xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>または<xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A>のメソッド、<xref:System.Windows.Forms.ListView.Items%2A>プロパティです。 <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>メソッドは、1 つの項目を削除;<xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A>メソッドは、一覧からすべての項目を削除します。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.ListView>  
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
