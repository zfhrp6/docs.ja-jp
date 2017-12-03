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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c74b1826ca280ba05420449758cdbb84dac3e93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-models"></a><span data-ttu-id="21658-102">トランザクション モデル</span><span class="sxs-lookup"><span data-stu-id="21658-102">Transaction Models</span></span>
<span data-ttu-id="21658-103">ここでは、トランザクション プログラミング モデルと、マイクロソフトが提供するインフラストラクチャ コンポーネントとの関係を説明します。</span><span class="sxs-lookup"><span data-stu-id="21658-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="21658-104">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でトランザクションを使用する場合、選択するトランザクション モデルが異なるのではなく、統合され一貫した 1 つのモデルにおいて操作するレイヤーが異なるのだということを理解することが大切です。</span><span class="sxs-lookup"><span data-stu-id="21658-104">When using transactions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="21658-105">以下に、3 つの主要なトランザクション コンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="21658-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="21658-106">Windows Communication Foundation トランザクション</span><span class="sxs-lookup"><span data-stu-id="21658-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="21658-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされるトランザクションでは、トランザクション サービスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="21658-107">The transaction support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows you write transactional services.</span></span> <span data-ttu-id="21658-108">さらに、WS-AtomicTransaction (WS-AT) プロトコルのサポートにより、アプリケーションは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] またはサードパーティのテクノロジを使用して構築された Web サービスにトランザクションをフローさせることができます。</span><span class="sxs-lookup"><span data-stu-id="21658-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or third-party technology.</span></span>  
  
 <span data-ttu-id="21658-109">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはアプリケーションでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トランザクション機能により、インフラストラクチャがトランザクションを作成、フロー、同期する方法と時期を宣言的に指定するための属性と構成が提供されます。</span><span class="sxs-lookup"><span data-stu-id="21658-109">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="21658-110">System.Transactions トランザクション</span><span class="sxs-lookup"><span data-stu-id="21658-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="21658-111"><xref:System.Transactions> 名前空間は、<xref:System.Transactions.Transaction> クラスに基づく明示的なプログラミング モデルだけでなく、インフラストラクチャがトランザクションを自動的に管理する、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なプログラミング モデルも提供します。</span><span class="sxs-lookup"><span data-stu-id="21658-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="21658-112">これら 2 つのモデルを使用して、トランザクションのアプリケーションを作成する方法[トランザクション アプリケーションの作成](http://go.microsoft.com/fwlink/?LinkId=94947)です。</span><span class="sxs-lookup"><span data-stu-id="21658-112"> how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="21658-113">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはアプリケーションでは、クライアント アプリケーション内にトランザクションを作成し、サービス内で必要な場合に、明示的にトランザクションと対話するためのプログラミング モデルが <xref:System.Transactions> により提供されます。</span><span class="sxs-lookup"><span data-stu-id="21658-113">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="21658-114">MSDTC トランザクション</span><span class="sxs-lookup"><span data-stu-id="21658-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="21658-115">Microsoft 分散トランザクション コーディネーター (MSDTC) は、分散トランザクションをサポートするトランザクション マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="21658-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="21658-116">[DTC プログラマ リファレンス](http://go.microsoft.com/fwlink/?LinkId=94948)です。</span><span class="sxs-lookup"><span data-stu-id="21658-116"> the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="21658-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたはアプリケーションにおいて MSDTC は、クライアントまたはサービス内で作成されたトランザクションを調整するためのインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="21658-117">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
