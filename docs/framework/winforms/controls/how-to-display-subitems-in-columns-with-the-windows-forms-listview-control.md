---
title: '方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: efee926301bc358bb7645ba67826f412c0d0dbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532508"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する
Windows フォーム<xref:System.Windows.Forms.ListView>コントロールは、追加のテキスト、または詳細ビュー内の各項目のサブ項目を表示できます。 最初の列には、たとえば社員数、項目のテキストが表示されます。 2 番目、3 番目、およびそれ以降の列に、最初は第 2 に、表示し、後続の関連するサブ項目です。  
  
### <a name="to-add-subitems-to-a-list-item"></a>リスト項目にサブ項目を追加するには  
  
1.  必要なすべての列を追加します。 最初の列は、項目の表示されるため<xref:System.Windows.Forms.ListView.Text%2A>プロパティ、する必要がありますが、サブ項目よりも 1 つ以上の列です。 列を追加する方法については、次を参照してください。[する方法: Windows フォーム ListView コントロールに列の追加](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)です。  
  
2.  呼び出す、<xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A>メソッドによって返されるコレクションの<xref:System.Windows.Forms.ListViewItem.SubItems%2A>項目のプロパティです。 次のコード例では、employee name フィールドとリスト アイテムの部門を設定します。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>関連項目  
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [方法: Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [方法: Windows フォーム ListView コントロールに列を追加する](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [方法: Windows フォーム ListView コントロールのアイコンを表示する](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
