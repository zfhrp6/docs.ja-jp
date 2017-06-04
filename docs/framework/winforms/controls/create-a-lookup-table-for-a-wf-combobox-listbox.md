---
title: "方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールのルックアップ テーブルを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "CheckedListBox コントロール [Windows フォーム], 作成 (ルックアップ テーブルを)"
  - "コンボ ボックス, ルックアップ テーブル"
  - "ComboBox コントロール [Windows フォーム], ルックアップ テーブル"
  - "リスト ボックス, ルックアップ テーブル"
  - "ListBox コントロール [Windows フォーム], 作成 (ルックアップ テーブルを)"
  - "ListBox コントロール [Windows フォーム], ルックアップ テーブル"
  - "ルックアップ テーブル"
  - "ルックアップ テーブル, 作成 (コントロールの)"
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールのルックアップ テーブルを作成する
Windows フォーム上ではわかりやすい形式でデータを表示し、一方プログラムにはより意味のある形式でデータを格納すると便利な場合があります。  たとえば、食品の注文書の場合、リスト ボックスにメニュー項目が名前で表示されます。  一方、注文を記録するデータ テーブルには、食品を表す一意の ID 番号が含まれることになります。  次の表は、食品の注文書データを格納および表示する方法の例を示しています。  
  
### OrderDetailsTable  
  
|OrderID|ItemID|数量|  
|-------------|------------|--------|  
|4085|12|1|  
|4086|13|3|  
  
### ItemTable  
  
|ID|名前|  
|--------|--------|  
|12|ポテト|  
|13|チキン|  
  
 このシナリオでは、表示と保存に関係する実際の情報が、OrderDetailsTable という 1 つのテーブルに格納されます。  しかし、スペースを節約するために、これはかなり謎めいた方法で実行されます。  もう一方のテーブル \(OrdersTable\) には、どの ID 番号がどの食品名に相当するかという見かけ上の情報のみが含まれ、実際の食品の注文についての情報はありません。  
  
 ItemTable は、3 つのプロパティを介して <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox>、または <xref:System.Windows.Forms.CheckedListBox> コントロールに接続されます。   `DataSource`  プロパティには、このテーブルの名前が含まれます。   `DisplayMember` プロパティには、コントロール \(食品名\) に表示する、そのテーブルのデータ列が含まれます。   `ValueMember`  プロパティには、格納された情報 \(ID 番号\) が入った、そのテーブルのデータ列が含まれます。  
  
 OrderDetailsTable は、<xref:System.Windows.Forms.Control.DataBindings%2A> プロパティを介してアクセスされるそのバインディング コレクションにより、コントロールに接続されます。  バインディング オブジェクトをコレクションに追加すると、データ ソース \(OrderDetailsTable\) 内の特定のデータ メンバー \(ID 番号の列\) にコントロール プロパティが接続されます。  コントロールで選択がなされる際、このテーブルはフォーム入力が保存される場所です。  
  
### ルックアップ テーブルを作成するには  
  
1.  フォームに <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox>、または <xref:System.Windows.Forms.CheckedListBox> コントロールを追加します。  
  
2.  データ ソースに接続します。  
  
3.  2 つのテーブル間のデータ リレーションシップを確立します。  「[DataRelation オブジェクトの概要](../Topic/Introduction%20to%20DataRelation%20Objects.md)」を参照してください。  
  
4.  次のプロパティを設定します。  これらはコードまたはデザイナーで設定できます。  
  
    |プロパティ|設定|  
    |-----------|--------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|どの ID 番号がどの項目に相当するかについての情報を含むテーブル。  上記のシナリオでは、これは  `ItemTable` です。|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|コントロールに表示するデータ ソース テーブルの列。  上記のシナリオでは、これは  `"Name"`  です \(コードで設定する場合は引用符を使用\)。|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|格納された情報を含むデータ ソース テーブルの列。  上記のシナリオでは、これは  `"ID"`  です \(コードで設定する場合は引用符を使用\)。|  
  
5.  プロシージャで <xref:System.Windows.Forms.ControlBindingsCollection> クラスの <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> メソッドを呼び出して、フォーム入力を記録するテーブルにコントロールの <xref:System.Windows.Forms.ListControl.SelectedValue%2A> プロパティをバインドします。  この操作は、コードでなくデザイナーでも可能です。その場合は、\[**プロパティ**\] ウィンドウでコントロールの <xref:System.Windows.Forms.Control.DataBindings%2A> プロパティにアクセスします。  上記のシナリオでは、これは  `OrderDetailsTable` であり、列は  `"ItemID"` です。  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
  
    ```  
  
## 参照  
 [データ連結と Windows フォーム](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [ListBox コントロールの概要](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)   
 [ComboBox コントロールの概要](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)   
 [CheckedListBox コントロールの概要](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)   
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)