---
title: '方法 : Web フォーム アプリケーションでイベントを利用する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [.NET Framework], Web Forms
- Web Forms controls, and events
- event handlers [.NET Framework], Web Forms
- events [.NET Framework], consuming
- Web Forms, event handling
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b8af7b3894c010d5a7a4c712efe2458a6bb2a50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="0405a-102">方法 : Web フォーム アプリケーションでイベントを利用する</span><span class="sxs-lookup"><span data-stu-id="0405a-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="0405a-103">ASP.NET Web フォーム アプリケーションの一般的なシナリオとして、Web ページにコントロールを入力し、ユーザーがクリックしたコントロールに基づいて特定のアクションを実行するというものがあります。</span><span class="sxs-lookup"><span data-stu-id="0405a-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="0405a-104">たとえば、<xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> コントロールは、ユーザーが Web ページでそれをクリックすると、イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="0405a-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="0405a-105">そのイベントを処理することで、アプリケーションはそのボタン クリックに最適なアプリケーション ロジックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0405a-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="0405a-106">Web ページ上のボタン クリック イベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="0405a-106">To handle a button click event on a webpage</span></span>  
  
1.  <span data-ttu-id="0405a-107"><xref:System.Web.UI.WebControls.Button> コントロールを含む ASP.NET Web フォーム ページ (Web ページ) を作成します。このコントロールの `OnClick` 値には、次の手順で定義するメソッドの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="0405a-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  <span data-ttu-id="0405a-108"><xref:System.Web.UI.WebControls.Button.Click> イベント デリゲート シグネチャに一致し、`OnClick` 値に定義した名前を含むイベント ハンドラーを定義します。</span><span class="sxs-lookup"><span data-stu-id="0405a-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     <span data-ttu-id="0405a-109"><xref:System.Web.UI.WebControls.Button.Click> イベントはデリゲート タイプに <xref:System.EventHandler> クラスを、イベント データに <xref:System.EventArgs> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0405a-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="0405a-110">ASP.NET ページ フレームワークは、<xref:System.EventHandler> のインスタンスを作成し、<xref:System.Web.UI.WebControls.Button> インスタンスの <xref:System.Web.UI.WebControls.Button.Click> イベントにこのデリゲート インスタンスを追加するコードを自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="0405a-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3.  <span data-ttu-id="0405a-111">手順 2 で定義したイベント ハンドラー メソッドで、イベントの発生時に必要となるアクションを実行するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0405a-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0405a-112">参照</span><span class="sxs-lookup"><span data-stu-id="0405a-112">See Also</span></span>  
 [<span data-ttu-id="0405a-113">イベント</span><span class="sxs-lookup"><span data-stu-id="0405a-113">Events</span></span>](../../../docs/standard/events/index.md)
