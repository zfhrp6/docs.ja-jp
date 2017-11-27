---
title: "トランザクション モデル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 182a394b7698c7a1a59a4db50ee81caed4d2e75f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-models"></a>トランザクション モデル
ここでは、トランザクション プログラミング モデルと、マイクロソフトが提供するインフラストラクチャ コンポーネントとの関係を説明します。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でトランザクションを使用する場合、選択するトランザクション モデルが異なるのではなく、統合され一貫した 1 つのモデルにおいて操作するレイヤーが異なるのだということを理解することが大切です。  
  
 以下に、3 つの主要なトランザクション コンポーネントについて説明します。  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation トランザクション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされるトランザクションでは、トランザクション サービスを作成することができます。 さらに、WS-AtomicTransaction (WS-AT) プロトコルのサポートにより、アプリケーションは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] またはサードパーティのテクノロジを使用して構築された Web サービスにトランザクションをフローさせることができます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはアプリケーションでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トランザクション機能により、インフラストラクチャがトランザクションを作成、フロー、同期する方法と時期を宣言的に指定するための属性と構成が提供されます。  
  
## <a name="systemtransactions-transactions"></a>System.Transactions トランザクション  
 <xref:System.Transactions> 名前空間は、<xref:System.Transactions.Transaction> クラスに基づく明示的なプログラミング モデルだけでなく、インフラストラクチャがトランザクションを自動的に管理する、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なプログラミング モデルも提供します。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]これら 2 つのモデルを使用して、トランザクションのアプリケーションを作成する方法[トランザクション アプリケーションの作成](http://go.microsoft.com/fwlink/?LinkId=94947)です。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはアプリケーションでは、クライアント アプリケーション内にトランザクションを作成し、サービス内で必要な場合に、明示的にトランザクションと対話するためのプログラミング モデルが <xref:System.Transactions> により提供されます。  
  
## <a name="msdtc-transactions"></a>MSDTC トランザクション  
 Microsoft 分散トランザクション コーディネーター (MSDTC) は、分散トランザクションをサポートするトランザクション マネージャーです。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][DTC プログラマ リファレンス](http://go.microsoft.com/fwlink/?LinkId=94948)です。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはアプリケーションにおいて MSDTC は、クライアントまたはサービス内で作成されたトランザクションを調整するためのインフラストラクチャを提供します。
