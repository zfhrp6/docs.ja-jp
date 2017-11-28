---
title: "データ メンバーの順序"
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
helpviewer_keywords: data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06b311f0ca8e9b0a298cd1d9a5e87ff96d13a787
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="data-member-order"></a><span data-ttu-id="0424a-102">データ メンバーの順序</span><span class="sxs-lookup"><span data-stu-id="0424a-102">Data Member Order</span></span>
<span data-ttu-id="0424a-103">一部のアプリケーションでは、各種のデータ メンバーから送信される、または受信されると予想できるデータの順序 (たとえばシリアル化された XML でデータが表れる順序) がわかると便利です。</span><span class="sxs-lookup"><span data-stu-id="0424a-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="0424a-104">この順序を変更する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="0424a-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="0424a-105">ここでは、このような順序を決定する規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="0424a-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="0424a-106">基本的な規則</span><span class="sxs-lookup"><span data-stu-id="0424a-106">Basic Rules</span></span>  
 <span data-ttu-id="0424a-107">データの順序を決定する基本的な規則には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="0424a-107">The basic rules for data ordering include:</span></span>  
  
-   <span data-ttu-id="0424a-108">データ コントラクト型が継承階層の一部である場合、その基本型のデータ メンバーが常に最初の順番になります。</span><span class="sxs-lookup"><span data-stu-id="0424a-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
-   <span data-ttu-id="0424a-109">次に来るのは <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティが設定されていない、現在の型のデータ メンバー (アルファベット順) になります。</span><span class="sxs-lookup"><span data-stu-id="0424a-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
-   <span data-ttu-id="0424a-110">その次に来るのは、<xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティが設定されているすべてのデータ メンバーです。</span><span class="sxs-lookup"><span data-stu-id="0424a-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="0424a-111">これらのデータ メンバーはまず `Order` プロパティの値によって並べられ、次に特定の `Order` 値を持つメンバーが複数ある場合は、そのアルファベット順に並びます。</span><span class="sxs-lookup"><span data-stu-id="0424a-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="0424a-112">Order 値はスキップされることがあります。</span><span class="sxs-lookup"><span data-stu-id="0424a-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="0424a-113">アルファベット順は、<xref:System.String.CompareOrdinal%2A> メソッドを呼び出すことによって確立されます。</span><span class="sxs-lookup"><span data-stu-id="0424a-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0424a-114">例</span><span class="sxs-lookup"><span data-stu-id="0424a-114">Examples</span></span>  
 <span data-ttu-id="0424a-115">次のコードについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="0424a-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="0424a-116">作成される XML は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0424a-116">The XML produced is similar to the following.</span></span>  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>   
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>   
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>   
</DerivedType>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0424a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0424a-117">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [<span data-ttu-id="0424a-118">データ コントラクトの等価性</span><span class="sxs-lookup"><span data-stu-id="0424a-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [<span data-ttu-id="0424a-119">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="0424a-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
