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
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e2ae9a659bb7575023dfa1847c9d405d0f7d6ac3
ms.lasthandoff: 03/13/2017

---
# <a name="myresponse-object"></a>My.Response オブジェクト
<xref:System.Web.HttpResponse> <xref:System.Web.UI.Page>。</xref:System.Web.UI.Page>に関連付けられたオブジェクト</xref:System.Web.HttpResponse>を取得します。 このオブジェクトは、HTTP 応答データをクライアントに送信することができます、その応答に関する情報が含まれています。  
  
## <a name="remarks"></a>コメント  
 `My.Response`オブジェクトには、現在が含まれています<xref:System.Web.HttpResponse>ページに関連付けられているオブジェクト。</xref:System.Web.HttpResponse> 。  
  
 `My.Response`のみ、オブジェクトが使用できる[!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]アプリケーションです。  
  
## <a name="example"></a>例  
 次の例からヘッダーのコレクションを取得する、`My.Request`オブジェクトと使用法、 `My.Response` ASP.NET ページに書き込むオブジェクト。  
  
 [!code-vb[VbVbalrMyWeb&#1;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Web.HttpResponse></xref:System.Web.HttpResponse>   
 [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)
