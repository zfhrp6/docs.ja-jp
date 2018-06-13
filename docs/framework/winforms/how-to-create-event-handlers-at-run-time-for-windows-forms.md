---
title: '方法 : Windows フォームで実行時にイベント ハンドラーを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 38453c751e6cc63827f3f1e9d20ad2ebdfc841d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538006"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>方法 : Windows フォームで実行時にイベント ハンドラーを作成する
Windows フォーム デザイナーを使用してイベント ハンドラーを作成する他に、実行時にもイベント ハンドラーを作成できます。 これにより、プログラムが最初に起動したときにイベント ハンドラーを接続する代わりに、コード内に記述されている条件に基づいて、実行時にイベント ハンドラーを接続できます。  
  
### <a name="to-create-an-event-handler-at-run-time"></a>実行時にイベント ハンドラーを作成するには  
  
1.  コード エディターで、イベント ハンドラーを追加するフォームを開きます。  
  
2.  処理するイベントに対応するメソッド シグネチャを持つメソッドをフォームに追加します。  
  
     処理する場合など、<xref:System.Windows.Forms.Control.Click>のイベント、<xref:System.Windows.Forms.Button>コントロールを次のようメソッドを作成するとします。  
  
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
  
3.  アプリケーションに応じて、イベント ハンドラーにコードを追加します。  
  
4.  イベント ハンドラーをどのフォームまたはコントロールに対して作成するかを指定します。  
  
5.  フォームのクラスのメソッドに、イベントを処理するためのイベント ハンドラーを指定するコードを追加します。 たとえば、次のコードには、イベント ハンドラーを指定します。`button1_Click`ハンドル、<xref:System.Windows.Forms.Control.Click>のイベント、<xref:System.Windows.Forms.Button>コントロール。  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <xref:System.ComponentModel.EventHandlerList.AddHandler%2A>上の Visual Basic のコードに示されているメソッドは、ボタンの click イベント ハンドラーを確立します。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム内でのイベント ハンドラーの作成](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [イベント ハンドラーの概要](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 [Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
