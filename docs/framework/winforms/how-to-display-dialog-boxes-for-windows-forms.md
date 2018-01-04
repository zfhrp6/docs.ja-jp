---
title: "方法 : Windows フォームのダイアログ ボックスを表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46e4d019bbd586c0ed46794f55c65da7bcc657f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>方法 : Windows フォームのダイアログ ボックスを表示する
アプリケーションでその他の形式を表示する同じ方法では、ダイアログ ボックスを表示します。 スタートアップ フォームは、アプリケーションの実行時に自動的に読み込みます。 2 番目のフォームまたはダイアログ ボックスをアプリケーションで表示するには、するには、読み込み、表示するコードを記述します。 同様に、フォームまたはダイアログ ボックスを非アンロードしたり非表示にコードを記述します。  
  
### <a name="to-display-a-dialog-box"></a>ダイアログ ボックスを表示するには  
  
1.  ダイアログ ボックスを開く場合、イベント ハンドラーに移動します。 これは、メニュー コマンドを選択すると、ボタンがクリックされたときに、または、他のイベントが発生したときに発生することができます。  
  
2.  イベント ハンドラーでは、ダイアログ ボックスを開くコードを追加します。 この例では、ボタンのクリック イベントを使用して、ダイアログ ボックスを表示を。  
  
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
