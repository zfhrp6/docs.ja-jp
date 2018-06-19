---
title: トランザクション モデル
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499025"
---
# <a name="transaction-models"></a>トランザクション モデル
ここでは、トランザクション プログラミング モデルと、マイクロソフトが提供するインフラストラクチャ コンポーネントとの関係を説明します。  
  
 トランザクションでは、Windows Communication Foundation (WCF) を使用する場合は、選択する別のトランザクション モデルですが統合され一貫したモデルのさまざまなレイヤーではなくオペレーティングを理解する必要があります。  
  
 以下に、3 つの主要なトランザクション コンポーネントについて説明します。  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation トランザクション  
 WCF でサポートされるトランザクションでは、トランザクション サービスを作成することができます。 さらに、Ws-atomictransaction (WS-AT) プロトコルのサポートに、アプリケーションは WCF またはサードパーティのテクノロジを使用して構築された Web サービスにトランザクションをフローできます。  
  
 WCF サービスまたはアプリケーションでは、WCF のトランザクション機能は、属性と宣言を指定する方法とタイミング インフラストラクチャ必要がありますを作成、フロー、トランザクションを同期の構成を提供します。  
  
## <a name="systemtransactions-transactions"></a>System.Transactions トランザクション  
 <xref:System.Transactions> 名前空間は、<xref:System.Transactions.Transaction> クラスに基づく明示的なプログラミング モデルだけでなく、インフラストラクチャがトランザクションを自動的に管理する、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なプログラミング モデルも提供します。  
  
 これら 2 つのモデルを使用して、トランザクションのアプリケーションを作成する方法の詳細については、次を参照してください。[トランザクション アプリケーションの作成](http://go.microsoft.com/fwlink/?LinkId=94947)です。  
  
 WCF サービスまたはアプリケーションでは、<xref:System.Transactions>をクライアント アプリケーション内にトランザクションを作成して、サービス内で必要なときに、トランザクションと明示的に対話するために、プログラミング モデルを提供します。  
  
## <a name="msdtc-transactions"></a>MSDTC トランザクション  
 Microsoft 分散トランザクション コーディネーター (MSDTC) は、分散トランザクションをサポートするトランザクション マネージャーです。  
  
 詳細については、次を参照してください。、 [DTC プログラマ リファレンス](http://go.microsoft.com/fwlink/?LinkId=94948)です。  
  
 WCF サービスまたはアプリケーションでは、MSDTC のインフラストラクチャのクライアントまたはサービス内で作成されたトランザクションの調整を提供します。
