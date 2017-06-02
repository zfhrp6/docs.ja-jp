---
title: "方法 : Windows フォームの 1 つのイベント ハンドラーに複数のイベントを関連付ける | Microsoft Docs"
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
  - "イベント ハンドラー [Windows フォーム], 接続 (イベントを)"
  - "イベント [Windows フォーム], 接続 (単一のイベント ハンドラーに複数のイベントを)"
  - "メニュー項目, マルチキャスティング (イベント処理メソッドの)"
  - "メニュー, イベント処理メソッド (複数メニュー項目の)"
  - "Windows フォーム コントロール, イベント"
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : Windows フォームの 1 つのイベント ハンドラーに複数のイベントを関連付ける
アプリケーションのデザインによっては、1 つのイベント ハンドラーを複数のイベントに対応付ける必要があります。つまり、複数のイベントから 1 つのプロシージャを起動するようにする必要があります。  たとえば、メニュー コマンドとフォームのボタンの機能が同じ場合は、メニュー コマンドからフォームのボタンと同じイベントが発生するようにすると、大幅に作業時間を短縮できます。  これを行うには、C\# では、\[プロパティ\] ウィンドウのイベント ビューを使用します。Visual Basic コード エディターでは、`Handles`  キーワードと、**\[クラス名\]** ボックスおよび **\[メソッド名\]** ボックスを使用します。  
  
### Visual Basic で 1 つのイベント ハンドラーに複数のイベントを関連付けるには  
  
1.  フォームを右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  **\[クラス名\]** ボックスで、イベント ハンドラーが処理するコントロールを 1 つ選択します。  
  
3.  **\[メソッド名\]** ボックスで、イベント ハンドラーが処理するイベントを 1 つ選択します。  
  
4.  コード エディターによって適切なイベント ハンドラーが挿入され、対応するメソッド内にカーソルが移動します。  以下に <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベントの例を示します。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  処理対象の他のイベントを `Handles` 句に追加します。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  適切なコードをイベント ハンドラーに追加します。  
  
### C\# で 1 つのイベント ハンドラーに複数のイベントを関連付けるには  
  
1.  イベント ハンドラーを接続するコントロールを選択します。  
  
2.  \[プロパティ\] ウィンドウで、**\[イベント\]** ボタン \(![イベント ボタン](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton\_PropertiesWindow")\) をクリックします。  
  
3.  処理するイベントの名前をクリックします。  
  
4.  イベント名の横にある値セクションでドロップダウン ボタンをクリックすると、処理するイベントのメソッド シグネチャと一致する既存のイベント ハンドラーの一覧が表示されます。  
  
5.  一覧から、該当するイベント ハンドラーを選択します。  
  
     選択したイベントを既存のイベント ハンドラーに関連付けするコードが、フォームに追加されます。  
  
## 参照  
 [Windows フォーム内でのイベント ハンドラーの作成](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [イベント ハンドラーの概要](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)