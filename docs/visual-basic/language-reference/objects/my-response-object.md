---
title: "My.Response Object | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.MyWebExtension.Response"
  - "My.Response"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Response object"
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# My.Response Object
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:System.Web.UI.Page> に関連付けられている <xref:System.Web.HttpResponse> オブジェクトを取得します。  このオブジェクトを使用することにより、HTTP 応答データをクライアントに送り、この応答に関する情報を格納できます。  
  
## 解説  
 `My.Response` オブジェクトには、ページに関連する現在の <xref:System.Web.HttpResponse> オブジェクトが含まれます。  
  
 `My.Response` オブジェクトは [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] アプリケーションでのみ利用できます。  
  
## 使用例  
 次のコード例は、`My.Request` オブジェクトからヘッダー コレクションを取得し、`My.Response` オブジェクトを使ってそれを ASP.NET ページに書き込みます。  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/visualbasic/my-response-object_1.aspx)]  
  
## 参照  
 <xref:System.Web.HttpResponse>   
 [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)