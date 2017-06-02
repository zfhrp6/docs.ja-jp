---
title: "方法 : Windows フォーム ColorDialog コンポーネントの表示形式を変更する | Microsoft Docs"
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
  - "色のダイアログ ボックス, 構成 (表示形式を)"
  - "ColorDialog コンポーネント, 例"
  - "ColorDialog コンポーネント, 書式指定 (外観を)"
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォーム ColorDialog コンポーネントの表示形式を変更する
複数のプロパティを使用して、Windows フォーム <xref:System.Windows.Forms.ColorDialog> コンポーネントの表示形式を設定できます。  ダイアログ ボックスは 2 つの部分に分かれています。基本色が表示される部分と、ユーザーがカスタム カラーを定義できる部分です。  
  
 ほとんどのプロパティでは、ユーザーがダイアログ ボックスで選択できる色が制限されています。  <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> プロパティが `true` に設定されている場合、ユーザーはカスタム カラーを定義できます。  <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> プロパティは、カスタム カラーを定義するためにダイアログ ボックスが拡張されている場合に `true` になります。ダイアログ ボックスが拡張されていない場合、ユーザーは \[色の作成\] ボタンをクリックする必要があります。  <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> プロパティが `true` に設定されていると、ダイアログ ボックスには基本色のセットの中で使用できるすべての色が表示されます。  <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> プロパティが `true` に設定されていると、ユーザーはディザー カラーを選択できず、純色だけを選択できます。  
  
 <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> プロパティが `true` に設定されていると、ダイアログ ボックスに \[ヘルプ\] ボタンが表示されます。  ユーザーが \[ヘルプ\] をクリックすると、<xref:System.Windows.Forms.ColorDialog> コンポーネントの <xref:System.Windows.Forms.CommonDialog.HelpRequest> イベントが発生します。  
  
### カラー ダイアログ ボックスの表示形式を設定するには  
  
1.  <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> プロパティ、<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>、プロパティ、<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> プロパティ、および <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> プロパティを任意の値に設定します。  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ColorDialog>   
 [ColorDialog コンポーネント](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)   
 [ColorDialog コンポーネントの概要](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)