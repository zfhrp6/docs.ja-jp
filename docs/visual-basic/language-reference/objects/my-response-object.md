---
title: My.Response オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 0a907d74112586e7b88c5a0a6f40080455454d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597524"
---
# <a name="myresponse-object"></a><span data-ttu-id="b8e60-102">My.Response オブジェクト</span><span class="sxs-lookup"><span data-stu-id="b8e60-102">My.Response Object</span></span>
<span data-ttu-id="b8e60-103">取得、<xref:System.Web.HttpResponse>オブジェクトに関連付けられている、<xref:System.Web.UI.Page>です。</span><span class="sxs-lookup"><span data-stu-id="b8e60-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="b8e60-104">このオブジェクトでは、HTTP 応答データをクライアントに送信し、その応答に関する情報を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b8e60-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8e60-105">コメント</span><span class="sxs-lookup"><span data-stu-id="b8e60-105">Remarks</span></span>  
 <span data-ttu-id="b8e60-106">`My.Response`オブジェクトには、現在が含まれています。<xref:System.Web.HttpResponse>ページに関連付けられているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b8e60-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="b8e60-107">`My.Response`オブジェクトは、の使用のみ[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="b8e60-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8e60-108">例</span><span class="sxs-lookup"><span data-stu-id="b8e60-108">Example</span></span>  
 <span data-ttu-id="b8e60-109">次の例からヘッダーのコレクションを取得、`My.Request`オブジェクトと使用、 `My.Response` ASP.NET ページに書き込むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b8e60-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a><span data-ttu-id="b8e60-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8e60-110">See Also</span></span>  
 <xref:System.Web.HttpResponse>  
 [<span data-ttu-id="b8e60-111">My.Request オブジェクト</span><span class="sxs-lookup"><span data-stu-id="b8e60-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
