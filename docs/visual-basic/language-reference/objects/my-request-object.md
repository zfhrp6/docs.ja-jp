---
title: "My.Request Object | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.MyWebExtension.Request"
  - "My.Request"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Request object"
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# My.Request Object
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

要求されたページに対する <xref:System.Web.HttpRequest> オブジェクトを取得します。  
  
## 解説  
 `My.Request` オブジェクトには現在の HTTP 要求に関する情報が含まれます。  
  
 `My.Request` オブジェクトは、ASP.NET アプリケーションだけで使用できます。  
  
## 使用例  
 次のコード例は、`My.Request` オブジェクトからヘッダー コレクションを取得し、`My.Response` オブジェクトを使ってそれを ASP.NET ページに書き込みます。  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/visualbasic/my-request-object_1.aspx)]  
  
## 参照  
 <xref:System.Web.HttpRequest>   
 [My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)