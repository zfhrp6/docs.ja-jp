---
title: "方法 : コントロールのコレクションに対して実行時にコントロールを追加または削除する | Microsoft Docs"
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
  - "コレクション, 追加 (アイテムを)"
  - "コントロール [Windows フォーム], 追加 (コレクションを使用して)"
  - "コントロール [Windows フォーム], 削除 (コレクションを使用して)"
  - "コントロールのコレクション"
  - "実行時に, 追加 (コントロールを)"
  - "実行時に, 削除 (コントロールを)"
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : コントロールのコレクションに対して実行時にコントロールを追加または削除する
アプリケーション開発における一般的なタスクの 1 つに、フォーム上のコンテナー コントロール \(<xref:System.Windows.Forms.Panel> や <xref:System.Windows.Forms.GroupBox> などのコントロール、またはフォーム自体\) へのコントロールの追加および削除があります。  デザイン時には、パネルまたはグループ ボックスにコントロールを直接ドラッグできます。  実行時には、これらのコンテナー コントロールは `Controls` コレクションを保持します。それにより、現在どのコントロールが含まれているかを追跡します。  
  
> [!NOTE]
>  次のコード例は、内部にコントロールのコレクションを保持するすべてのコントロールに適用されます。  
  
### プログラムによって、コレクションにコントロールを追加するには  
  
1.  追加するコントロールのインスタンスを作成します。  
  
2.  新規コントロールのプロパティを設定します。  
  
3.  このコントロールを親コントロールの `Controls` コレクションに追加します。  
  
     次に示すのは、<xref:System.Windows.Forms.Button> コントロールのインスタンスを作成する方法のコード例です。  このコード例では、フォームに <xref:System.Windows.Forms.Panel> コントロールがあり、作成するボタンのイベント処理メソッド `NewPanelButton_Click` が既に存在することが必要です。  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code   
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {   
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code   
       // below is used as an example. Substite the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### プログラムによって、コレクションからコントロールを削除するには  
  
1.  イベントからイベント ハンドラーを削除します。  [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] では、[RemoveHandler Statement](../../../../ocs/visual-basic/language-reference/statements/removehandler-statement.md) キーワードを使用し、[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] では、[\-\= 演算子](../Topic/-=%20Operator%20\(C%23%20Reference\)2.md) を使用します。  
  
2.  `Remove` メソッドを使用して、パネルの `Controls` コレクションから目的のコントロールを削除します。  
  
3.  <xref:System.Windows.Forms.Control.Dispose%2A> メソッドを呼び出して、そのコントロールによって使用されていたすべてのリソースを解放します。  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of   
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _   
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of   
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.   
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.Panel>   
 [Panel コントロール](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)