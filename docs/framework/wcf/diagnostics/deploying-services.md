---
title: "サービスの配置 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# サービスの配置
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションをランタイム環境に配置する方法を説明します。  
  
## アプリケーションのホスト環境の選択  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、マネージ コードをサポートする任意の Windows プロセスで実行されるように設計されています。アクティブにするには、サービスを作成してそのコンテキストと有効期間を制御するランタイム環境内で、サービスをホストする必要があります。ホスティング環境の範囲は、最も単純なコンソール アプリケーション内、Windows サービスやインターネット インフォメーション サービス \(IIS\) のようなサーバー環境、あるいは Windows アクティブ化サービス \(WAS\) で管理されるワーカー プロセス内での実行にまで及びます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションに対する各種のホスティング環境については、「[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)」を参照してください。  
  
## 参照  
 [ホスト](../../../../docs/framework/wcf/feature-details/hosting.md)   
 [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)