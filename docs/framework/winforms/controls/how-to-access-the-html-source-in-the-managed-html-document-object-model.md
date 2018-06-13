---
title: '方法 : マネージ HTML DOM (Document Object Model) の HTML ソースにアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: 49a50bdf5ea0f24d712458c739b7829ee73d157a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527814"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a><span data-ttu-id="ff3a4-102">方法 : マネージ HTML DOM (Document Object Model) の HTML ソースにアクセスする</span><span class="sxs-lookup"><span data-stu-id="ff3a4-102">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="ff3a4-103"><xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> コントロールの <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> プロパティおよび <xref:System.Windows.Forms.WebBrowser> プロパティは、現在のドキュメントが最初に表示されたときに存在した HTML を返します。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-103">The <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> properties on the <xref:System.Windows.Forms.WebBrowser> control return the HTML of the current document as it existed when it was first displayed.</span></span> <span data-ttu-id="ff3a4-104">ただし、<xref:System.Windows.Forms.HtmlElement.AppendChild%2A> や <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A> のようなメソッド呼び出しやプロパティ呼び出しを使用してページを変更すると、<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> や <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> を呼び出したときにこれらの変更は表示されません。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-104">However, if you modify the page using method and property calls such as <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> and <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, these changes will not appear when you call <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span></span> <span data-ttu-id="ff3a4-105">DOM の最新の HTML ソースを取得するには、HTML 要素の <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> プロパティを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-105">To obtain the most up-to-date HTML source for the DOM, you must call the <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> property on the HTML element.</span></span>  
  
 <span data-ttu-id="ff3a4-106">次の手順では、動的ソースを取得し、別のショートカット メニューに表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-106">The following procedure shows how to retrieve the dynamic source and display it in a separate shortcut menu.</span></span>  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a><span data-ttu-id="ff3a4-107">OuterHtml プロパティを使用した動的ソースの取得</span><span class="sxs-lookup"><span data-stu-id="ff3a4-107">Retrieving the dynamic source with the OuterHtml property</span></span>  
  
1.  <span data-ttu-id="ff3a4-108">新しい Windows フォーム アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-108">Create a new Windows Forms application.</span></span> <span data-ttu-id="ff3a4-109">1 つの開始<xref:System.Windows.Forms.Form>、および呼び出し`Form1`です。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-109">Start with a single <xref:System.Windows.Forms.Form>, and call it `Form1`.</span></span>  
  
2.  <span data-ttu-id="ff3a4-110">ホスト、 <xref:System.Windows.Forms.WebBrowser> 、Windows フォーム アプリケーションで制御し、名前を付けます`WebBrowser1`です。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-110">Host the <xref:System.Windows.Forms.WebBrowser> control in your Windows Forms application, and name it `WebBrowser1`.</span></span> <span data-ttu-id="ff3a4-111">詳細については、次を参照してください。[する方法: Web ブラウザーの機能を Windows フォーム アプリケーションに追加](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-111">For more information, see [How to: Add Web Browser Capabilities to a Windows Forms Application](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span></span>  
  
3.  <span data-ttu-id="ff3a4-112">1 秒あたりの作成<xref:System.Windows.Forms.Form>と呼ばれる、アプリケーションで`CodeForm`です。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-112">Create a second <xref:System.Windows.Forms.Form> in your application called `CodeForm`.</span></span>  
  
4.  <span data-ttu-id="ff3a4-113">追加、<xref:System.Windows.Forms.RichTextBox>に制御を`CodeForm`設定とその<xref:System.Windows.Forms.Control.Dock%2A>プロパティを`Fill`です。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-113">Add a <xref:System.Windows.Forms.RichTextBox> control to `CodeForm` and set its <xref:System.Windows.Forms.Control.Dock%2A> property to `Fill`.</span></span>  
  
5.  <span data-ttu-id="ff3a4-114">パブリック プロパティを作成`CodeForm`と呼ばれる`Code`です。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-114">Create a public property on `CodeForm` called `Code`.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  <span data-ttu-id="ff3a4-115">追加、<xref:System.Windows.Forms.Button>という名前のコントロール`Button1`を<xref:System.Windows.Forms.Form>、監視する、<xref:System.Windows.Forms.Control.Click>イベント。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-115">Add a <xref:System.Windows.Forms.Button> control named `Button1` to your <xref:System.Windows.Forms.Form>, and monitor for the <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="ff3a4-116">イベントの監視の詳細については、「[イベント](../../../../docs/standard/events/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-116">For details on monitoring events, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
7.  <span data-ttu-id="ff3a4-117"><xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-117">Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ff3a4-118">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="ff3a4-118">Robust Programming</span></span>  
 <span data-ttu-id="ff3a4-119"><xref:System.Windows.Forms.WebBrowser.Document%2A> の値を取得する前に、必ずテストしてください。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-119">Always test the value of <xref:System.Windows.Forms.WebBrowser.Document%2A> before attempting to retrieve it.</span></span> <span data-ttu-id="ff3a4-120">現在のページの読み込みが完了していない場合、<xref:System.Windows.Forms.WebBrowser.Document%2A> またはその 1 つ以上の子オブジェクトが初期化されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ff3a4-120">If the current page is not finished loading, <xref:System.Windows.Forms.WebBrowser.Document%2A> or one or more of its child objects may not be initialized.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff3a4-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff3a4-121">See Also</span></span>  
 [<span data-ttu-id="ff3a4-122">マネージ HTML DOM (Document Object Model) の使用</span><span class="sxs-lookup"><span data-stu-id="ff3a4-122">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)  
 [<span data-ttu-id="ff3a4-123">WebBrowser コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="ff3a4-123">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
