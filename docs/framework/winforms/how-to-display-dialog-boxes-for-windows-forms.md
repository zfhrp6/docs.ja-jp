---
title: "方法 : Windows フォームのダイアログ ボックスを表示する | Microsoft Docs"
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
  - "ダイアログ ボックス, 表示 (Windows フォームの)"
  - "Windows フォームのダイアログ ボックス, 表示"
  - "Windows フォーム, 呼び出し (フォームからの他のフォームの)"
  - "Windows フォーム, 表示"
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : Windows フォームのダイアログ ボックスを表示する
ダイアログ ボックスは、アプリケーションで表示されるその他のフォームと同じ方法で表示されます。  スタートアップ フォームは、アプリケーションの実行時に自動的に読み込まれます。  別のフォームまたはダイアログ ボックスをアプリケーションで表示するには、フォームまたはダイアログ ボックスを読み込んで表示するコードを作成します。  同様に、フォームまたはダイアログ ボックスを非表示にするには、アンロードまたは非表示にするコードを作成します。  
  
### ダイアログ ボックスを表示するには  
  
1.  ダイアログ ボックスを開くために使用するイベント ハンドラーに移動します。  ダイアログ ボックスを開くイベントは、メニュー コマンドが選択されたとき、ボタンがクリックされたとき、または他のイベントが発生したときに発生します。  
  
2.  イベント ハンドラーに、ダイアログ ボックスを表示するコードを追加します。  次の例では、ボタン クリック イベントを使用してダイアログ ボックスを表示します。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
  
    ```  
  
    ```cpp  
    private:   
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```