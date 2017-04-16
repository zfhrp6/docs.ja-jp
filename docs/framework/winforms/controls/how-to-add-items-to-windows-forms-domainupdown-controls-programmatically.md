---
title: "方法 : Windows フォーム DomainUpDown コントロールにプログラムで項目を追加する | Microsoft Docs"
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
  - "DomainUpDown コントロール [Windows フォーム], 追加 (アイテムを)"
  - "スピン ボタン コントロール, 追加 (アイテムを)"
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォーム DomainUpDown コントロールにプログラムで項目を追加する
Windows フォームの <xref:System.Windows.Forms.DomainUpDown> コントロールにコードで項目を追加できます。  <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> クラスの <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> メソッドまたは<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> メソッドを呼び出して、コントロールの <xref:System.Windows.Forms.DomainUpDown.Items%2A> プロパティに項目を追加します。  <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> メソッドは、コレクションの最後に項目を追加します。<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> メソッドは、指定された位置に項目を追加します。  
  
### 新しい項目を追加するには  
  
1.  <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> メソッドを使用して、項目のリストの最後に項目を追加します。  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     または  
  
2.  <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> メソッドを使用して、リスト内の指定した位置に項目を挿入します。  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.DomainUpDown>   
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=fullName>   
 <xref:System.Collections.ArrayList.Insert%2A?displayProperty=fullName>   
 [DomainUpDown コントロール](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)   
 [DomainUpDown コントロールの概要](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)