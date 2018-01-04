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
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="e97ef-102">方法 : Windows フォームのダイアログ ボックスを表示する</span><span class="sxs-lookup"><span data-stu-id="e97ef-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="e97ef-103">アプリケーションでその他の形式を表示する同じ方法では、ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="e97ef-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="e97ef-104">スタートアップ フォームは、アプリケーションの実行時に自動的に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e97ef-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="e97ef-105">2 番目のフォームまたはダイアログ ボックスをアプリケーションで表示するには、するには、読み込み、表示するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="e97ef-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="e97ef-106">同様に、フォームまたはダイアログ ボックスを非アンロードしたり非表示にコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="e97ef-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="e97ef-107">ダイアログ ボックスを表示するには</span><span class="sxs-lookup"><span data-stu-id="e97ef-107">To display a dialog box</span></span>  
  
1.  <span data-ttu-id="e97ef-108">ダイアログ ボックスを開く場合、イベント ハンドラーに移動します。</span><span class="sxs-lookup"><span data-stu-id="e97ef-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="e97ef-109">これは、メニュー コマンドを選択すると、ボタンがクリックされたときに、または、他のイベントが発生したときに発生することができます。</span><span class="sxs-lookup"><span data-stu-id="e97ef-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2.  <span data-ttu-id="e97ef-110">イベント ハンドラーでは、ダイアログ ボックスを開くコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e97ef-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="e97ef-111">この例では、ボタンのクリック イベントを使用して、ダイアログ ボックスを表示を。</span><span class="sxs-lookup"><span data-stu-id="e97ef-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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
