---
title: '方法: Windows フォームの DataGridViewComboBoxCell ドロップダウン リストのオブジェクトにアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 2758841031be9ca9f0a5eb5e57165191d6870e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529403"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>方法: Windows フォームの DataGridViewComboBoxCell ドロップダウン リストのオブジェクトにアクセスする
同様に、<xref:System.Windows.Forms.ComboBox>コントロール、<xref:System.Windows.Forms.DataGridViewComboBoxColumn>と<xref:System.Windows.Forms.DataGridViewComboBoxCell>型では、ドロップダウン リストに任意のオブジェクトを追加できます。 この機能により、個別のコレクションに対応するオブジェクトを格納することがなくドロップダウン リストで複雑な状態を表すことができます。  
  
 異なり、<xref:System.Windows.Forms.ComboBox>コントロール、<xref:System.Windows.Forms.DataGridView>型がない、<xref:System.Windows.Forms.ComboBox.SelectedItem%2A>現在選択されているオブジェクトを取得するためのプロパティです。 代わりに、設定する必要があります、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>または<xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>プロパティをビジネス オブジェクトのプロパティの名前にします。 選択を行ったとき、ユーザー、ビジネス オブジェクトの指定されたプロパティは、セルを設定します<xref:System.Windows.Forms.DataGridViewCell.Value%2A>プロパティです。  
  
 セルの値からビジネス オブジェクトを取得する、`ValueMember`プロパティは、ビジネス オブジェクト自体への参照を返すプロパティを示す必要があります。 したがって、ビジネス オブジェクトの種類が自分の管理下にない場合は、継承によって型を拡張することによってこのようなプロパティを追加する必要があります。  
  
 次の手順は、ビジネス オブジェクトで、ドロップダウン リストに設定して、セルからオブジェクトを取得する方法を説明<xref:System.Windows.Forms.DataGridViewCell.Value%2A>プロパティです。  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>ドロップダウン リストにビジネス オブジェクトを追加するには  
  
1.  新規作成<xref:System.Windows.Forms.DataGridViewComboBoxColumn>設定とその<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>コレクション。 列を設定する代わりに、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>ビジネス オブジェクトのコレクションにプロパティです。 その場合は、ただし、追加できません「未割り当て」ドロップダウン リストに、コレクションに対応するビジネス オブジェクトを作成します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> プロパティと <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> プロパティを設定します。 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> ドロップダウン リストに表示するビジネス オブジェクトのプロパティを示します。 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> ビジネス オブジェクトへの参照を返すプロパティを示します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  ビジネス オブジェクトの種類が、現在のインスタンスへの参照を返すプロパティが含まれていることを確認してください。 割り当てられている値は、このプロパティの名前を指定する必要があります<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>前の手順でします。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>現在選択されているビジネス オブジェクトを取得するには  
  
-   セルを取得<xref:System.Windows.Forms.DataGridViewCell.Value%2A>プロパティであり、ビジネス オブジェクトの種類にキャストします。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>例  
 完全な例では、ドロップダウン リストでビジネス オブジェクトの使用を示します。 この例で、<xref:System.Windows.Forms.DataGridView>コントロールのコレクションにバインドする`Task`オブジェクト。 各`Task`オブジェクトには、`AssignedTo`を示すプロパティを`Employee`そのタスクに現在割り当てられているオブジェクト。 `Assigned To`列が表示されます、`Name`従業員、または「未割り当て」の各プロパティの値が割り当てられている、`Task.AssignedTo`プロパティの値が`null`です。  
  
 この例の動作を表示するには、次の手順を実行します。  
  
1.  割り当てを変更、`Assigned To`ドロップ ダウン リストから別の値を選択するか、ctrl キーを押しながらコンボ ボックスのセルに 0 を押すことによって列です。  
  
2.  をクリックして`Generate Report`を現在の割り当てを表示します。 これを示しているの変更、`Assigned To`列が自動的に更新、`tasks`コレクション。  
  
3.  クリックして、`Request Status`を呼び出すボタン、 `RequestStatus` 、現在のメソッド`Employee`その行のオブジェクト。 これは、選択したオブジェクトが正常に取得されたことを示します。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
