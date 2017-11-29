---
title: "トランザクション処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5248dd3a4da450e411dd5d9a7843df6c9263026e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-processing"></a><span data-ttu-id="844fc-102">トランザクション処理</span><span class="sxs-lookup"><span data-stu-id="844fc-102">Transaction Processing</span></span>
<span data-ttu-id="844fc-103">オンライン書店で書籍を購入する場合、書籍と代金 (クレジット形式) を交換します。</span><span class="sxs-lookup"><span data-stu-id="844fc-103">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="844fc-104">クレジットに問題がなければ、一連の処理によって顧客は書籍を入手し、書店には代金が入金されます。</span><span class="sxs-lookup"><span data-stu-id="844fc-104">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="844fc-105">ただし、一連の取引処理の 1 つでも失敗すると取引全体が失敗し、</span><span class="sxs-lookup"><span data-stu-id="844fc-105">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="844fc-106">顧客は書籍を入手できず、書店は代金を受け取れません。</span><span class="sxs-lookup"><span data-stu-id="844fc-106">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="844fc-107">取引のバランスを取り、予測可能なものにするための技術をトランザクション処理と呼びます。</span><span class="sxs-lookup"><span data-stu-id="844fc-107">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="844fc-108">トランザクションは、トランザクション単位内のすべての処理が正常に完了しない限り、データ指向のリソースが永続的に更新されないことを保証します。</span><span class="sxs-lookup"><span data-stu-id="844fc-108">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="844fc-109">完全に成功するか、または完全に失敗する 1 つの単位に一連の関連する処理を結合することにより、エラーの回復を単純化し、アプリケーションの信頼性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="844fc-109">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="844fc-110">トランザクション処理システムは、ビジネスに必要なルーチン トランザクションを実行するためのトランザクション指向アプリケーションをホストする、コンピューター ハードウェアとソフトウェアから構成されます。</span><span class="sxs-lookup"><span data-stu-id="844fc-110">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="844fc-111">例としては、発注エントリ、航空券の予約、給与支払い、従業員レコード、製造、出荷などの管理システムが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="844fc-111">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="844fc-112">ここでは、トランザクション処理に関する一般的な情報と、Microsoft .NET Framework を使用したトランザクション アプリケーションおよびリソース マネージャーの具体的な作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="844fc-112">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="844fc-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="844fc-113">In This Section</span></span>  
 [<span data-ttu-id="844fc-114">トランザクションの基礎</span><span class="sxs-lookup"><span data-stu-id="844fc-114">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 <span data-ttu-id="844fc-115">トランザクション処理の基本的な用語と概念について紹介します。</span><span class="sxs-lookup"><span data-stu-id="844fc-115">Introduces basic transaction processing terms and concepts.</span></span>  
  
 [<span data-ttu-id="844fc-116">System.Transactions により提供される機能</span><span class="sxs-lookup"><span data-stu-id="844fc-116">Features Provided by System.Transactions</span></span>](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 <span data-ttu-id="844fc-117">System.Transactions の機能を使用して、独自のトランザクション アプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="844fc-117">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="844fc-118">参照</span><span class="sxs-lookup"><span data-stu-id="844fc-118">Reference</span></span>  
 <xref:System.Transactions>  
 <span data-ttu-id="844fc-119">コードのトランザクションへの参加を許可するクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="844fc-119">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="844fc-120">このクラスは、複数の分散参加要素、複数のフェーズ通知、および永続参加リストを使用するトランザクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="844fc-120">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>
