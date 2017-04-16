---
title: "方法 : Windows フォームの ComboBox または ListBox コントロールをデータにバインドする  | Microsoft Docs"
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
  - "バインド コントロール, コンボ ボックス"
  - "コンボ ボックス, データ バインド"
  - "ComboBox コントロール [Windows フォーム], データ バインド"
  - "データ [Windows フォーム], バインド (コントロールに)"
  - "データ バインド, コンボ ボックス"
  - "データ バインド コントロール, Windows フォーム"
  - "リスト ボックス, データ バインド"
  - "ListBox コントロール [Windows フォーム], データ バインド"
  - "Windows フォーム コントロール, データ バインド"
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォームの ComboBox または ListBox コントロールをデータにバインドする 
<xref:System.Windows.Forms.ComboBox> および <xref:System.Windows.Forms.ListBox> をデータにバインドすると、データベースのデータの参照、新しいデータの入力、既存のデータの編集などのタスクを実行できます。  
  
### ComboBox コントロールまたは ListBox コントロールをデータ連結するには  
  
1.  `DataSource`  プロパティをデータ ソース オブジェクトに設定します。  使用できるデータ ソースには、データにバインドされた <xref:System.Windows.Forms.BindingSource>、データ テーブル、データ ビュー、データセット、データ ビュー マネージャー、配列、または <xref:System.Collections.IList> インターフェイスを実装するクラスがあります。  詳細については、「[Windows フォームがサポートするデータ ソース](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)」を参照してください。  
  
2.  テーブルにバインドする場合は、`DisplayMember`  プロパティをデータ ソースの列の名前に設定します。  
  
     または  
  
     <xref:System.Collections.IList> にバインドする場合は、表示メンバーを、リスト内の型のパブリック プロパティに設定します。  
  
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
    >  <xref:System.ComponentModel.IBindingList> インターフェイスを実装しないデータ ソース \(<xref:System.Collections.ArrayList> オブジェクトなど\) にバインドされている場合、データ ソースが更新されても、バインドされているコントロールのデータは更新されません。  たとえば、コンボ ボックスが <xref:System.Collections.ArrayList> オブジェクトにバインドされている場合は、<xref:System.Collections.ArrayList> にデータが追加されても、コンボ ボックスに新しい項目は表示されません。  ただし、コントロールがバインドされている <xref:System.Windows.Forms.BindingContext> クラスのインスタンスの <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> メソッドおよび <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> メソッドを呼び出すことによって、コンボ ボックスを強制的に更新できます。  
  
## 参照  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 [Windows フォームでのデータ バインド](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [データ連結と Windows フォーム](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)