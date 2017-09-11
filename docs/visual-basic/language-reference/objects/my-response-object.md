---
title: "My.Response オブジェクト |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Response
- My.Response
dev_langs:
- VB
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b9b34c9df31536f6d553cda2e26677a2645768c2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="myresponse-object"></a><span data-ttu-id="da7ca-102">My.Response オブジェクト</span><span class="sxs-lookup"><span data-stu-id="da7ca-102">My.Response Object</span></span>
<span data-ttu-id="da7ca-103"><xref:System.Web.HttpResponse> <xref:System.Web.UI.Page>。</xref:System.Web.UI.Page>に関連付けられたオブジェクト</xref:System.Web.HttpResponse>を取得します。</span><span class="sxs-lookup"><span data-stu-id="da7ca-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="da7ca-104">このオブジェクトは、HTTP 応答データをクライアントに送信することができます、その応答に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="da7ca-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da7ca-105">コメント</span><span class="sxs-lookup"><span data-stu-id="da7ca-105">Remarks</span></span>  
 <span data-ttu-id="da7ca-106">`My.Response`オブジェクトには、現在が含まれています<xref:System.Web.HttpResponse>ページに関連付けられているオブジェクト。</xref:System.Web.HttpResponse> 。</span><span class="sxs-lookup"><span data-stu-id="da7ca-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="da7ca-107">`My.Response`のみ、オブジェクトが使用できる[!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="da7ca-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da7ca-108">例</span><span class="sxs-lookup"><span data-stu-id="da7ca-108">Example</span></span>  
 <span data-ttu-id="da7ca-109">次の例からヘッダーのコレクションを取得する、`My.Request`オブジェクトと使用法、 `My.Response` ASP.NET ページに書き込むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="da7ca-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 <span data-ttu-id="da7ca-110">[!code-vb[VbVbalrMyWeb&#1;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]</span><span class="sxs-lookup"><span data-stu-id="da7ca-110">[!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da7ca-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="da7ca-111">See Also</span></span>  
 <span data-ttu-id="da7ca-112"><xref:System.Web.HttpResponse></xref:System.Web.HttpResponse></span><span class="sxs-lookup"><span data-stu-id="da7ca-112"><xref:System.Web.HttpResponse></span></span>   
<span data-ttu-id="da7ca-113"> [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)</span><span class="sxs-lookup"><span data-stu-id="da7ca-113"> [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)</span></span>
