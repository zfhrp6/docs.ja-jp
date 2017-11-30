---
title: "方法 : クラスを使用して Windows Communication Foundation コントラクトを作成する"
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
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf32559f9b5a1040390562cc8492646288494638
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="9d613-102">方法 : クラスを使用して Windows Communication Foundation コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="9d613-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="9d613-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] コントラクトの作成には、インターフェイスの使用が適しています。</span><span class="sxs-lookup"><span data-stu-id="9d613-103">The preferred way of creating a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="9d613-104">[する方法: サービス コントラクトを定義する](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d613-104"> [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="9d613-105">ここで説明する代替方法では、クラスを作成してから、<xref:System.ServiceModel.ServiceContractAttribute> 属性を直接そのクラスに適用し、<xref:System.ServiceModel.OperationContractAttribute> 属性をコントラクトに含まれるクラス内の各メソッドに適用します。</span><span class="sxs-lookup"><span data-stu-id="9d613-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="9d613-106">`[ServiceContract]` と `[ServiceContractAttribute]` は、同じことを行います。</span><span class="sxs-lookup"><span data-stu-id="9d613-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="9d613-107">`[OperationContract]` と `[OperationContractAttribute]` でも、同様です。</span><span class="sxs-lookup"><span data-stu-id="9d613-107">The same thing it true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="9d613-108">いずれの場合も、前者は後者の短縮形です。</span><span class="sxs-lookup"><span data-stu-id="9d613-108">In each case the former is shorthand for the latter.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9d613-109">サービス コントラクトを参照してください[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d613-109"> service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="9d613-110">クラスを使用した Windows Communication Foundation コントラクトの作成</span><span class="sxs-lookup"><span data-stu-id="9d613-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1.  <span data-ttu-id="9d613-111">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]、C#、またはその他の任意の共通言語ランタイム言語を使用して、新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d613-111">Create a new class using [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="9d613-112">クラスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="9d613-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3.  <span data-ttu-id="9d613-113">クラスでメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d613-113">Create methods in the class.</span></span>  
  
4.  <span data-ttu-id="9d613-114"><xref:System.ServiceModel.OperationContractAttribute> のパブリック コントラクトの一部として公開する必要のある各メソッドに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="9d613-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d613-115">例</span><span class="sxs-lookup"><span data-stu-id="9d613-115">Example</span></span>  
 <span data-ttu-id="9d613-116">次のコード例は、サービス コントラクトを定義するクラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="9d613-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="9d613-117"><xref:System.ServiceModel.OperationContractAttribute> クラスが適用されたメソッドは、既定で要求/応答メッセージ パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d613-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9d613-118">このメッセージ パターンを参照してください[する方法: 要求/応答コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d613-118"> this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="9d613-119">属性のプロパティを設定することにより、他のメッセージ パターンを作成および使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9d613-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="9d613-120">例については、次を参照してください。[する方法: 一方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)と[する方法: 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d613-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d613-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d613-121">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
