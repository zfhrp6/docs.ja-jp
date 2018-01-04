---
title: "データ コントラクトの等価性"
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
helpviewer_keywords: data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4059fa401d082f4408080cf5fd13f1331314a2d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="data-contract-equivalence"></a><span data-ttu-id="ed831-102">データ コントラクトの等価性</span><span class="sxs-lookup"><span data-stu-id="ed831-102">Data Contract Equivalence</span></span>
<span data-ttu-id="ed831-103">クライアントがサービスに特定の型のデータを正常に送信するために、またはサービスがクライアントにデータを正常に送信するために、送信する型が受信側に存在する必要があるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="ed831-103">For a client to successfully send data of a certain type to a service, or a service to successfully send data to a client, the sent type does not necessarily have to exist on the receiving end.</span></span> <span data-ttu-id="ed831-104">両方の型のデータ コントラクトが同等であるということが唯一の要件です</span><span class="sxs-lookup"><span data-stu-id="ed831-104">The only requirement is that the data contracts of both types be equivalent.</span></span> <span data-ttu-id="ed831-105">(場合によっては、厳密に一致が必要でないで説明したよう[データ コントラクトのバージョン管理](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md))。</span><span class="sxs-lookup"><span data-stu-id="ed831-105">(Sometimes, strict equivalence is not required, as discussed in [Data Contract Versioning](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)</span></span>  
  
 <span data-ttu-id="ed831-106">データ コントラクトを同等にするには、そのデータ コントラクトに同じ名前空間と名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed831-106">For data contracts to be equivalent, they must have the same namespace and name.</span></span> <span data-ttu-id="ed831-107">また、一方のデータ コントラクトの各データ メンバーには、他方のデータ コントラクトに同等のデータ メンバーがある必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed831-107">Additionally, each data member on one side must have an equivalent data member on the other side.</span></span>  
  
 <span data-ttu-id="ed831-108">データ メンバーを同等にするには、そのデータ メンバーに同じ名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed831-108">For data members to be equivalent, they must have the same name.</span></span> <span data-ttu-id="ed831-109">さらに、データ メンバーは同じ型のデータを表す必要があります。つまり、データ コントラクトが同等である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed831-109">Additionally, they must represent the same type of data; that is, their data contracts must be equivalent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed831-110">データ コントラクト名と名前空間、およびデータ メンバー名は、大文字と小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="ed831-110">Note that data contract names and namespaces, as well as data member names, are case-sensitive.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ed831-111">データ コントラクト名と名前空間、さらにデータ メンバー名を参照してください[データ コントラクト名](../../../../docs/framework/wcf/feature-details/data-contract-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="ed831-111"> data contract names and namespaces, as well as data member names, see [Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md).</span></span>  
  
 <span data-ttu-id="ed831-112">2 つの型が両側 (送信者と受信者) に存在し、そのデータ コントラクトが同等でない場合 (たとえば、異なるデータ メンバーを含んでいる場合)、そのデータ コントラクトに同じ名前と名前空間を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ed831-112">If two types exist on the same side (sender or receiver) and their data contracts are not equivalent (for example, they have different data members), you should not give them the same name and namespace.</span></span> <span data-ttu-id="ed831-113">同じ名前と名前空間を使用すると、例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed831-113">Doing so may cause exceptions to be thrown.</span></span>  
  
 <span data-ttu-id="ed831-114">次の型のデータ コントラクトは同等です。</span><span class="sxs-lookup"><span data-stu-id="ed831-114">The data contracts for the following types are equivalent:</span></span>  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a><span data-ttu-id="ed831-115">データ メンバーの順序とデータ コントラクトの等価性</span><span class="sxs-lookup"><span data-stu-id="ed831-115">Data Member Order and Data Contract equivalence</span></span>  
 <span data-ttu-id="ed831-116"><xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> クラスの <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティの使用は、データ コントラクトの等価性に影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="ed831-116">Using the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> class may affect data contract equivalence.</span></span> <span data-ttu-id="ed831-117">データ コントラクトを同等にするには、データ メンバーが同じ順序で現れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed831-117">The data contracts must have members that appear in the same order to be equivalent.</span></span> <span data-ttu-id="ed831-118">既定の順序はアルファベット順です。</span><span class="sxs-lookup"><span data-stu-id="ed831-118">The default order is alphabetical.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="ed831-119">[データ メンバーの順序](../../../../docs/framework/wcf/feature-details/data-member-order.md)です。</span><span class="sxs-lookup"><span data-stu-id="ed831-119"> [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="ed831-120">たとえば、次のコードでは、同等なデータ コントラクトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ed831-120">For example, the following code results in equivalent data contracts.</span></span>  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 <span data-ttu-id="ed831-121">次のコードでは、同等なデータ コントラクトは生成されません。</span><span class="sxs-lookup"><span data-stu-id="ed831-121">However, the following does not result in an equivalent data contract.</span></span>  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a><span data-ttu-id="ed831-122">継承、インターフェイス、およびデータ コントラクトの等価性</span><span class="sxs-lookup"><span data-stu-id="ed831-122">Inheritance, Interfaces, and Data Contract Equivalence</span></span>  
 <span data-ttu-id="ed831-123">等価性を判断するとき、別のデータ コントラクトから継承したデータ コントラクトは、基本型のすべてのデータ メンバーを含んでいる 1 つのデータ コントラクトとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="ed831-123">When determining equivalence, a data contract that inherits from another data contract is treated as if it is just one data contract that includes all of the data members from the base type.</span></span> <span data-ttu-id="ed831-124">データ メンバーの順序が一致する必要があり、基本型のメンバーは派生型のメンバーより前に現れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed831-124">Keep in mind that the order of the data members must match and that base type members precede derived type members in the order.</span></span> <span data-ttu-id="ed831-125">さらに、次のコード例のように、2 つのデータ メンバーの順序の値が同じ場合、そのデータ メンバーの順序はアルファベット順になります。</span><span class="sxs-lookup"><span data-stu-id="ed831-125">Furthermore, if, as in the following code example, two data members have the same order value, the ordering for those data members is alphabetical.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="ed831-126">[データ メンバーの順序](../../../../docs/framework/wcf/feature-details/data-member-order.md)です。</span><span class="sxs-lookup"><span data-stu-id="ed831-126"> [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="ed831-127">次の例では、型 `Employee` のデータ コントラクトは型 `Worker` のデータ コントラクトと同等です。</span><span class="sxs-lookup"><span data-stu-id="ed831-127">In the following example, the data contract for type `Employee` is equivalent to the data contract for the type `Worker`.</span></span>  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 <span data-ttu-id="ed831-128">クライアントとサービスの間でパラメーターを渡し、値を返すとき、受信エンドポイントが派生クラスからのデータ コントラクトを予期している場合、基本クラスからのデータ コントラクトを送信できません。</span><span class="sxs-lookup"><span data-stu-id="ed831-128">When passing parameters and return values between a client and a service, a data contract from a base class cannot be sent when the receiving endpoint expects a data contract from a derived class.</span></span> <span data-ttu-id="ed831-129">これは、オブジェクト指向プログラミングの原則に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ed831-129">This is in accordance with object-oriented programming tenets.</span></span> <span data-ttu-id="ed831-130">前の例では、型のオブジェクトで`Person`ときに送信することはできません、`Employee`が必要です。</span><span class="sxs-lookup"><span data-stu-id="ed831-130">In the previous example, an object of type `Person` cannot be sent when an `Employee` is expected.</span></span>  
  
 <span data-ttu-id="ed831-131">基本クラスからのデータ コントラクトが予期されるときに派生クラスからのデータ コントラクトを送信することは可能ですが、受信エンドポイントが <xref:System.Runtime.Serialization.KnownTypeAttribute> を使用して派生型を認識している場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="ed831-131">A data contract from a derived class can be sent when a data contract from a base class is expected, but only if the receiving endpoint "knows" of the derived type using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="ed831-132">[データが既知の型をコントラクト](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="ed831-132"> [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="ed831-133">上記の例では、`Employee` が予期されるときに、受信者のコードが既知の型のリストに `Person` を追加するために <xref:System.Runtime.Serialization.KnownTypeAttribute> を使用している場合のみ、型 Employee のオブジェクトを送信できます。</span><span class="sxs-lookup"><span data-stu-id="ed831-133">In the previous example, an object of type `Employee` can be sent when a `Person` is expected, but only if the receiver code employs the <xref:System.Runtime.Serialization.KnownTypeAttribute> to include it in the list of known types.</span></span>  
  
 <span data-ttu-id="ed831-134">アプリケーション間でパラメーターを渡し、値を返すとき、予期される型がインターフェイスの場合、その型は、型が <xref:System.Object> の予期される型と同等です。</span><span class="sxs-lookup"><span data-stu-id="ed831-134">When passing parameters and return values between applications, if the expected type is an interface, it is equivalent to the expected type being of type <xref:System.Object>.</span></span> <span data-ttu-id="ed831-135">すべての型は最終的に <xref:System.Object> から派生するので、すべてのデータ コントラクトは最終的に、<xref:System.Object> のデータ コントラクトから派生します。</span><span class="sxs-lookup"><span data-stu-id="ed831-135">Because every type ultimately derives from <xref:System.Object>, every data contract ultimately derives from the data contract for <xref:System.Object>.</span></span> <span data-ttu-id="ed831-136">したがって、インターフェイスが予期されるとき、すべてのデータ コントラクト型を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="ed831-136">Thus, any data contract type can be passed when an interface is expected.</span></span> <span data-ttu-id="ed831-137">インターフェイス; で正常に動作する追加手順が必要詳細については、次を参照してください。[データ コントラクトの既知の型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="ed831-137">Additional steps are required to successfully work with interfaces; for more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed831-138">参照</span><span class="sxs-lookup"><span data-stu-id="ed831-138">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="ed831-139">データ メンバーの順序</span><span class="sxs-lookup"><span data-stu-id="ed831-139">Data Member Order</span></span>](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [<span data-ttu-id="ed831-140">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="ed831-140">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="ed831-141">データ コントラクト名</span><span class="sxs-lookup"><span data-stu-id="ed831-141">Data Contract Names</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
