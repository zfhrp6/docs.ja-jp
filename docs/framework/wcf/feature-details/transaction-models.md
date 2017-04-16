---
title: "トランザクション モデル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# トランザクション モデル
ここでは、トランザクション プログラミング モデルと、マイクロソフトが提供するインフラストラクチャ コンポーネントとの関係を説明します。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でトランザクションを使用する場合、選択するトランザクション モデルが異なるのではなく、統合され一貫した 1 つのモデルにおいて操作するレイヤーが異なるのだということを理解することが大切です。  
  
 以下に、3 つの主要なトランザクション コンポーネントについて説明します。  
  
## Windows Communication Foundation トランザクション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされるトランザクションでは、トランザクション サービスを作成することができます。さらに、WS\-AtomicTransaction \(WS\-AT\) プロトコルのサポートにより、アプリケーションは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] またはサードパーティのテクノロジを使用して構築された Web サービスにトランザクションをフローさせることができます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはアプリケーションでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トランザクション機能により、インフラストラクチャがトランザクションを作成、フロー、同期する方法と時期を宣言的に指定するための属性と構成が提供されます。  
  
## System.Transactions トランザクション  
 <xref:System.Transactions> 名前空間は、<xref:System.Transactions.Transaction> クラスに基づく明示的なプログラミング モデルだけでなく、インフラストラクチャがトランザクションを自動的に管理する、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なプログラミング モデルも提供します。  
  
 この 2 つのモデルを使用したトランザクション アプリケーション作成方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[トランザクション アプリケーションの作成](http://go.microsoft.com/fwlink/?LinkId=94947)」を参照してください。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはアプリケーションでは、クライアント アプリケーション内にトランザクションを作成し、サービス内で必要な場合に、明示的にトランザクションと対話するためのプログラミング モデルが <xref:System.Transactions> により提供されます。  
  
## MSDTC トランザクション  
 Microsoft 分散トランザクション コーディネーター \(MSDTC\) は、分散トランザクションをサポートするトランザクション マネージャーです。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「[DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948)」を参照してください。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはアプリケーションにおいて MSDTC は、クライアントまたはサービス内で作成されたトランザクションを調整するためのインフラストラクチャを提供します。