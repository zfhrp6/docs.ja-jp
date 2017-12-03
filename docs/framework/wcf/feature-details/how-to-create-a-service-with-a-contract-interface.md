---
title: "方法 : コントラクト インターフェイスを使用してサービスを作成する"
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
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cf3938f96674b07a7938861e217a93babd83101
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="572a9-102">方法 : コントラクト インターフェイスを使用してサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="572a9-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="572a9-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] コントラクトの作成には、インターフェイスの使用が適しています。</span><span class="sxs-lookup"><span data-stu-id="572a9-103">The preferred way to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> <span data-ttu-id="572a9-104">このコントラクトでは、サービスが提供する操作にアクセスするために必要なメッセージのコレクションと構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="572a9-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="572a9-105">このインターフェイスでは、インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用し、公開するメソッドに <xref:System.ServiceModel.OperationContractAttribute> クラスを適用して、入力と出力の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="572a9-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="572a9-106">サービス コントラクトを参照してください[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="572a9-106"> service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="572a9-107">インターフェイスを使用した WCF コントラクトの作成</span><span class="sxs-lookup"><span data-stu-id="572a9-107">Creating a WCF contract with an interface</span></span>  
  
1.  <span data-ttu-id="572a9-108">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]、C#、またはその他の共通言語ランタイム言語を使用して、新しいインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="572a9-108">Create a new interface using [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="572a9-109">インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="572a9-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3.  <span data-ttu-id="572a9-110">インターフェイスのメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="572a9-110">Define the methods in the interface.</span></span>  
  
4.  <span data-ttu-id="572a9-111"><xref:System.ServiceModel.OperationContractAttribute> のパブリック コントラクトの一部として公開する必要のある各メソッドに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="572a9-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="572a9-112">例</span><span class="sxs-lookup"><span data-stu-id="572a9-112">Example</span></span>  
 <span data-ttu-id="572a9-113">次のコード例は、サービス コントラクトを定義するインターフェイスを示しています。</span><span class="sxs-lookup"><span data-stu-id="572a9-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="572a9-114"><xref:System.ServiceModel.OperationContractAttribute> クラスが適用されたメソッドは、既定で要求/応答メッセージ パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="572a9-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="572a9-115">このメッセージ パターンを参照してください[する方法: 要求/応答コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)です。</span><span class="sxs-lookup"><span data-stu-id="572a9-115"> this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="572a9-116">属性のプロパティを設定することにより、他のメッセージ パターンを作成および使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="572a9-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="572a9-117">例については、次を参照してください。[する方法: 一方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)と[する方法: 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)です。</span><span class="sxs-lookup"><span data-stu-id="572a9-117">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="572a9-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="572a9-118">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
