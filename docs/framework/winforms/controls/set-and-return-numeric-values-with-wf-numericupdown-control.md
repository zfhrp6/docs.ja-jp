---
title: "方法 : Windows フォームの NumericUpDown コントロールを使用して数値を設定および取得する | Microsoft Docs"
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
  - "数値, Windows フォーム"
  - "NumericUpDown コントロール [Windows フォーム], 設定と取得 (値の)"
  - "Windows フォーム コントロール, NumericUpDown"
  - "Windows フォーム, 数値"
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォームの NumericUpDown コントロールを使用して数値を設定および取得する
Windows フォームの <xref:System.Windows.Forms.NumericUpDown> コントロールの数値は、<xref:System.Windows.Forms.NumericUpDown.Value%2A> プロパティによって決定されます。  他のプロパティと同様に、このコントロールの値に対する条件テストを記述できます。  <xref:System.Windows.Forms.NumericUpDown.Value%2A> プロパティを設定した後は、プロパティを操作するコードを記述して値を直接調整するか、または、<xref:System.Windows.Forms.NumericUpDown.UpButton%2A> メソッドおよび <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> メソッドを呼び出すことができます。  
  
### 数値を設定するには  
  
1.  コードまたは \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.NumericUpDown.Value%2A> プロパティに値を割り当てます。  
  
    ```vb  
    NumericUpDown1.Value = 55  
  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     または  
  
2.  <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> メソッドまたは <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> メソッドを呼び出して、<xref:System.Windows.Forms.NumericUpDown.Increment%2A> プロパティに指定された量だけ値を増加または減少させます。  
  
    ```vb  
    NumericUpDown1.UpButton()  
  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### 数値を取得するには  
  
-   コードで <xref:System.Windows.Forms.NumericUpDown.Value%2A> プロパティにアクセスします。  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.NumericUpDown>   
 <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=fullName>   
 [NumericUpDown コントロール](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)   
 [NumericUpDown コントロールの概要](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)