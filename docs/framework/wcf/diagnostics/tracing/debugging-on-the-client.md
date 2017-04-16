---
title: "クライアントでのデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# クライアントでのデバッグ
[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスのクライアント アプリケーションをユーザーが簡単に記述できるようにするには、サービスの構成ファイルに [\<serviceDebug\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) サービス動作を追加します。この動作は、ヘルプ ページを公開し、クライアントに返される SOAP エラーの詳細にマネージ例外情報を表示するために使用できます。