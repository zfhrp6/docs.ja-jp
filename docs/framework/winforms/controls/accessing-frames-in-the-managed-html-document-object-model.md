---
title: "マネージ HTML DOM (Document Object Model) へのアクセス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8766e33f0fb253d532ff7161ed0a1e7842d0c50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a><span data-ttu-id="cb16e-102">マネージ HTML DOM (Document Object Model) へのアクセス</span><span class="sxs-lookup"><span data-stu-id="cb16e-102">Accessing Frames in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="cb16e-103">一部の HTML ドキュメントが不在で構成される*フレーム*、または独自の個別の HTML ドキュメントを持つウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="cb16e-103">Some HTML documents are composed out of *frames*, or windows that can hold their own distinct HTML documents.</span></span> <span data-ttu-id="cb16e-104">フレームを使用すると、ページ内に 1 つ以上の静的な部分 (ナビゲーション バーなど) があり、その他のフレームでは内容が常に変化するような HTML ページを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="cb16e-104">Using frames makes it easy to create HTML pages in which one or more pieces of the page remain static, such as a navigation bar, while other frames constantly change their content.</span></span>  
  
 <span data-ttu-id="cb16e-105">HTML の作成者は、2 つの方法のいずれかでフレームを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cb16e-105">HTML authors can create frames in one of two ways:</span></span>  
  
-   <span data-ttu-id="cb16e-106">`FRAMESET` タグと `FRAME` タグを使用して、固定ウィンドウを作成する。</span><span class="sxs-lookup"><span data-stu-id="cb16e-106">Using the `FRAMESET` and `FRAME` tags, which create fixed windows.</span></span>  
  
 <span data-ttu-id="cb16e-107">または</span><span class="sxs-lookup"><span data-stu-id="cb16e-107">-or-</span></span>  
  
-   <span data-ttu-id="cb16e-108">`IFRAME` タグを使用して、実行時に移動できるフローティング ウィンドウを作成する。</span><span class="sxs-lookup"><span data-stu-id="cb16e-108">Using the `IFRAME` tag, which creates a floating window that can be repositioned at run time.</span></span>  
  
1.  <span data-ttu-id="cb16e-109">フレームは HTML ドキュメントを含むため、DOM (Document Object Model) においてフレームはウィンドウ要素およびフレーム要素の両方として表されます</span><span class="sxs-lookup"><span data-stu-id="cb16e-109">Because frames contain HTML documents, they are represented in the Document Object Model (DOM) as both window elements and frame elements.</span></span>  
  
2.  <span data-ttu-id="cb16e-110"><xref:System.Windows.Forms.HtmlWindow> の Frames コレクションを使用して `FRAME` タグまたは `IFRAME` タグにアクセスすると、フレームに対応するウィンドウ要素を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cb16e-110">When you access a `FRAME` or `IFRAME` tag by using the Frames collection of <xref:System.Windows.Forms.HtmlWindow>, you are retrieving the window element corresponding to the frame.</span></span> <span data-ttu-id="cb16e-111">これは、現在の URL、ドキュメント、サイズなど、フレームのすべての動的プロパティを表します。</span><span class="sxs-lookup"><span data-stu-id="cb16e-111">This represents all of the frame's dynamic properties, such as its current URL, document, and size.</span></span>  
  
3.  <span data-ttu-id="cb16e-112"><xref:System.Windows.Forms.HtmlWindow> の <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> プロパティ、<xref:System.Windows.Forms.HtmlElement.Children%2A> コレクション、または <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> や <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> などのメソッドを使用して `FRAME` タグまたは `IFRAME` タグにアクセスすると、フレーム要素を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cb16e-112">When you access a `FRAME` or `IFRAME` tag by using the <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> property of <xref:System.Windows.Forms.HtmlWindow>, the <xref:System.Windows.Forms.HtmlElement.Children%2A> collection, or methods such as <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> or <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, you are retrieving the frame element.</span></span> <span data-ttu-id="cb16e-113">これは、元の HTML ファイルに指定されている URL を含む、フレームの静的プロパティを表します。</span><span class="sxs-lookup"><span data-stu-id="cb16e-113">This represents the static properties of the frame, including the URL specified in the original HTML file.</span></span>  
  
