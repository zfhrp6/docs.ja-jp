---
title: "サービスとトランザクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a206ff3d82378e825cd612a6564366ef1e07977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="services-and-transactions"></a><span data-ttu-id="93e3e-102">サービスとトランザクション</span><span class="sxs-lookup"><span data-stu-id="93e3e-102">Services and Transactions</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="93e3e-103"> アプリケーションでは、クライアントからトランザクションを開始し、そのトランザクションをサービス操作内で調整できます。</span><span class="sxs-lookup"><span data-stu-id="93e3e-103"> applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="93e3e-104">クライアントはトランザクションを開始し、複数のサービス操作を呼び出す可能性があります。サービス操作が、1 つの単位としてコミットまたはロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="93e3e-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="93e3e-105">サービス コントラクトでトランザクション動作を有効にするには、<xref:System.ServiceModel.ServiceBehaviorAttribute> を指定し、クライアント トランザクションを必要とするサービス操作について <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> プロパティと <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="93e3e-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="93e3e-106"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> パラメーターは、未処理の例外がスローされなかった場合に、メソッドが実行されているトランザクションが自動的に完了されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="93e3e-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="93e3e-107">これらの属性を参照してください[ServiceModel トランザクションの属性](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)です。</span><span class="sxs-lookup"><span data-stu-id="93e3e-107"> these attributes, see [ServiceModel Transaction Attributes](../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="93e3e-108">データベース更新の記録など、サービス操作で実行され、リソース マネージャーで管理される作業は、クライアント トランザクションの一部です。</span><span class="sxs-lookup"><span data-stu-id="93e3e-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="93e3e-109"><xref:System.ServiceModel.ServiceBehaviorAttribute> 属性と <xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用して、サービス側のトランザクション動作を制御する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="93e3e-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
```  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog(String.Format("Added {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog(String.Format("Subtracted {0} from {1}", n1, n2));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog(String.Format("Multiplied {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog(String.Format("Divided {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
}  
```  
  
 <span data-ttu-id="93e3e-110">トランザクションを有効にすることができ、トランザクションのクライアントを構成することによってフローしサービス バインド、Ws-atomictransaction プロトコルを使用して設定、 [ \<transactionFlow >](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)要素を`true`ように、次のサンプル構成します。</span><span class="sxs-lookup"><span data-stu-id="93e3e-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"   
          binding="netTcpBinding"   
          bindingConfiguration="netTcpBindingWSAT"   
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="93e3e-111">クライアントは、<xref:System.Transactions.TransactionScope> を作成し、トランザクションのスコープ内でサービス操作を呼び出すことにより、トランザクションを開始できます。</span><span class="sxs-lookup"><span data-stu-id="93e3e-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```  
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="93e3e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="93e3e-112">See Also</span></span>  
 [<span data-ttu-id="93e3e-113">System.ServiceModel でのトランザクション サポート</span><span class="sxs-lookup"><span data-stu-id="93e3e-113">Transactional Support in System.ServiceModel</span></span>](../../../docs/framework/wcf/feature-details/transactional-support-in-system-servicemodel.md)  
 [<span data-ttu-id="93e3e-114">トランザクション モデル</span><span class="sxs-lookup"><span data-stu-id="93e3e-114">Transaction Models</span></span>](../../../docs/framework/wcf/feature-details/transaction-models.md)  
 [<span data-ttu-id="93e3e-115">WS トランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="93e3e-115">WS Transaction Flow</span></span>](../../../docs/framework/wcf/samples/ws-transaction-flow.md)
