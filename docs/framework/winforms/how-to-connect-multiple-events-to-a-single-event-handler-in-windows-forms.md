---
title: '方法 : Windows フォームの 1 つのイベント ハンドラーに複数のイベントを関連付ける'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: 527a76376a4c1d5ad051f4768ca2bd42c3548b3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538581"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>方法 : Windows フォームの 1 つのイベント ハンドラーに複数のイベントを関連付ける
アプリケーションの設計にする必要がありますを単一のイベント ハンドラーを使用して、複数のイベントまたは同じ手順を実行する複数のイベント。 たとえば、時間を短縮するように、フォーム上のボタンは、同じ機能を公開している場合に、同じイベントを発生させるためのメニュー コマンドでは多くの場合です。 C# の場合、[プロパティ] ウィンドウのイベント ビューを使用するかを使用してこれを行う、`Handles`キーワードおよび**クラス名**と**メソッド名**ドロップダウン ボックスでは、Visual Basic コード エディター。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Visual Basic での 1 つのイベント ハンドラーに複数のイベントを接続するには  
  
1.  フォームを右クリックして選択**コードの表示**です。  
  
2.  **クラス名**ドロップダウン ボックスで、イベント ハンドラーが処理するコントロールのいずれかを選択します。  
  
3.  **メソッド名**ドロップダウン ボックスで、イベント ハンドラーが処理するイベントのいずれかを選択します。  
  
4.  コード エディターでは、適切なイベント ハンドラーを挿入し、メソッド内でカーソルを配置します。 次の例では、<xref:System.Windows.Forms.Control.Click>イベントを<xref:System.Windows.Forms.Button>コントロール。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  他のイベントが表示する処理を追加、`Handles`句。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  イベント ハンドラーに適切なコードを追加します。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>C# での 1 つのイベント ハンドラーに複数のイベントを接続するには  
  
1.  イベント ハンドラーを接続するコントロールを選択します。  
  
2.  [プロパティ] ウィンドウ、**イベント**ボタン (![イベント ボタン](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow"))。  
  
3.  処理するイベントの名前をクリックします。  
  
4.  イベント名の横の [値] セクションでは、処理するイベントのメソッド シグネチャに一致する既存のイベント ハンドラーの一覧を表示するドロップダウン ボタンをクリックします。  
  
5.  一覧から適切なイベント ハンドラーを選択します。  
  
     コードは、既存のイベント ハンドラーにイベントをバインドするフォームに追加されます。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム内でのイベント ハンドラーの作成](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [イベント ハンドラーの概要](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