## <a name="frames-and-security"></a><span data-ttu-id="cb16e-114">フレームとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="cb16e-114">Frames and Security</span></span>  
 <span data-ttu-id="cb16e-115">マネージ HTML DOM と呼ばれるセキュリティ手段が実装されているという事実によってフレームへのアクセスが複雑な*クロス フレーム スクリプティング セキュリティ*です。</span><span class="sxs-lookup"><span data-stu-id="cb16e-115">Access to frames is complicated by the fact that the managed HTML DOM implements a security measure known as *cross-frame scripting security*.</span></span> <span data-ttu-id="cb16e-116">異なるドメインに属する複数の `FRAME` を持つ `FRAMESET` がドキュメントに含まれる場合、これらの `FRAME` は相互にやり取りできません。</span><span class="sxs-lookup"><span data-stu-id="cb16e-116">If a document contains a `FRAMESET` with two or more `FRAME`s in different domains, these `FRAME`s cannot interact with one another.</span></span> <span data-ttu-id="cb16e-117">つまり、自分の Web サイトのコンテンツを表示する `FRAME` は、サード パーティのサイト (http://www.adatum.com/ など) をホストする `FRAME` 内の情報にアクセスできません</span><span class="sxs-lookup"><span data-stu-id="cb16e-117">In other words, a `FRAME` that displays content from your Web site cannot access information in a `FRAME` that hosts a third-party site such as http://www.adatum.com/.</span></span> <span data-ttu-id="cb16e-118">このセキュリティは、<xref:System.Windows.Forms.HtmlWindow> クラスのレベルで実装されます</span><span class="sxs-lookup"><span data-stu-id="cb16e-118">This security is implemented at the level of the <xref:System.Windows.Forms.HtmlWindow> class.</span></span> <span data-ttu-id="cb16e-119">別の Web サイトをホストする `FRAME` に関する一般情報 (URL など) は取得できますが、Web サイトの <xref:System.Windows.Forms.HtmlWindow.Document%2A> へのアクセスや、ホストしている `FRAME` または `IFRAME` のサイズや位置の変更はできません。</span><span class="sxs-lookup"><span data-stu-id="cb16e-119">You can obtain general information about a `FRAME` hosting another Web site, such as its URL, but you will be unable to access its <xref:System.Windows.Forms.HtmlWindow.Document%2A> or change the size or location of its hosting `FRAME` or `IFRAME`.</span></span>  
  
 <span data-ttu-id="cb16e-120">この規則は、<xref:System.Windows.Forms.HtmlWindow.Open%2A> メソッドおよび <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> メソッドを使用して開くウィンドウにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="cb16e-120">This rule also applies to windows that you open using the <xref:System.Windows.Forms.HtmlWindow.Open%2A> and <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> methods.</span></span> <span data-ttu-id="cb16e-121">開いたウィンドウが <xref:System.Windows.Forms.WebBrowser> コントロール内でホストされているページとは異なるドメインにある場合、そのウィンドウを移動したり、内容をチェックしたりできません。</span><span class="sxs-lookup"><span data-stu-id="cb16e-121">If the window you open is in a different domain from the page hosted in the <xref:System.Windows.Forms.WebBrowser> control, you will not be able to move that window or examine its contents.</span></span> <span data-ttu-id="cb16e-122">このような制限は、<xref:System.Windows.Forms.WebBrowser> コントロールを使用して、Windows フォーム ベースのアプリケーションの配置に使用した Web サイトとは異なる Web サイトを表示する場合にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="cb16e-122">These restrictions are also enforced if you use the <xref:System.Windows.Forms.WebBrowser> control to display a Web site that is different from the Web site used to deploy your Windows Forms-based application.</span></span> <span data-ttu-id="cb16e-123">[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 配置テクノロジを使用して Web サイト A からアプリケーションをインストールし、<xref:System.Windows.Forms.WebBrowser> を使用して Web サイト B を表示した場合、Web サイト B のデータにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="cb16e-123">If you use [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] deployment technology to install your application from Web site A, and you use the <xref:System.Windows.Forms.WebBrowser> to display Web site B, you will not be able to access Web site B's data.</span></span>  
  
 <span data-ttu-id="cb16e-124">クロスサイト スクリプティングの詳細については、次を参照してください。[に関するクロス フレームのスクリプティングとセキュリティ](http://msdn.microsoft.com/library/ms533028.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="cb16e-124">For more information about cross-site scripting, see[About Cross-Frame Scripting and Security](http://msdn.microsoft.com/library/ms533028.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb16e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb16e-125">See Also</span></span>  
 [<span data-ttu-id="cb16e-126">フレーム要素 &#124;です。フレーム オブジェクト</span><span class="sxs-lookup"><span data-stu-id="cb16e-126">FRAME Element &#124; frame Object</span></span>](http://msdn.microsoft.com/library/ms535250.aspx)  
 [<span data-ttu-id="cb16e-127">マネージ HTML DOM (Document Object Model) の使用</span><span class="sxs-lookup"><span data-stu-id="cb16e-127">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
