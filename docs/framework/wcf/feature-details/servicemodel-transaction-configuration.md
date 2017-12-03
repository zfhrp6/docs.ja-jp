---
title: "ServiceModel トランザクションの構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef1d8a9e749c06701aa0a187f81b5b345518c07b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="20335-102">ServiceModel トランザクションの構成</span><span class="sxs-lookup"><span data-stu-id="20335-102">ServiceModel Transaction Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="20335-103"> では、サービスのトランザクションを構成するために、`transactionFlow`、`transactionProtocol`、および `transactionTimeout` という 3 つの属性が用意されています。</span><span class="sxs-lookup"><span data-stu-id="20335-103"> provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="20335-104">transactionFlow の構成</span><span class="sxs-lookup"><span data-stu-id="20335-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="20335-105">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に用意されているほとんどの定義済みバインディングには、`transactionFlow` 属性と `transactionProtocol` 属性が含まれています。これらの属性を使用すると、特定のトランザクション フロー プロトコルを使用する特定のエンドポイントの受信トランザクションを受け入れるようにバインディングを構成できます。</span><span class="sxs-lookup"><span data-stu-id="20335-105">Most of the predefined bindings [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="20335-106">さらに、`transactionFlow` 要素とその `transactionProtocol` 属性を使用して、ユーザー独自のカスタム バインディングを構築できます。</span><span class="sxs-lookup"><span data-stu-id="20335-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="20335-107">構成要素を設定するには、表示[\<バインディング >](../../../../docs/framework/misc/binding.md)と[WCF 構成スキーマ](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="20335-107"> setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="20335-108">`transactionFlow` 属性は、バインディングを使用するサービス エンドポイントに対してトランザクション フローを有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="20335-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="20335-109">transactionProtocol の構成</span><span class="sxs-lookup"><span data-stu-id="20335-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="20335-110">`transactionProtocol` 属性は、バインディングを使用するサービス エンドポイントで使用されるトランザクション プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="20335-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="20335-111">以下に、指定したバインディングがトランザクション フローをサポートし、WS-AtomicTransaction プロトコルを使用するように構成する構成セクションの例を示します。</span><span class="sxs-lookup"><span data-stu-id="20335-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"   
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"   
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="20335-112">transactionTimeout の構成</span><span class="sxs-lookup"><span data-stu-id="20335-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="20335-113">`transactionTimeout` サービスの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 属性は、構成ファイルの `behavior` 要素内で構成できます。</span><span class="sxs-lookup"><span data-stu-id="20335-113">You can configure the `transactionTimeout` attribute for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="20335-114">次のコードでは、この設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="20335-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="20335-115">`transactionTimeout` 属性は、サービスで作成された新しいトランザクションを完了させる期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="20335-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="20335-116">この属性は、新しいトランザクションを確立するすべての操作の <xref:System.Transactions.TransactionScope> タイムアウトとして使用され、<xref:System.ServiceModel.OperationBehaviorAttribute> が適用されている場合、<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> プロパティは `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="20335-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="20335-117">このタイムアウトは、2 フェーズ コミット プロトコルにおける、トランザクションの作成からフェーズ 1 の完了までの期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="20335-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="20335-118">この属性を `service` 構成セクション内に設定する場合は、対応するサービスの 1 つ以上のメソッドで、<xref:System.ServiceModel.OperationBehaviorAttribute> プロパティが <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> に設定された `true` を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20335-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="20335-119">使用されるタイムアウト値は常に、この `transactionTimeout` 構成設定と <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> プロパティの小さい方の値になります。</span><span class="sxs-lookup"><span data-stu-id="20335-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20335-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="20335-120">See Also</span></span>  
 [<span data-ttu-id="20335-121">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="20335-121">\<binding></span></span>](../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="20335-122">WCF 構成スキーマ</span><span class="sxs-lookup"><span data-stu-id="20335-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
