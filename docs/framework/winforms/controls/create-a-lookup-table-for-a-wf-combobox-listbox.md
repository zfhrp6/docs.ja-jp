---
title: '方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールのルックアップ テーブルを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: 212cc229d8a496be11c84e30dbf3a0eedb952006
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529380"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールのルックアップ テーブルを作成する
Windows フォーム上ではわかりやすい形式でデータを表示し、一方プログラムにはより意味のある形式でデータを格納すると便利な場合があります。 たとえば、食品の注文書の場合、リスト ボックスにメニュー項目が名前で表示されます。 一方、注文を記録するデータ テーブルには、食品を表す一意の ID 番号が含まれることになります。 次の表は、食品の注文書データを格納および表示する方法の例を示しています。  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|ItemID|数量|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|名前|  
|--------|----------|  
|12|ポテト|  
|13|チキン|  
  
 このシナリオでは、1 つのテーブルで**OrderDetailsTable**、表示と保存には、実際の情報を格納します。 しかし、スペースを節約するために、これはかなり謎めいた方法で実行されます。 その他のテーブル**ItemTable**、どの id 番号がする食品名、および実際の食品の注文について nothing と同じ外観に関連する情報のみが含まれています。  
  
 **ItemTable**に接続されている、 <xref:System.Windows.Forms.ComboBox>、 <xref:System.Windows.Forms.ListBox>、または<xref:System.Windows.Forms.CheckedListBox>3 つのプロパティを使用してコントロール。 `DataSource`プロパティには、このテーブルの名前が含まれています。 `DisplayMember`プロパティには、コントロール (食品名) に表示する、テーブルのデータ列が含まれています。 `ValueMember`プロパティに格納されている情報 (ID 番号) を持つ、テーブルのデータ列が含まれています。  
  
 **OrderDetailsTable**が接続されているコントロールを使用してアクセス、そのバインディング コレクションにより、<xref:System.Windows.Forms.Control.DataBindings%2A>プロパティです。 データ ソース内の特定のデータ メンバー (ID 番号の列) には、コントロールのプロパティを接続するバインディング オブジェクトをコレクションに追加すると (、 **OrderDetailsTable**)。 コントロールで選択がなされる際、このテーブルはフォーム入力が保存される場所です。  
  
### <a name="to-create-a-lookup-table"></a>ルックアップ テーブルを作成するには  
  
1.  フォームに <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox>、または <xref:System.Windows.Forms.CheckedListBox> コントロールを追加します。  
  
2.  データ ソースに接続します。  
  
3.  2 つのテーブル間のデータ リレーションシップを確立します。 参照してください[DataRelation オブジェクトの概要](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192)です。  
  
4.  次のプロパティを設定します。 これらはコードまたはデザイナーで設定できます。  
  
    |プロパティ|設定|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|どの ID 番号がどの項目に相当するかについての情報を含むテーブル。 これは、上記のシナリオで`ItemTable`です。|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|コントロールに表示するデータ ソース テーブルの列。 これは、上記のシナリオで`"Name"`(コードで設定するには引用符を使用)。|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|格納された情報を含むデータ ソース テーブルの列。 これは、上記のシナリオで`"ID"`(コードで設定するには引用符を使用)。|  
  
5.  プロシージャで <xref:System.Windows.Forms.ControlBindingsCollection> クラスの <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> メソッドを呼び出して、フォーム入力を記録するテーブルにコントロールの <xref:System.Windows.Forms.ListControl.SelectedValue%2A> プロパティをバインドします。 行うことができますもこのコードでは、代わりに、デザイナーでコントロールのアクセスすることによって<xref:System.Windows.Forms.Control.DataBindings%2A>プロパティに、**プロパティ**ウィンドウです。 これは、上記のシナリオで`OrderDetailsTable`、列が`"ItemID"`です。  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>関連項目  
 [データ連結と Windows フォーム](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [ListBox コントロールの概要](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [ComboBox コントロールの概要](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [CheckedListBox コントロールの概要](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
