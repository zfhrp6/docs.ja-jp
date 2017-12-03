---
title: "サービス コントラクトの実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 688637ae54e92296d103a681715dd491ba8782ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="da66c-102">サービス コントラクトの実装</span><span class="sxs-lookup"><span data-stu-id="da66c-102">Implementing Service Contracts</span></span>
<span data-ttu-id="da66c-103">サービスは、1 つ以上のエンドポイントでクライアントが使用できる機能を公開するクラスです。</span><span class="sxs-lookup"><span data-stu-id="da66c-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="da66c-104">サービスを作成するには、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] コントラクトを実装するクラスを記述します。</span><span class="sxs-lookup"><span data-stu-id="da66c-104">To create a service, write a class that implements a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] contract.</span></span> <span data-ttu-id="da66c-105">2 つの方法のいずれかでこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="da66c-105">You can do this in one of two ways.</span></span> <span data-ttu-id="da66c-106">コントラクトを個別にインターフェイスとして定義し、そのインターフェイスを実装するクラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="da66c-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="da66c-107">または、クラスに <xref:System.ServiceModel.ServiceContractAttribute> 属性を配置し、サービスのクライアントが使用できるメソッドに <xref:System.ServiceModel.OperationContractAttribute> 属性を配置することによって、クラスとコントラクトを直接作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="da66c-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="da66c-108">サービス クラスの作成</span><span class="sxs-lookup"><span data-stu-id="da66c-108">Creating a service class</span></span>  
 <span data-ttu-id="da66c-109">個別に定義された `IMath` コントラクトを実装するサービスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="da66c-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="da66c-110">また、サービスは直接コントラクトを公開できます。</span><span class="sxs-lookup"><span data-stu-id="da66c-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="da66c-111">`MathService` コントラクトを定義し、実装するサービス クラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="da66c-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="da66c-112">コントラクト名が異なるので、上記の 2 つのサービスが公開するコントラクトはそれぞれ異なります。</span><span class="sxs-lookup"><span data-stu-id="da66c-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="da66c-113">最初の例では、公開されるコントラクトの名前が "`IMath`" であるのに対し、2 番目の例では、コントラクトの名前は "`MathService`" です。</span><span class="sxs-lookup"><span data-stu-id="da66c-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="da66c-114">同時実行やインスタンス化など、いくつかの項目は、サービス実装レベルと操作実装レベルで設定できます。</span><span class="sxs-lookup"><span data-stu-id="da66c-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="da66c-115">[サービスの実装の設計と](../../../docs/framework/wcf/designing-and-implementing-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="da66c-115"> [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="da66c-116">サービス コントラクトを実装したら、そのサービスに 1 つ以上のエンドポイントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da66c-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="da66c-117">[エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="da66c-117"> [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="da66c-118">サービスを実行する方法[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="da66c-118"> how to run a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da66c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="da66c-119">See Also</span></span>  
 [<span data-ttu-id="da66c-120">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="da66c-120">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="da66c-121">方法: コントラクト クラスでサービスを作成</span><span class="sxs-lookup"><span data-stu-id="da66c-121">How to: Create a Service with a Contract Class</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [<span data-ttu-id="da66c-122">方法: コントラクト インターフェイスでサービスを作成</span><span class="sxs-lookup"><span data-stu-id="da66c-122">How to: Create a Service with a Contract Interface</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [<span data-ttu-id="da66c-123">サービスのランタイム動作の指定</span><span class="sxs-lookup"><span data-stu-id="da66c-123">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
