---
title: "方法 : Windows フォーム パネルの背景を設定する | Microsoft Docs"
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
  - "背景色, Windows フォーム Panel コントロール"
  - "背景イメージ, Windows フォーム Panel コントロール"
  - "色, Windows フォーム Panel コントロール"
  - "Panel コントロール [Windows フォーム], バックグラウンド"
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォーム パネルの背景を設定する
Windows フォーム <xref:System.Windows.Forms.Panel> コントロールでは、背景色と背景イメージの両方を表示できます。  ラベルやオプション ボタンなど、表示されるコントロールの背景色を設定するには、<xref:System.Windows.Forms.Control.BackColor%2A> プロパティを使用します。  <xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティを設定していない場合は、<xref:System.Windows.Forms.Control.BackColor%2A> で選択した色でパネル全体が塗りつぶされます。  <xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティを設定している場合は、コントロールの背景にイメージが表示されます。  
  
### プログラムによって背景を設定するには  
  
1.  パネルの <xref:System.Windows.Forms.Control.BackColor%2A> プロパティに <xref:System.Drawing.Color?displayProperty=fullName> 型の値を設定します。  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2.  <xref:System.Drawing.Image?displayProperty=fullName> クラスの <xref:System.Drawing.Image.FromFile%2A> メソッドを使用して、パネルの <xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティを設定します。  
  
    ```vb  
    ' You should replace the bolded image   
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
  
    ```  
  
    ```csharp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
  
    ```  
  
    ```cpp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.Control.BackColor%2A>   
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>   
 [Panel コントロール](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)   
 [Panel コントロールの概要](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)