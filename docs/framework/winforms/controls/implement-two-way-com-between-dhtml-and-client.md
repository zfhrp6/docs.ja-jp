---
title: "方法 : DHTML コードとクライアント アプリケーション コード間の双方向の通信を実装する"
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
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ad99683f0e41e64a42032a9d64e589723fa8ed4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="523d0-102">方法 : DHTML コードとクライアント アプリケーション コード間の双方向の通信を実装する</span><span class="sxs-lookup"><span data-stu-id="523d0-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>
<span data-ttu-id="523d0-103"><xref:System.Windows.Forms.WebBrowser> コントロールを使用して、既存の動的 HTML (DHTML) Web アプリケーション コードを Windows フォーム クライアント アプリケーションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="523d0-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="523d0-104">これは、DHTML ベースのコントロールの作成にかなりの開発時間を投資し、既存のコードを再作成せずに Windows フォームの機能が豊富なユーザー インターフェイスを利用したい場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="523d0-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>  
  
 <span data-ttu-id="523d0-105"><xref:System.Windows.Forms.WebBrowser> コントロールでは、<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> プロパティと <xref:System.Windows.Forms.WebBrowser.Document%2A> プロパティを通じて、クライアント アプリケーション コードと Web ページ内のスクリプト コードの間の双方向の通信を実装できます。</span><span class="sxs-lookup"><span data-stu-id="523d0-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="523d0-106">また、<xref:System.Windows.Forms.WebBrowser> コントロールを構成して、Web コントロールをアプリケーション フォームのその他のコントロールとシームレスに統合し、DHTML 実装を非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="523d0-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="523d0-107">コントロールをシームレスに統合するには、背景色と視覚スタイルが残りのフォームと一致するように表示されるページの書式を設定し、<xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>、<xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>、および <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> の各プロパティを使用して標準的なブラウザーの機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="523d0-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="523d0-108">Windows フォーム アプリケーションで DHTML を埋め込むには</span><span class="sxs-lookup"><span data-stu-id="523d0-108">To embed DHTML in your Windows Forms application</span></span>  
  
1.  <span data-ttu-id="523d0-109"><xref:System.Windows.Forms.WebBrowser> コントロールの <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> プロパティを `false` に設定し、<xref:System.Windows.Forms.WebBrowser> コントロールがその上にドロップされたファイルを開かないようにします。</span><span class="sxs-lookup"><span data-stu-id="523d0-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  <span data-ttu-id="523d0-110">コントロールの <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> プロパティを `false` に設定し、ユーザーが右クリックしたときに、<xref:System.Windows.Forms.WebBrowser> コントロールでショートカット メニューが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="523d0-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  <span data-ttu-id="523d0-111">コントロールの <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> プロパティを `false` に設定して、<xref:System.Windows.Forms.WebBrowser> コントロールがショートカット キーに応答しないようにします。</span><span class="sxs-lookup"><span data-stu-id="523d0-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  <span data-ttu-id="523d0-112">フォームのコンストラクターまたは <xref:System.Windows.Forms.Form.Load> イベント ハンドラーの <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="523d0-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
     <span data-ttu-id="523d0-113">次のコードは、スクリプト オブジェクトに、フォーム クラス自体を使用します。</span><span class="sxs-lookup"><span data-stu-id="523d0-113">The following code uses the form class itself for the scripting object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="523d0-114">コンポーネント オブジェクト モデル (COM) は、スクリプト オブジェクトにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="523d0-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="523d0-115">フォームが COM から参照できるようにするには<xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性をフォーム クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="523d0-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  <span data-ttu-id="523d0-116">スクリプト コードが使用するアプリケーション コードにパブリック プロパティまたはメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="523d0-116">Implement public properties or methods in your application code that your script code will use.</span></span>  
  
     <span data-ttu-id="523d0-117">たとえば、スクリプト オブジェクトにフォーム クラスを使用する場合、次のコードをフォーム クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="523d0-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  <span data-ttu-id="523d0-118">指定されたオブジェクトのパブリック プロパティおよびメソッドへのアクセスには、スクリプト コードで `window.external` オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="523d0-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>  
  
     <span data-ttu-id="523d0-119">次の HTML コードは、ボタンのクリックからスクリプト オブジェクトでメソッドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="523d0-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="523d0-120">コントロールの <xref:System.Windows.Forms.WebBrowser.Navigate%2A> メソッドを使用して読み込む、またはコントロールの <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> プロパティに割り当てる HTML ドキュメントの BODY 要素に、このコードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="523d0-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  <span data-ttu-id="523d0-121">アプリケーション コードが使用するスクリプト コードに関数を実装します。</span><span class="sxs-lookup"><span data-stu-id="523d0-121">Implement functions in your script code that your application code will use.</span></span>  
  
     <span data-ttu-id="523d0-122">次の HTML SCRIPT 要素は、関数の例を提供しています。</span><span class="sxs-lookup"><span data-stu-id="523d0-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="523d0-123">コントロールの <xref:System.Windows.Forms.WebBrowser.Navigate%2A> メソッドを使用して読み込む、またはコントロールの <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> プロパティに割り当てる HTML ドキュメントの HEAD 要素に、このコードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="523d0-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  <span data-ttu-id="523d0-124"><xref:System.Windows.Forms.WebBrowser.Document%2A> プロパティを使用して、クライアント アプリケーション コードからスクリプト コードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="523d0-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>  
  
     <span data-ttu-id="523d0-125">たとえば、次のコードをボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに追加します。</span><span class="sxs-lookup"><span data-stu-id="523d0-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. <span data-ttu-id="523d0-126">DHTML のデバッグが完了したら、コントロールの <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> プロパティを `true` に設定して、<xref:System.Windows.Forms.WebBrowser> コントロールがスクリプト コードの問題のエラー メッセージを表示しないようにします。</span><span class="sxs-lookup"><span data-stu-id="523d0-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="523d0-127">例</span><span class="sxs-lookup"><span data-stu-id="523d0-127">Example</span></span>  
 <span data-ttu-id="523d0-128">次の完全なコード例は、この機能を理解するために使用できるデモ アプリケーションを示します。</span><span class="sxs-lookup"><span data-stu-id="523d0-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="523d0-129">HTML コードは、個別の HTML ファイルから読み込まれる代わりに、<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> プロパティを通じて <xref:System.Windows.Forms.WebBrowser> コントロールに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="523d0-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="523d0-130">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="523d0-130">Compiling the Code</span></span>  
 <span data-ttu-id="523d0-131">このコードには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="523d0-131">This code requires:</span></span>  
  
-   <span data-ttu-id="523d0-132">System アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="523d0-132">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="523d0-133">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="523d0-133">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="523d0-134">また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="523d0-134">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="523d0-135">「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="523d0-135">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523d0-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="523d0-136">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="523d0-137">WebBrowser コントロール</span><span class="sxs-lookup"><span data-stu-id="523d0-137">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
