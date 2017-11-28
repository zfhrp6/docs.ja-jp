---
title: "方法 : Windows フォーム ListView コントロールに列を追加する"
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
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8df87e62e8c19ee6e30ffdbc2a4e473b444f538
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>方法 : Windows フォーム ListView コントロールに列を追加する
詳細ビューで、<xref:System.Windows.Forms.ListView>コントロールは、各リスト項目の複数の列を表示できます。 列を使用すると、いくつかの種類の各リスト項目に関する情報をユーザーに表示します。 たとえば、ファイルのリストには、ファイル名、ファイルの種類、サイズ、およびファイルの最終更新日を表示できます。 作成した後、列の設定方法の詳細については、次を参照してください。[する方法: Windows フォーム ListView コントロールでの列にサブ項目を表示](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)です。  
  
### <a name="to-add-columns-programmatically"></a>列をプログラムで追加するには  
  
1.  コントロールの設定<xref:System.Windows.Forms.ListView.View%2A>プロパティを<xref:System.Windows.Forms.View.Details>です。  
  
2.  使用して、<xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A>メソッドのリスト ビューの<xref:System.Windows.Forms.ListView.Columns%2A>プロパティです。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ListView>  
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
