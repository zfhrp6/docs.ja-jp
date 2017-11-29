---
title: "方法 : 一方向コントラクトを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb899bdc8d1452046b71fdce5d0782e1d1338d2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="c2719-102">方法 : 一方向コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="c2719-102">How to: Create a One-Way Contract</span></span>
<span data-ttu-id="c2719-103">ここでは、一方向コントラクトを使用するメソッドを作成するための基本手順を示します。</span><span class="sxs-lookup"><span data-stu-id="c2719-103">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="c2719-104">このようなメソッドは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスの操作をクライアントから呼び出しますが、応答を待ちません。</span><span class="sxs-lookup"><span data-stu-id="c2719-104">Such methods invoke operations on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service from a client but do not expect a reply.</span></span> <span data-ttu-id="c2719-105">この種のコントラクトは、たとえば、多数のサブスクライバーに対して通知を発行するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2719-105">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="c2719-106">一方向コントラクトは、二重のコントラクトを作成する場合にも使用できます。その場合は、クライアントとサーバーが互いに独立して通信できるため、どちらからでも相手の呼び出しを開始できます。</span><span class="sxs-lookup"><span data-stu-id="c2719-106">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="c2719-107">これにより、特にサーバーは、クライアントがイベントとして処理できる一方向の呼び出しをクライアントに対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="c2719-107">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="c2719-108">一方向メソッドの指定の詳細については、<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティおよび <xref:System.ServiceModel.OperationContractAttribute> クラスのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2719-108">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="c2719-109">双方向コントラクト用のクライアント アプリケーションを作成するを参照してください[する方法: 一方向とアクセス サービスと要求/応答コントラクト](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2719-109"> creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="c2719-110">作業用サンプルについては、次を参照してください。、[一方向](../../../../docs/framework/wcf/samples/one-way.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="c2719-110">For a working sample, see the [One-Way](../../../../docs/framework/wcf/samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="c2719-111">一方向コントラクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="c2719-111">To create a one-way contract</span></span>  
  
1.  <span data-ttu-id="c2719-112">サービスにより実装されるメソッドを定義するインターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用することにより、サービス コントラクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c2719-112">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2.  <span data-ttu-id="c2719-113"><xref:System.ServiceModel.OperationContractAttribute> クラスをメソッドに適用する際に、クライアントが呼び出すことのできるインターフェイスのメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="c2719-113">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3.  <span data-ttu-id="c2719-114"><xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティを `true` に設定することにより、出力を行わない (戻り値および出力または参照パラメーターを持たない) 一方向の操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2719-114">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="c2719-115"><xref:System.ServiceModel.OperationContractAttribute> プロパティの既定値は <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> であるため、`false` クラスを持つ操作では、既定で要求/応答コントラクトが満たされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c2719-115">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="c2719-116">したがって、このメソッドに一方向コントラクトが必要な場合は、この属性プロパティの値を明示的に `true` に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2719-116">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2719-117">例</span><span class="sxs-lookup"><span data-stu-id="c2719-117">Example</span></span>  
 <span data-ttu-id="c2719-118">複数の一方向メソッドを含むサービスのコントラクトを定義する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="c2719-118">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="c2719-119">`Equals` (既定で応答/要求コントラクトに設定され、結果を返します) を除き、すべてのメソッドは一方向コントラクトを持ちます。</span><span class="sxs-lookup"><span data-stu-id="c2719-119">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c2719-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2719-120">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="c2719-121">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="c2719-121">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="c2719-122">方法: サービス コントラクトを定義する</span><span class="sxs-lookup"><span data-stu-id="c2719-122">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="c2719-123">セッション</span><span class="sxs-lookup"><span data-stu-id="c2719-123">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)  
 [<span data-ttu-id="c2719-124">方法: 双方向コントラクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c2719-124">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
