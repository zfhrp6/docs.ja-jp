---
title: "方法 : Windows フォーム ErrorProvider コンポーネントで DataSet 内にエラーを表示する | Microsoft Docs"
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
  - "エラー メッセージ, 表示 (データセット内の)"
  - "ErrorProvider コンポーネント [Windows フォーム], データセット エラー"
  - "エラー [Windows フォーム], データセット エラー"
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォーム ErrorProvider コンポーネントで DataSet 内にエラーを表示する
Windows フォームの <xref:System.Windows.Forms.ErrorProvider> コンポーネントを使用すると、データセットなどのデータ ソース内の列エラーを表示できます。  <xref:System.Windows.Forms.ErrorProvider> コンポーネントでデータ エラーをフォームに表示する場合、コンポーネントをコントロールに直接関連付ける必要はありません。  データ ソースに連結すると、そのデータ ソースに連結されたすべてのコントロールの隣に、エラー アイコンを表示できるようになります。  
  
> [!NOTE]
>  エラー プロバイダーの <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> プロパティおよび <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> プロパティを実行時に変更する場合は、<xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> メソッドを使用して競合を避ける必要があります。  
  
### データ エラーを表示するには  
  
1.  データ テーブルの特定の列にコンポーネントを連結します。  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
  
    ```  
  
2.  <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> プロパティをフォームに設定します。  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
  
    ```  
  
3.  現在のレコードの位置に、列エラーのある行を設定します。  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
  
    ```  
  
## 参照  
 [ErrorProvider コンポーネントの概要](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)   
 [方法 : Windows フォーム ErrorProvider コンポーネントを使用してフォーム妥当性検査でエラー アイコンを表示する](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)