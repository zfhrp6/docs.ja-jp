---
title: My.Response オブジェクト
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76d0e701107add0d5bd468ba7a829759739e0cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="myresponse-object"></a><span data-ttu-id="63d85-102">My.Response オブジェクト</span><span class="sxs-lookup"><span data-stu-id="63d85-102">My.Response Object</span></span>
<span data-ttu-id="63d85-103">取得、<xref:System.Web.HttpResponse>オブジェクトに関連付けられている、<xref:System.Web.UI.Page>です。</span><span class="sxs-lookup"><span data-stu-id="63d85-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="63d85-104">このオブジェクトでは、HTTP 応答データをクライアントに送信し、その応答に関する情報を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="63d85-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63d85-105">コメント</span><span class="sxs-lookup"><span data-stu-id="63d85-105">Remarks</span></span>  
 <span data-ttu-id="63d85-106">`My.Response`オブジェクトには、現在が含まれています。<xref:System.Web.HttpResponse>ページに関連付けられているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="63d85-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="63d85-107">`My.Response`オブジェクトは、の使用のみ[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="63d85-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63d85-108">例</span><span class="sxs-lookup"><span data-stu-id="63d85-108">Example</span></span>  
 <span data-ttu-id="63d85-109">次の例からヘッダーのコレクションを取得、`My.Request`オブジェクトと使用、 `My.Response` ASP.NET ページに書き込むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="63d85-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="63d85-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="63d85-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="63d85-111">My.Request オブジェクト</span><span class="sxs-lookup"><span data-stu-id="63d85-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
