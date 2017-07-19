---
title: "方法 : Windows フォームで実行時にイベント ハンドラーを作成する | Microsoft Docs"
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
  - "Button コントロール [Windows フォーム], イベント ハンドラー"
  - "イベント ハンドラー, 作成"
  - "例 [Windows フォーム], イベント処理"
  - "実行時に, 作成 (イベント ハンドラーを)"
  - "Windows フォーム, イベント処理"
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォームで実行時にイベント ハンドラーを作成する
Windows フォーム デザイナーを使用してイベント ハンドラーを作成する他に、実行時にもイベント ハンドラーを作成できます。  これによって、プログラムが最初に起動したときにイベント ハンドラーを接続する代わりに、コード内に記述されている条件に基づいて、実行時にイベント ハンドラーを接続できます。  
  
### 実行時にイベント ハンドラーを作成するには  
  
1.  コード エディターで、イベント ハンドラーを追加するフォームを開きます。  
  
2.  処理するイベントに対応するメソッド シグネチャを持つメソッドをフォームに追加します。  
  
     たとえば、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベントを処理する場合は、次のようなメソッドを作成します。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)  
       ' Add event handler code here.  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
    // Add event handler code here.  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          // Add event handler code here.  
       }  
    ```  
  
3.  アプリケーションの必要に応じて、イベント ハンドラーにコードを追加します。  
  
4.  イベント ハンドラーをどのフォームまたはコントロールに対して作成するかを指定します。  
  
5.  フォームのクラスのメソッドに、イベントを処理するためのイベント ハンドラーを指定するコードを追加します。  たとえば、次のコードは、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベントを処理する `button1_Click` イベント ハンドラーを指定します。  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     上の Visual Basic コードの <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> メソッドは、ボタンに対するクリック イベント ハンドラーを作成しています。  
  
## 参照  
 [Windows フォーム内でのイベント ハンドラーの作成](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [イベント ハンドラーの概要](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)