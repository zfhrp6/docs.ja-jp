---
title: "方法 : Windows フォームの NumericUpDown コントロールの書式を設定する | Microsoft Docs"
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
  - "NumericUpDown コントロール [Windows フォーム], 書式指定 (値を)"
  - "アップダウン コントロール, 書式設定 (数値を)"
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォームの NumericUpDown コントロールの書式を設定する
Windows フォームの <xref:System.Windows.Forms.NumericUpDown> コントロールで値をどのように表示するかを設定できます。  <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> プロパティは、小数点以下の桁数を指定します。既定値は 0 です。  <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> プロパティは、10 進値の 3 桁ごとに区切り記号を挿入するかどうかを指定します。既定値は `false` です。  <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> プロパティが `true` の場合、コントロールの値は 10 進形式ではなく 16 進形式で表示されます。既定では `false` です。  
  
### 数値の形式を指定するには  
  
-   <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> プロパティを整数に設定し、<xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> プロパティを `true` または `false` に設定して、10 進の値を表示します。  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     または  
  
-   <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> プロパティを `true` に設定して、16 進の値を表示します。  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    >  フォーム上の値が 16 進で表示されている場合でも、<xref:System.Windows.Forms.NumericUpDown.Value%2A> プロパティに対して実行するテストはすべて 10 進の値をテストします。  
  
## 参照  
 <xref:System.Windows.Forms.NumericUpDown>   
 [NumericUpDown コントロール](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)   
 [NumericUpDown コントロールの概要](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)