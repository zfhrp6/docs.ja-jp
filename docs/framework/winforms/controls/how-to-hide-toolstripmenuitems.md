---
title: "方法 : ToolStripMenuItems を非表示にする | Microsoft Docs"
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
  - "非表示 (メニュー項目を)"
  - "メニュー項目, 非表示"
  - "メニュー, 非表示 (メニュー項目を)"
  - "MenuStrip コントロール [Windows フォーム], 非表示 (メニュー項目を)"
  - "ToolStripMenuItem, 非表示"
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : ToolStripMenuItems を非表示にする
メニュー項目を非表示にすると、アプリケーションのユーザー インターフェイスを制御したり、ユーザーが使用するコマンドを制限したりできます。  通常、メニュー項目がすべて使用不可能なメニューは、メニュー全体を非表示にする必要があります。  使用できないメニューを非表示にすることによって、ユーザーの混乱を避けることができます。  さらに、メニューまたはメニュー項目の非表示と無効化の両方が必要となることがあります。これは非表示にしただけでは、ショートカット キーを使用してメニュー コマンドにアクセスできてしまうためです。  
  
### プログラムによって、メニュー項目を非表示にするには  
  
-   メニュー項目のプロパティを設定するメソッド内で、コードを追加して <xref:System.Windows.Forms.ToolStripItem.Visible%2A> プロパティを `false` に設定します。  
  
    ```vb  
    MenuItem3.Visible = False  
  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>   
 <xref:System.Windows.Forms.MenuStrip>   
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)   
 [方法 : ToolStripMenuItems を無効にする](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)