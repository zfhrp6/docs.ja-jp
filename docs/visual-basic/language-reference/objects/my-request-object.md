---
title: "My.Request オブジェクト"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords: My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0e67c8fd85860eacc57bcc7dd7f15f97097efe3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="myrequest-object"></a><span data-ttu-id="03ed9-102">My.Request オブジェクト</span><span class="sxs-lookup"><span data-stu-id="03ed9-102">My.Request Object</span></span>
<span data-ttu-id="03ed9-103">要求されたページの <xref:System.Web.HttpRequest> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="03ed9-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03ed9-104">コメント</span><span class="sxs-lookup"><span data-stu-id="03ed9-104">Remarks</span></span>  
 <span data-ttu-id="03ed9-105">`My.Request` オブジェクトには、現在の HTTP 要求に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="03ed9-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="03ed9-106">`My.Request` オブジェクトは、ASP.NET アプリケーションでのみ使うことができます。</span><span class="sxs-lookup"><span data-stu-id="03ed9-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03ed9-107">例</span><span class="sxs-lookup"><span data-stu-id="03ed9-107">Example</span></span>  
 <span data-ttu-id="03ed9-108">次の例からヘッダーのコレクションを取得、`My.Request`オブジェクトと使用、 `My.Response` ASP.NET ページに書き込むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="03ed9-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-request-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="03ed9-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="03ed9-109">See Also</span></span>  
 <xref:System.Web.HttpRequest>  
 [<span data-ttu-id="03ed9-110">My.Response オブジェクト</span><span class="sxs-lookup"><span data-stu-id="03ed9-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
