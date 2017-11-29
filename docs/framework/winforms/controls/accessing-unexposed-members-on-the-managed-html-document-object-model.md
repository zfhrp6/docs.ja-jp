---
title: "マネージ HTML DOM (Document Object Model) の非公開メンバーへのアクセス"
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
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dda2581ceed854fa5121076f0c7b9df414bffe52
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="75a30-102">マネージ HTML DOM (Document Object Model) の非公開メンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="75a30-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="75a30-103">マネージ HTML ドキュメント オブジェクト モデル (DOM) と呼ばれるクラスが含まれています<xref:System.Windows.Forms.HtmlElement>プロパティ、メソッド、およびすべての HTML 要素に共通するイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="75a30-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="75a30-104">場合によっては、ただし、する必要があります、マネージ インターフェイスを直接公開しないメンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="75a30-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="75a30-105">このトピックは、非公開メンバーにアクセスするための 2 つの方法を調べて[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]と Web ページ内で定義されている VBScript 関数。</span><span class="sxs-lookup"><span data-stu-id="75a30-105">This topic examines two ways for accessing unexposed members, including [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="75a30-106">マネージ インターフェイスを非公開メンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="75a30-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="75a30-107"><xref:System.Windows.Forms.HtmlDocument>および<xref:System.Windows.Forms.HtmlElement>非公開メンバーへのアクセスを有効にする 4 つのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="75a30-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="75a30-108">次の表は、種類とその対応するメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="75a30-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="75a30-109">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="75a30-109">Member Type</span></span>|<span data-ttu-id="75a30-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="75a30-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="75a30-111">プロパティ (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="75a30-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="75a30-112">メソッド</span><span class="sxs-lookup"><span data-stu-id="75a30-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="75a30-113">イベント (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="75a30-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="75a30-114">イベント (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="75a30-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="75a30-115">イベント (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="75a30-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="75a30-116">これらのメソッドを使用する場合、適切な基になる型の要素があると見なされます。</span><span class="sxs-lookup"><span data-stu-id="75a30-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="75a30-117">リッスンするようにすると、`Submit`のイベント、 `FORM` HTML 要素をページにいくつかの事前処理を実行できるように、`FORM`の値は、ユーザー、サーバーに送信する前にします。</span><span class="sxs-lookup"><span data-stu-id="75a30-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="75a30-118">理想的には、HTML を制御する場合は、定義して、`FORM`を一意に`ID`属性。</span><span class="sxs-lookup"><span data-stu-id="75a30-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 <span data-ttu-id="75a30-119">このページを読み込んだ後、<xref:System.Windows.Forms.WebBrowser>制御を行うこともできます、<xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>を取得する方法、`FORM`を使用して実行時に`form1`引数として。</span><span class="sxs-lookup"><span data-stu-id="75a30-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="75a30-120">アンマネージ インターフェイスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="75a30-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="75a30-121">マネージ HTML DOM の非公開メンバーは、各 DOM クラスによって公開されているアンマネージ コンポーネント オブジェクト モデル (COM) インターフェイスを使用してアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="75a30-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="75a30-122">非公開メンバーに対していくつかの呼び出しを行う必要がある場合、または非公開メンバーがマネージ HTML DOM によってラップされていないその他のアンマネージ インターフェイスを返す場合、これは推奨します。</span><span class="sxs-lookup"><span data-stu-id="75a30-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="75a30-123">次の表はすべてのマネージ HTML DOM を通じて公開されるアンマネージ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75a30-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="75a30-124">使用法と例のコードの詳細については、各リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="75a30-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="75a30-125">型</span><span class="sxs-lookup"><span data-stu-id="75a30-125">Type</span></span>|<span data-ttu-id="75a30-126">アンマネージ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75a30-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="75a30-127">これはサポートされていませんが、アプリケーションから HTML DOM のアンマネージ ライブラリ (MSHTML.dll) への参照を追加する COM インターフェイスを使用する最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="75a30-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="75a30-128">詳細については、次を参照してください。[サポート技術情報の記事 934368](http://support.microsoft.com/kb/934368)です。</span><span class="sxs-lookup"><span data-stu-id="75a30-128">For more information, see [Knowledge Base Article 934368](http://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="75a30-129">スクリプト関数へのアクセス</span><span class="sxs-lookup"><span data-stu-id="75a30-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="75a30-130">HTML ページなどのスクリプト言語を使用して、1 つまたは複数の関数を定義できます[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]または VBScript です。</span><span class="sxs-lookup"><span data-stu-id="75a30-130">An HTML page can define one or more functions by using a scripting language such as [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] or VBScript.</span></span> <span data-ttu-id="75a30-131">内のこれらの関数を配置している、 `SCRIPT`  ページで、ページ、DOM でイベントへの応答または要求時に実行できます。</span><span class="sxs-lookup"><span data-stu-id="75a30-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="75a30-132">HTML ページを使用して、定義するスクリプト関数を呼び出すことができます、<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="75a30-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="75a30-133">スクリプト メソッドに HTML 要素が返される場合に返されるこの結果を変換する、キャストを使用することができます、<xref:System.Windows.Forms.HtmlElement>です。</span><span class="sxs-lookup"><span data-stu-id="75a30-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="75a30-134">詳細とコード例では、次を参照してください。<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>です。</span><span class="sxs-lookup"><span data-stu-id="75a30-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75a30-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="75a30-135">See Also</span></span>  
 [<span data-ttu-id="75a30-136">マネージ HTML DOM (Document Object Model) の使用</span><span class="sxs-lookup"><span data-stu-id="75a30-136">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
