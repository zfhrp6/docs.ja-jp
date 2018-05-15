---
title: トランザクション モデル
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-models"></a><span data-ttu-id="d17c9-102">トランザクション モデル</span><span class="sxs-lookup"><span data-stu-id="d17c9-102">Transaction Models</span></span>
<span data-ttu-id="d17c9-103">ここでは、トランザクション プログラミング モデルと、マイクロソフトが提供するインフラストラクチャ コンポーネントとの関係を説明します。</span><span class="sxs-lookup"><span data-stu-id="d17c9-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="d17c9-104">トランザクションでは、Windows Communication Foundation (WCF) を使用する場合は、選択する別のトランザクション モデルですが統合され一貫したモデルのさまざまなレイヤーではなくオペレーティングを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d17c9-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="d17c9-105">以下に、3 つの主要なトランザクション コンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d17c9-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="d17c9-106">Windows Communication Foundation トランザクション</span><span class="sxs-lookup"><span data-stu-id="d17c9-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="d17c9-107">WCF でサポートされるトランザクションでは、トランザクション サービスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="d17c9-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="d17c9-108">さらに、Ws-atomictransaction (WS-AT) プロトコルのサポートに、アプリケーションは WCF またはサードパーティのテクノロジを使用して構築された Web サービスにトランザクションをフローできます。</span><span class="sxs-lookup"><span data-stu-id="d17c9-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="d17c9-109">WCF サービスまたはアプリケーションでは、WCF のトランザクション機能は、属性と宣言を指定する方法とタイミング インフラストラクチャ必要がありますを作成、フロー、トランザクションを同期の構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="d17c9-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="d17c9-110">System.Transactions トランザクション</span><span class="sxs-lookup"><span data-stu-id="d17c9-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="d17c9-111"><xref:System.Transactions> 名前空間は、<xref:System.Transactions.Transaction> クラスに基づく明示的なプログラミング モデルだけでなく、インフラストラクチャがトランザクションを自動的に管理する、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なプログラミング モデルも提供します。</span><span class="sxs-lookup"><span data-stu-id="d17c9-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="d17c9-112">これら 2 つのモデルを使用して、トランザクションのアプリケーションを作成する方法の詳細については、次を参照してください。[トランザクション アプリケーションの作成](http://go.microsoft.com/fwlink/?LinkId=94947)です。</span><span class="sxs-lookup"><span data-stu-id="d17c9-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="d17c9-113">WCF サービスまたはアプリケーションでは、<xref:System.Transactions>をクライアント アプリケーション内にトランザクションを作成して、サービス内で必要なときに、トランザクションと明示的に対話するために、プログラミング モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="d17c9-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="d17c9-114">MSDTC トランザクション</span><span class="sxs-lookup"><span data-stu-id="d17c9-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="d17c9-115">Microsoft 分散トランザクション コーディネーター (MSDTC) は、分散トランザクションをサポートするトランザクション マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="d17c9-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="d17c9-116">詳細については、次を参照してください。、 [DTC プログラマ リファレンス](http://go.microsoft.com/fwlink/?LinkId=94948)です。</span><span class="sxs-lookup"><span data-stu-id="d17c9-116">For more information, see the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="d17c9-117">WCF サービスまたはアプリケーションでは、MSDTC のインフラストラクチャのクライアントまたはサービス内で作成されたトランザクションの調整を提供します。</span><span class="sxs-lookup"><span data-stu-id="d17c9-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
