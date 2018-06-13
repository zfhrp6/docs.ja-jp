---
title: '方法 : クラスまたは構造体に基本的なデータ コントラクトを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: bb2cebabc8e51870398689ea032d27c72f0503b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490069"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="337ba-102">方法 : クラスまたは構造体に基本的なデータ コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="337ba-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="337ba-103">このトピックでは、クラスまたは構造体を使用してデータ コントラクトを作成する基本的な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="337ba-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="337ba-104">データ コントラクトとその使用方法の詳細については、次を参照してください。[を使用してデータ コントラクト](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="337ba-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="337ba-105">基本的な Windows Communication Foundation (WCF) サービスとクライアントを作成する手順について説明するチュートリアルとして、次を参照してください。、[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)です。</span><span class="sxs-lookup"><span data-stu-id="337ba-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="337ba-106">基本的なサービスとクライアントで構成されている実際のサンプル アプリケーションを参照してください。[基本的なデータ コントラクト](../../../../docs/framework/wcf/samples/basic-data-contract.md)です。</span><span class="sxs-lookup"><span data-stu-id="337ba-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="337ba-107">クラスまたは構造体に基本的なデータ コントラクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="337ba-107">To create a basic data contract for a class or structure</span></span>  
  
1.  <span data-ttu-id="337ba-108">クラスに <xref:System.Runtime.Serialization.DataContractAttribute> 属性を適用することにより、データ コントラクトを持つ型であることを宣言します。</span><span class="sxs-lookup"><span data-stu-id="337ba-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="337ba-109">パブリック型は、属性のないものも含めてすべてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="337ba-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="337ba-110"><xref:System.Runtime.Serialization.DataContractSerializer> 属性がない場合は、<xref:System.Runtime.Serialization.DataContractAttribute> によってデータ コントラクトが推論されます。</span><span class="sxs-lookup"><span data-stu-id="337ba-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="337ba-111">詳細については、次を参照してください。[シリアル化できる型](../../../../docs/framework/wcf/feature-details/serializable-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="337ba-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2.  <span data-ttu-id="337ba-112">シリアル化するメンバー (プロパティ、フィールド、またはイベント) を定義します。これは、該当する各メンバーに <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用することで行います。</span><span class="sxs-lookup"><span data-stu-id="337ba-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="337ba-113">このようなメンバーのことを、データ メンバーと呼びます。</span><span class="sxs-lookup"><span data-stu-id="337ba-113">These members are called data members.</span></span> <span data-ttu-id="337ba-114">既定では、すべてのパブリック型がシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="337ba-114">By default, all public types are serializable.</span></span> <span data-ttu-id="337ba-115">詳細については、次を参照してください。[シリアル化できる型](../../../../docs/framework/wcf/feature-details/serializable-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="337ba-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="337ba-116">プライベート フィールドであっても、<xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用すると、データが外部に公開されることになります。</span><span class="sxs-lookup"><span data-stu-id="337ba-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="337ba-117">機密性のあるデータが含まれていないかどうか確認してください。</span><span class="sxs-lookup"><span data-stu-id="337ba-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="337ba-118">例</span><span class="sxs-lookup"><span data-stu-id="337ba-118">Example</span></span>  
 <span data-ttu-id="337ba-119">次の例では、`Person` 属性と <xref:System.Runtime.Serialization.DataContractAttribute> 属性をクラスとそのメンバーに適用して、<xref:System.Runtime.Serialization.DataMemberAttribute> 型のデータ コントラクトを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="337ba-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="337ba-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="337ba-120">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="337ba-121">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="337ba-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="337ba-122">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="337ba-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="337ba-123">はじめに</span><span class="sxs-lookup"><span data-stu-id="337ba-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
