---
title: "方法 : Windows フォームの境界線を変更する | Microsoft Docs"
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
  - "Windows フォーム, 変更 (境界線を)"
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォームの境界線を変更する
Windows フォームの外観や動作を決定する際にはさまざまな境界線スタイルを選択できます。  <xref:System.Windows.Forms.Form.FormBorderStyle%2A> プロパティを変更して、フォームのサイズ変更動作を制御できます。  また、<xref:System.Windows.Forms.Form.FormBorderStyle%2A> を設定すると、キャプション バーの表示方法や、キャプション バーに表示されるボタンを変更できます。  詳細については、「<xref:System.Windows.Forms.FormBorderStyle>」を参照してください。  
  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] では、このタスクに対する広範なサポートが用意されています。  
  
 「[方法 : デザイナーを使用して Windows フォームの境界線を変更する](http://msdn.microsoft.com/library/yettzh3e%20\(v=vs.110\))」も参照してください。  
  
### プログラムで Windows フォームの境界線スタイルを設定するには  
  
-   <xref:System.Windows.Forms.Form.FormBorderStyle%2A> プロパティを任意のスタイルに設定します。  フォーム `DlgBx1`  の境界線スタイルを <xref:System.Windows.Forms.FormBorderStyle> に設定するコード例は、次のとおりです。  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     「[方法 : デザイン時にダイアログ ボックスを作成する](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))」も参照してください。  
  
     また、**\[最小化\]** ボタンまたは **\[最大化\]** ボタンをフォームに配置できる境界線スタイルを選択した場合は、この 2 つのボタンのいずれか、または両方の機能を有効にするかどうかを指定できます。  これらのボタンは、ユーザーの操作感を細かく調節する場合に便利です。  既定では、**\[最小化\]** ボタンと **\[最大化\]** ボタンが有効になっています。**\[プロパティ\]** ウィンドウで、これらの機能を有効にするかどうかを制御できます。  
  
## 参照  
 <xref:System.Windows.Forms.FormBorderStyle>   
 <xref:System.Windows.Forms.FormBorderStyle>   
 [Windows フォームについて](../../../docs/framework/winforms/getting-started-with-windows-forms.md)