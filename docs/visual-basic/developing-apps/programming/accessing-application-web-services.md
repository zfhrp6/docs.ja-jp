---
title: "Accessing Application Web Services (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Web services, My.WebServices object"
  - "My.WebServices object"
  - "applications [Visual Basic], Web services"
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Accessing Application Web Services (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.WebServices` オブジェクトは、現在のプロジェクトから参照されている各 Web サービスのインスタンスを提供します。  各インスタンスは、要求に応じてインスタンス化されます。  これらの Web サービスには、`My.WebServices` オブジェクトのプロパティからアクセスできます。  プロパティの名前は、そのプロパティでアクセスする Web サービスの名前と同じです。  <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> を継承するクラスはすべて Web サービスです。  
  
## タスク  
 次の表は、アプリケーションが参照する Web サービスにアクセスする方法を示しています。  
  
|||  
|-|-|  
|目的|参照項目|  
|Web サービスを呼び出す。|[My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)|  
|Web サービスを非同期で呼び出し、完了したときにイベントを処理する。|[How to: Call a Web Service Asynchronously](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|  
  
## 参照  
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)