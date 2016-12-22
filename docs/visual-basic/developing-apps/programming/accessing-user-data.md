---
title: "Accessing User Data (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "domain names, retrieving"
  - "data [Visual Basic], accessing user data"
  - "My.User object, tasks"
  - "user data, domain"
  - "user names, retrieving"
  - "user data, accessing"
  - "login names"
  - "examples [Visual Basic], accessing user data"
ms.assetid: 32492a15-ee59-4a63-a1f1-9b24cc13140a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Accessing User Data (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

このセクションのトピックでは、`My.User` オブジェクトと、これを使用して実行できるタスクについて取り上げます。  
  
 `My.User` オブジェクトを使用すると、<xref:System.Security.Principal.IPrincipal> インターフェイスを実装するオブジェクトを取得でき、ログオン ユーザーについての情報にアクセスできます。  
  
## タスク  
  
|目的|参照項目|  
|--------|----------|  
|ユーザーのログイン名を取得する。|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|アプリケーションが Windows 認証を使用している場合に、ユーザーのドメイン名を取得する。|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|ユーザーのロールを判断する。|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>