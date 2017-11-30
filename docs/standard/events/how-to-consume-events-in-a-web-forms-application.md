---
title: "方法 : Web フォーム アプリケーションでイベントを利用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bdb0a6be309f27348ba13bf93fd5aedd3c66a792
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="29ce7-102">方法 : Web フォーム アプリケーションでイベントを利用する</span><span class="sxs-lookup"><span data-stu-id="29ce7-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="29ce7-103">コントロールと web ページを作成し、ユーザーがクリックしたコントロールに基づく特定のアクションを実行する ASP.NET Web フォーム アプリケーションで一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="29ce7-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="29ce7-104">たとえば、<xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType>コントロールをユーザーが web ページでクリックしたときにイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="29ce7-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="29ce7-105">イベントを処理することによって、アプリケーションは、そのボタンをクリックし、適切なアプリケーション ロジックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="29ce7-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="29ce7-106">Web ページ上のボタン クリック イベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="29ce7-106">To handle a button click event on a webpage</span></span>  
  
1.  <span data-ttu-id="29ce7-107">ASP.NET Web フォーム ページ (web ページ) を作成、<xref:System.Web.UI.WebControls.Button>と制御、`OnClick`値は、次の手順で定義するメソッドの名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="29ce7-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  <span data-ttu-id="29ce7-108">一致するイベント ハンドラーを定義する、<xref:System.Web.UI.WebControls.Button.Click>イベントのデリゲート シグネチャし名前を持つ、に対して定義されている、`OnClick`値。</span><span class="sxs-lookup"><span data-stu-id="29ce7-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="29ce7-109"><xref:System.Web.UI.WebControls.Button.Click>イベントを使用して、<xref:System.EventHandler>はデリゲート型のクラスと<xref:System.EventArgs>イベント データ クラスです。</span><span class="sxs-lookup"><span data-stu-id="29ce7-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="29ce7-110">ASP.NET ページ フレームワークのインスタンスを作成するコードを自動的に生成する<xref:System.EventHandler>をこのデリゲート インスタンスを追加し、<xref:System.Web.UI.WebControls.Button.Click>のイベント、<xref:System.Web.UI.WebControls.Button>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="29ce7-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3.  <span data-ttu-id="29ce7-111">イベント ハンドラー メソッドを手順 2. で定義されているは、イベントが発生したときに必要なすべてのアクションを実行するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="29ce7-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ce7-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="29ce7-112">See Also</span></span>  
 [<span data-ttu-id="29ce7-113">イベント</span><span class="sxs-lookup"><span data-stu-id="29ce7-113">Events</span></span>](../../../docs/standard/events/index.md)
