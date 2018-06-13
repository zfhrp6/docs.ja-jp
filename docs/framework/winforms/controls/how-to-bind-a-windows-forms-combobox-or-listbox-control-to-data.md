---
title: '方法 : Windows フォームの ComboBox または ListBox コントロールをデータにバインドする '
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: 270ed1c9fab4013df72b715ce8b074d287616713
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530134"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>方法 : Windows フォームの ComboBox または ListBox コントロールをデータにバインドする 
バインドすることができます、<xref:System.Windows.Forms.ComboBox>と<xref:System.Windows.Forms.ListBox>または既存のデータを編集する、データベース内のデータの参照などのタスクを実行するデータを新しいデータを入力します。  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>ComboBox または ListBox コントロールをバインドするには  
  
1.  設定、`DataSource`プロパティをデータ ソース オブジェクト。 データ ソースには、<xref:System.Windows.Forms.BindingSource>データ、データ テーブル、データ ビュー、データセットにバインドされると、データ マネージャー、配列、または表示を実装するクラス、<xref:System.Collections.IList>インターフェイスです。 詳細については、次を参照してください。 [Windows フォームでサポートされるデータ ソース](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)です。  
  
2.  テーブルにバインドする場合は、設定、`DisplayMember`プロパティをデータ ソース内の列の名前にします。  
  
     \- または -  
  
     バインドする場合、<xref:System.Collections.IList>表示のメンバー リスト内の型のパブリック プロパティを設定します。  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    >  かどうかは、実装されていないデータ ソースにバインドされている、<xref:System.ComponentModel.IBindingList>インターフェイスなど、 <xref:System.Collections.ArrayList>、データ ソースが更新されたときに、バインドされたコントロールのデータは更新されません。 たとえばがある場合、コンボ ボックスにバインド、<xref:System.Collections.ArrayList>にデータが追加されると、 <xref:System.Collections.ArrayList>、コンボ ボックスでこれらの新しい項目は表示されません。 ただし、呼び出すことで更新するコンボ ボックスを強制することができます、<xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A>と<xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A>メソッドのインスタンスで、<xref:System.Windows.Forms.BindingContext>コントロールがバインドされるクラスです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [Windows フォームでのデータ バインディング](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [データ連結と Windows フォーム](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
