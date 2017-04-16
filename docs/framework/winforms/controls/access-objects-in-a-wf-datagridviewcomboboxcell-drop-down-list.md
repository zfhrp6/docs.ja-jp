---
title: "方法 : Windows フォームの DataGridViewComboBoxCell ドロップダウン リストのオブジェクトにアクセスする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コンボ ボックス, アクセス (DataGridViewComboBoxCell ドロップダウン リストのオブジェクトに)"
  - "コンボ ボックス, DataGridView コントロール内の"
  - "DataGridView コントロール [Windows フォーム], アクセス (コンボ ボックス セルのオブジェクトに)"
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : Windows フォームの DataGridViewComboBoxCell ドロップダウン リストのオブジェクトにアクセスする
<xref:System.Windows.Forms.ComboBox> コントロールと同様に、<xref:System.Windows.Forms.DataGridViewComboBoxColumn> 型と <xref:System.Windows.Forms.DataGridViewComboBoxCell> 型を使用すると、任意のオブジェクトをドロップダウン リストに追加できます。  この機能を使用して、対応するオブジェクトを別のコレクションに格納しなくても、ドロップダウン リストで複雑な状態を表現できます。  
  
 <xref:System.Windows.Forms.ComboBox> コントロールとは異なり、<xref:System.Windows.Forms.DataGridView> 型には、現在選択しているオブジェクトを取得する <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> プロパティがありません。  代わりに、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=fullName> プロパティまたは <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=fullName> プロパティを、ビジネス オブジェクトのプロパティ名に設定する必要があります。  ユーザーが選択すると、指定したビジネス オブジェクトのプロパティによってセルの <xref:System.Windows.Forms.DataGridViewCell.Value%2A> プロパティが設定されます。  
  
 セルの値からビジネス オブジェクトを取得するには、`ValueMember` プロパティで、ビジネス オブジェクト自体への参照を返すプロパティを指定する必要があります。  そのため、使用するコントロールにその型のビジネス オブジェクトがない場合、継承によって型を拡張することでそのようなプロパティを追加します。  
  
 次の手順では、ビジネス オブジェクトでドロップダウン リストを作成する方法と、セルの <xref:System.Windows.Forms.DataGridViewCell.Value%2A> プロパティからオブジェクトを取得する方法の例を示します。  
  
### ビジネス オブジェクトをドロップダウン リストに追加するには  
  
1.  新しい <xref:System.Windows.Forms.DataGridViewComboBoxColumn> を作成し、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> コレクションを作成します。  または、列の <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> プロパティをビジネス オブジェクトのコレクションに設定します。  ただし、この場合、対応するビジネス オブジェクトをコレクション内に作成せずに、"未割り当て" をドロップダウン リストに追加することはできません。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> プロパティおよび <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> プロパティを設定します。  <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>は、ドロップダウン リストに表示するビジネス オブジェクトのプロパティを示します。  <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> は、ビジネス オブジェクトへの参照を返すプロパティを示します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  ビジネス オブジェクト型に、現在のインスタンスへの参照を返すプロパティが含まれていることを確認します。  このプロパティには、前の手順で <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> に割り当てた値と同じ名前を付けます。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### 現在選択されているビジネス オブジェクトを取得するには  
  
-   セルの <xref:System.Windows.Forms.DataGridViewCell.Value%2A> プロパティを取得し、ビジネス オブジェクト型にキャストします。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## 使用例  
 完全な例では、ドロップダウン リストでのビジネス オブジェクトの使用法を示します。  この例では、<xref:System.Windows.Forms.DataGridView> コントロールは `Task` オブジェクトのコレクションにバインドされます。  各 `Task` オブジェクトには、現在そのタスクに割り当てられている `Employee` オブジェクトを示す `AssignedTo` プロパティがあります。  `Assigned To` 列には、割り当てられた各従業員の `Name` プロパティ値が表示されます。`Task.AssignedTo` プロパティ値が `null` の場合、"未割り当て" が表示されます。  
  
 この例の動作を表示するには、次の手順を実行します。  
  
1.  ドロップダウン リストの他の値を選択するか、コンボ ボックス セルで Ctrl キーを押しながら 0 キーを押して、`Assigned To` 列の割り当てを変更します。  
  
2.  `Generate Report` をクリックして現在の割り当てを表示します。  これで、`Assigned To` 列を変更すると、自動的に `tasks` コレクションが更新されることがわかります。  
  
3.  `Request Status` ボタンをクリックし、その行で現在の `Employee` オブジェクトの `RequestStatus` メソッドを呼び出します。  これで、選択したオブジェクトが正常に取得されることがわかります。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System アセンブリと System.Windows.Forms アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ComboBox>   
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)