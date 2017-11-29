---
title: "データ メンバーの既定値"
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
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 776106da717a81094679002c99d00a470a637947
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="data-member-default-values"></a><span data-ttu-id="18e17-102">データ メンバーの既定値</span><span class="sxs-lookup"><span data-stu-id="18e17-102">Data Member Default Values</span></span>
<span data-ttu-id="18e17-103">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]、型の概念がある*既定値*です。</span><span class="sxs-lookup"><span data-stu-id="18e17-103">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], types have a concept of *default values*.</span></span> <span data-ttu-id="18e17-104">たとえば、参照型の既定値は `null` で、整数型の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="18e17-104">For example, for any reference type the default value is `null`, and for an integer type it is zero.</span></span> <span data-ttu-id="18e17-105">しかし、データ メンバーが既定値に設定されている場合は、シリアル化されたデータからそのデータ メンバーを省略することが望ましいことがあります。</span><span class="sxs-lookup"><span data-stu-id="18e17-105">It is occasionally desirable to omit a data member from serialized data when it is set to its default value.</span></span> <span data-ttu-id="18e17-106">それは、メンバーが既定値に設定されているために実際の値をシリアル化する必要がなく、パフォーマンスの点で有利だからです。</span><span class="sxs-lookup"><span data-stu-id="18e17-106">Because the member has a default value, an actual value need not be serialized; this has a performance advantage.</span></span>  
  
 <span data-ttu-id="18e17-107">シリアル化されたデータからデータ メンバーを省略するには、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティを `false` に設定します (既定値は `true`)。</span><span class="sxs-lookup"><span data-stu-id="18e17-107">To omit a member from serialized data, set the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to `false` (the default is `true`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18e17-108">相互運用性の維持やデータ サイズの縮小のような特別なニーズがある場合は、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> プロパティを `false` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18e17-108">You should set the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property to `false` if there is a specific need to do so, such as for interoperability or data size reduction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18e17-109">例</span><span class="sxs-lookup"><span data-stu-id="18e17-109">Example</span></span>  
 <span data-ttu-id="18e17-110">次のコードには、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> が `false` に設定された複数のメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="18e17-110">The following code has several members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> set to `false`.</span></span>  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 <span data-ttu-id="18e17-111">このクラスのインスタンスをシリアル化すると、次に示すように `employeeName` と `employeeID` がシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="18e17-111">If an instance of this class is serialized, the result is as follows: `employeeName` and `employeeID` is serialized.</span></span> <span data-ttu-id="18e17-112">`employeeName` の null 値と `employeeID` の値 0 は、シリアル化されるデータに明示的に含められます。</span><span class="sxs-lookup"><span data-stu-id="18e17-112">The null value for `employeeName` and the zero value for `employeeID` is explicitly part of the serialized data.</span></span> <span data-ttu-id="18e17-113">ただし、`position`、`salary`、および `bonus` のメンバーはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="18e17-113">However, the `position`, `salary`, and `bonus` members are not serialized.</span></span> <span data-ttu-id="18e17-114">また、`targetSalary` プロパティは <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> に設定されていますが、57800 が .NET の整数の既定値 (0) と一致しないため、`false` が通常どおりにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="18e17-114">Finally, `targetSalary` is serialized as usual, even though the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property is set to `false`, because 57800 does not match the .NET default value for an integer, which is zero.</span></span>  
  
### <a name="xml-representation"></a><span data-ttu-id="18e17-115">XML 表現</span><span class="sxs-lookup"><span data-stu-id="18e17-115">XML Representation</span></span>  
 <span data-ttu-id="18e17-116">前の例を XML にシリアル化すると、生成される XML 表現は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="18e17-116">If the previous example is serialized to XML, the representation is similar to the following.</span></span>  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 <span data-ttu-id="18e17-117">`xsi:nil` 属性は W3C (World Wide Web Consortium) XML スキーマ インスタンス名前空間の特別な属性であり、null 値を明示的に表すための相互運用可能な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="18e17-117">The `xsi:nil` attribute is a special attribute in the World Wide Web Consortium (W3C) XML Schema instance namespace that provides an interoperable way to explicitly represent a null value.</span></span> <span data-ttu-id="18e17-118">この XML には、地位、給与、ボーナスの各データ メンバーに関する情報がまったく含まれていないことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="18e17-118">Note that there is no information at all in the XML about position, salary, and bonus data members.</span></span> <span data-ttu-id="18e17-119">これらのデータ メンバーは、受信エンドポイントで、それぞれ `null`、0、および `null` として解釈します。</span><span class="sxs-lookup"><span data-stu-id="18e17-119">The receiving end can interpret these as `null`, zero, and `null`, respectively.</span></span> <span data-ttu-id="18e17-120">これらをサードパーティ製のデシリアライザーで正しく解釈できる保証はないため、このパターンはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="18e17-120">There is no guarantee that a third-party deserializer can make the correct interpretation, which is why this pattern is not recommended.</span></span> <span data-ttu-id="18e17-121"><xref:System.Runtime.Serialization.DataContractSerializer> クラスを使用すると、値が指定されていない場合でも、常に正しい解釈が選択されます。</span><span class="sxs-lookup"><span data-stu-id="18e17-121">The <xref:System.Runtime.Serialization.DataContractSerializer> class always selects the correct interpretation for missing values.</span></span>  
  
### <a name="interaction-with-isrequired"></a><span data-ttu-id="18e17-122">IsRequired との対話</span><span class="sxs-lookup"><span data-stu-id="18e17-122">Interaction with IsRequired</span></span>  
 <span data-ttu-id="18e17-123">説明したよう[データ コントラクトのバージョン管理](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)、<xref:System.Runtime.Serialization.DataMemberAttribute>属性が、<xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>プロパティ (既定値は`false`)。</span><span class="sxs-lookup"><span data-stu-id="18e17-123">As discussed in [Data Contract Versioning](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property (the default is `false`).</span></span> <span data-ttu-id="18e17-124">このプロパティは、シリアル化されたデータを逆シリアル化する際に、指定されたデータ メンバーが存在する必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="18e17-124">The property indicates whether a given data member must be present in the serialized data when it is being deserialized.</span></span> <span data-ttu-id="18e17-125">`IsRequired` が `true` (値が存在する必要がある) に設定され、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> が `false` (既定値に設定されている場合は、値が存在する必要がない) に設定されている場合は、結果が矛盾するため、このデータ メンバーの既定値をシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="18e17-125">If `IsRequired` is set to `true`, (which indicates that a value must be present) and <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> is set to `false` (indicating that the value must not be present if it is set to its default value), default values for this data member cannot be serialized because the results would be contradictory.</span></span> <span data-ttu-id="18e17-126">このようなデータ メンバーを既定値 (通常は `null` または 0) に設定してシリアル化を実行すると、<xref:System.Runtime.Serialization.SerializationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="18e17-126">If such a data member is set to its default value (usually `null` or zero) and a serialization is attempted, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
### <a name="schema-representation"></a><span data-ttu-id="18e17-127">スキーマ表現</span><span class="sxs-lookup"><span data-stu-id="18e17-127">Schema Representation</span></span>  
 <span data-ttu-id="18e17-128">XML スキーマ定義言語 (XSD) スキーマの形式をデータ メンバーの詳細と、`EmitDefaultValue`プロパティに設定されている`false`で説明した[データ コントラクト スキーマの参照](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)です。</span><span class="sxs-lookup"><span data-stu-id="18e17-128">The details of the XML Schema definition language (XSD) schema representation of data members when the `EmitDefaultValue` property is set to `false` are discussed in [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).</span></span> <span data-ttu-id="18e17-129">以下に、その概要を簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="18e17-129">However, the following is a brief overview:</span></span>  
  
-   <span data-ttu-id="18e17-130"><xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> を `false` に設定すると、スキーマでは [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に固有の注釈として表現されます。</span><span class="sxs-lookup"><span data-stu-id="18e17-130">When the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> is set to `false`, it is represented in the schema as an annotation specific to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="18e17-131">この情報を表すための相互運用可能な方法はありません。</span><span class="sxs-lookup"><span data-stu-id="18e17-131">There is no interoperable way to represent this information.</span></span> <span data-ttu-id="18e17-132">特に、スキーマにおける "default" 属性はこの目的では使用されません。また、`minOccurs` 属性は <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 設定だけに影響され、`nillable` 属性はデータ メンバーの型だけに影響されます。</span><span class="sxs-lookup"><span data-stu-id="18e17-132">In particular, the "default" attribute in the schema is not used for this purpose, the `minOccurs` attribute is affected only by the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> setting, and the `nillable` attribute is affected only by the type of the data member.</span></span>  
  
-   <span data-ttu-id="18e17-133">使用される実際の既定値は、スキーマには存在しません。</span><span class="sxs-lookup"><span data-stu-id="18e17-133">The actual default value to use is not present in the schema.</span></span> <span data-ttu-id="18e17-134">指定されていない要素が適切に解釈されるかどうかは、受信エンドポイントに依存します。</span><span class="sxs-lookup"><span data-stu-id="18e17-134">It is up to the receiving endpoint to appropriately interpret a missing element.</span></span>  
  
 <span data-ttu-id="18e17-135">スキーマのインポートでは、前述の <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> に固有の注釈が検出されるたびに `false` プロパティが自動的に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="18e17-135">On schema import, the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property is automatically set to `false` whenever the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-specific annotation mentioned previously is detected.</span></span> <span data-ttu-id="18e17-136">また、このプロパティは、一般に `false` Web サービスを使用したときに発生する特定の相互運用シナリオをサポートするために、`nillable` プロパティが `false` に設定されている参照型に対しても、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="18e17-136">It is also set to `false` for reference types that have the `nillable` property set to `false` to support specific interoperability scenarios that commonly occur when consuming [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e17-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="18e17-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>
