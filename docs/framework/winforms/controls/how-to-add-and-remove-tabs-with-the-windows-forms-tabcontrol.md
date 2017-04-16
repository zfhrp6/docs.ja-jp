---
title: "方法 : Windows フォーム TabControl のタブを追加および削除する | Microsoft Docs"
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
  - "タブ ページ"
  - "TabControl コントロール [Windows フォーム], 追加と削除 (タブを)"
  - "TabPage コントロール"
  - "タブ, 追加 (ページに)"
  - "タブ, 削除 (ページから)"
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォーム TabControl のタブを追加および削除する
既定では、<xref:System.Windows.Forms.TabControl> コントロールには 2 つの <xref:System.Windows.Forms.TabPage> コントロールが含まれています。  これらのタブには <xref:System.Windows.Forms.TabControl.TabPages%2A> プロパティを通じてアクセスできます。  
  
### プログラムによってタブを追加するには  
  
-   <xref:System.Windows.Forms.TabControl.TabPages%2A> プロパティの <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> メソッドを使用します。  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### プログラムによってタブを削除するには  
  
-   選択したタブを削除するには、<xref:System.Windows.Forms.TabControl.TabPages%2A> プロパティの <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> メソッドを使用します。  
  
     または  
  
-   すべてのタブを削除するには、<xref:System.Windows.Forms.TabControl.TabPages%2A> プロパティの <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> メソッドを使用します。  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## 参照  
 [TabControl コントロールの概要](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [方法 : タブ ページにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [方法 : タブ ページを無効化する](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [方法 : Windows フォーム TabControl の表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)