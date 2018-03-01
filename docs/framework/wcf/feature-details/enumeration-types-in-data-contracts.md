---
title: "データ コントラクトの列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7989996f7ed64ba4b85ddc1ca01538ec05e99e1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="enumeration-types-in-data-contracts"></a><span data-ttu-id="b73d0-102">データ コントラクトの列挙型</span><span class="sxs-lookup"><span data-stu-id="b73d0-102">Enumeration Types in Data Contracts</span></span>
<span data-ttu-id="b73d0-103">列挙はデータ コントラクト モデルで表現できます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-103">Enumerations can be expressed in the data contract model.</span></span> <span data-ttu-id="b73d0-104">このトピックでは、いくつかの例を通してプログラミング モデルを説明します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-104">This topic walks through several examples that explain the programming model.</span></span>  
  
## <a name="enumeration-basics"></a><span data-ttu-id="b73d0-105">列挙の基本</span><span class="sxs-lookup"><span data-stu-id="b73d0-105">Enumeration Basics</span></span>  
 <span data-ttu-id="b73d0-106">データ コントラクト モデルで列挙型を使用する 1 つの方法として、<xref:System.Runtime.Serialization.DataContractAttribute> 属性を型に割り当てる方法があります。</span><span class="sxs-lookup"><span data-stu-id="b73d0-106">One way to use enumeration types in the data contract model is to apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="b73d0-107">この場合、データ コントラクトに含める必要のある各メンバーに <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b73d0-107">You must then apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to each member that must be included in the data contract.</span></span>  
  
 <span data-ttu-id="b73d0-108">2 つのクラスを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-108">The following example shows two classes.</span></span> <span data-ttu-id="b73d0-109">1 つ目は列挙を使用し、2 つ目は列挙を定義します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-109">The first uses the enumeration and the second defines the enumeration.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 <span data-ttu-id="b73d0-110">`Car` クラスのインスタンスは、`condition` フィールドの値が `New`、`Used`、`Rental` のいずれかに設定されている場合にのみ送受信できます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-110">An instance of the `Car` class can be sent or received only if the `condition` field is set to one of the values `New`, `Used`, or `Rental`.</span></span> <span data-ttu-id="b73d0-111">`condition` が、`Broken` または `Stolen` の場合、<xref:System.Runtime.Serialization.SerializationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-111">If the `condition` is `Broken` or `Stolen`, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
 <span data-ttu-id="b73d0-112"><xref:System.Runtime.Serialization.DataContractAttribute> プロパティ (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> と <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) を、列挙データ コントラクトとして通常通り使用できます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-112">You can use the <xref:System.Runtime.Serialization.DataContractAttribute> properties (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> and <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) as usual for enumeration data contracts.</span></span>  
  
### <a name="enumeration-member-values"></a><span data-ttu-id="b73d0-113">列挙メンバー値</span><span class="sxs-lookup"><span data-stu-id="b73d0-113">Enumeration Member Values</span></span>  
 <span data-ttu-id="b73d0-114">通常、データ コントラクトには、数値ではなく列挙メンバー名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-114">Generally the data contract includes enumeration member names, not numerical values.</span></span> <span data-ttu-id="b73d0-115">ただし、データ コントラクト モデルを使用しているときに、受信側が [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントである場合、エクスポートされたスキーマは数値を保持します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-115">However, when using the data contract model, if the receiving side is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, the exported schema preserves the numerical values.</span></span> <span data-ttu-id="b73d0-116">これはいない大文字と小文字を使用する場合、 [XmlSerializer クラスを使用して](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)です。</span><span class="sxs-lookup"><span data-stu-id="b73d0-116">Note that this is not the case when using the [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span>  
  
 <span data-ttu-id="b73d0-117">前の例では、`condition` が `Used` に設定され、データが XML にシリアル化されると、結果の XML は `<condition>Used</condition>` になりますが `<condition>1</condition>` にはなりません。</span><span class="sxs-lookup"><span data-stu-id="b73d0-117">In the preceding example, if `condition` is set to `Used` and the data is serialized to XML, the resulting XML is `<condition>Used</condition>` and not `<condition>1</condition>`.</span></span> <span data-ttu-id="b73d0-118">したがって、次のデータ コントラクトは、`CarConditionEnum` のデータ コントラクトと同じです。</span><span class="sxs-lookup"><span data-stu-id="b73d0-118">Therefore, the following data contract is equivalent to the data contract of `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 <span data-ttu-id="b73d0-119">たとえば、`CarConditionEnum` を送信側で使用し、`CarConditionWithNumbers` を受信側で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-119">For example, you can use `CarConditionEnum` on the sending side and `CarConditionWithNumbers` on the receiving side.</span></span> <span data-ttu-id="b73d0-120">送信側で `Used` に値 "1" を使用し、受信側で値 "20" を使用しても、XML 表現は送信側と受信側共に `<condition>Used</condition>` です。</span><span class="sxs-lookup"><span data-stu-id="b73d0-120">Although the sending side uses the value "1" for `Used` and the receiving side uses the value "20," the XML representation is `<condition>Used</condition>` for both sides.</span></span>  
  
 <span data-ttu-id="b73d0-121">データ コントラクトに含めるには、<xref:System.Runtime.Serialization.EnumMemberAttribute> 属性を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b73d0-121">To be included in the data contract, you must apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="b73d0-122">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] では、列挙に特殊な値 0 (ゼロ) を常に割り当てることができます。これはまた、すべての列挙の既定値になります。</span><span class="sxs-lookup"><span data-stu-id="b73d0-122">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you can always apply the special value 0 (zero) to an enumeration, which is also the default value for any enumeration.</span></span> <span data-ttu-id="b73d0-123">ただし、この特殊値ゼロも <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性を使用してマークされない限りシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="b73d0-123">However, even this special zero value cannot be serialized unless it is marked with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="b73d0-124">これには、次のような 2 つの例外があります。</span><span class="sxs-lookup"><span data-stu-id="b73d0-124">There are two exceptions to this:</span></span>  
  
-   <span data-ttu-id="b73d0-125">フラグ列挙体 (このトピックの後で説明)</span><span class="sxs-lookup"><span data-stu-id="b73d0-125">Flag enumerations (discussed later in this topic).</span></span>  
  
-   <span data-ttu-id="b73d0-126"><xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> プロパティが `false` に設定された列挙データ メンバー (この場合、値がゼロの列挙はシリアル化されたデータから除外される)</span><span class="sxs-lookup"><span data-stu-id="b73d0-126">Enumeration data members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property set to `false` (in which case, the enumeration with the value zero is omitted from the serialized data).</span></span>  
  
### <a name="customizing-enumeration-member-values"></a><span data-ttu-id="b73d0-127">列挙メンバー値のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="b73d0-127">Customizing Enumeration Member Values</span></span>  
 <span data-ttu-id="b73d0-128">データ コントラクトの一部を形成する列挙メンバー値は、<xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> 属性の <xref:System.Runtime.Serialization.EnumMemberAttribute> プロパティを使ってカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-128">You can customize the enumeration member value that forms a part of the data contract by using the <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> property of the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="b73d0-129">たとえば、次のデータ コントラクトは `CarConditionEnum` のデータ コントラクトとも等価です。</span><span class="sxs-lookup"><span data-stu-id="b73d0-129">For example, the following data contract is also equivalent to the data contract of the `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 <span data-ttu-id="b73d0-130">シリアル化されると、`PreviouslyOwned` の値には XML 表現 `<condition>Used</condition>` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-130">When serialized, the value of `PreviouslyOwned` has the XML representation `<condition>Used</condition>`.</span></span>  
  
## <a name="simple-enumerations"></a><span data-ttu-id="b73d0-131">単純な列挙</span><span class="sxs-lookup"><span data-stu-id="b73d0-131">Simple Enumerations</span></span>  
 <span data-ttu-id="b73d0-132"><xref:System.Runtime.Serialization.DataContractAttribute> 属性が割り当てられていない列挙型をシリアル化することもできます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-132">You can also serialize enumeration types to which the <xref:System.Runtime.Serialization.DataContractAttribute> attribute has not been applied.</span></span> <span data-ttu-id="b73d0-133">このような列挙型は、前の説明とまったく同じように扱われます。ただし、すべてのメンバー (<xref:System.NonSerializedAttribute> 属性は適用されていない) に <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性が適用されているかのように扱われる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="b73d0-133">Such enumeration types are treated exactly as previously described, except that every member (that does not have the <xref:System.NonSerializedAttribute> attribute applied) is treated as if the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute has been applied.</span></span> <span data-ttu-id="b73d0-134">たとえば、次の列挙は、前の `CarConditionEnum` の例と同じデータ コントラクトが暗黙的に含まれます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-134">For example, the following enumeration implicitly has a data contract equivalent to the preceding `CarConditionEnum` example.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 <span data-ttu-id="b73d0-135">列挙のデータ コントラクト名と名前空間、および列挙メンバー値をカスタマイズする必要がない場合に、単純な列挙を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-135">You can use simple enumerations when you do not need to customize the enumeration's data contract name and namespace and the enumeration member values.</span></span>  
  
#### <a name="notes-on-simple-enumerations"></a><span data-ttu-id="b73d0-136">単純な列挙に関するメモ</span><span class="sxs-lookup"><span data-stu-id="b73d0-136">Notes on Simple Enumerations</span></span>  
 <span data-ttu-id="b73d0-137"><xref:System.Runtime.Serialization.EnumMemberAttribute> 属性を単純な列挙に適用しても効力はありません。</span><span class="sxs-lookup"><span data-stu-id="b73d0-137">Applying the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to simple enumerations has no effect.</span></span>  
  
 <span data-ttu-id="b73d0-138"><xref:System.SerializableAttribute> 属性を列挙に適用してもしなくても変わりはありません。</span><span class="sxs-lookup"><span data-stu-id="b73d0-138">It makes no difference whether or not the <xref:System.SerializableAttribute> attribute is applied to the enumeration.</span></span>  
  
 <span data-ttu-id="b73d0-139"><xref:System.Runtime.Serialization.DataContractSerializer> クラスが、列挙メンバーに適用された <xref:System.NonSerializedAttribute> 属性を受け入れるという事実は、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> と <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> の動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="b73d0-139">The fact that the <xref:System.Runtime.Serialization.DataContractSerializer> class honors the <xref:System.NonSerializedAttribute> attribute applied to enumeration members is different from the behavior of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="b73d0-140">この 2 つのシリアライザーは <xref:System.NonSerializedAttribute> 属性を無視します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-140">Both of those serializers ignore the <xref:System.NonSerializedAttribute> attribute.</span></span>  
  
## <a name="flag-enumerations"></a><span data-ttu-id="b73d0-141">フラグ列挙体</span><span class="sxs-lookup"><span data-stu-id="b73d0-141">Flag Enumerations</span></span>  
 <span data-ttu-id="b73d0-142">列挙体に <xref:System.FlagsAttribute> 属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-142">You can apply the <xref:System.FlagsAttribute> attribute to enumerations.</span></span> <span data-ttu-id="b73d0-143">この場合、ゼロ個以上の列挙値のリストを同時に送受信できます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-143">In that case, a list of zero or more enumeration values can be sent or received simultaneously.</span></span>  
  
 <span data-ttu-id="b73d0-144">これを行うには、<xref:System.Runtime.Serialization.DataContractAttribute> 属性をフラグ列挙体に適用し、2 の累乗であるすべてのメンバーを、<xref:System.Runtime.Serialization.EnumMemberAttribute> 属性を使用してマークします。</span><span class="sxs-lookup"><span data-stu-id="b73d0-144">To do so, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the flag enumeration and then mark all the members that are powers of two with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="b73d0-145">フラグ列挙体を使用するには、数列は (1、2、4、8、16、32、64 のように) 2 の累乗の連続である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b73d0-145">Note that to use a flag enumeration, the progression must be an uninterrupted sequence of powers of 2 (for example, 1, 2, 4, 8, 16, 32, 64).</span></span>  
  
 <span data-ttu-id="b73d0-146">フラグの列挙値を送信する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-146">The following steps apply to sending a flag's enumeration value:</span></span>  
  
1.  <span data-ttu-id="b73d0-147">数値にマップする列挙メンバー (<xref:System.Runtime.Serialization.EnumMemberAttribute> 属性が適用されている) の検索を試みます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-147">Attempt to find an enumeration member (with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that maps to the numeric value.</span></span> <span data-ttu-id="b73d0-148">見つかった場合、そのメンバーのみを含むリストを送信します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-148">If found, send a list that contains just that member.</span></span>  
  
2.  <span data-ttu-id="b73d0-149">合計の各部にマップされる列挙メンバー (それぞれに <xref:System.Runtime.Serialization.EnumMemberAttribute> 属性が適用されている) が存在するような形で、数値をこの合計に分割します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-149">Attempt to break the numeric value into a sum such that there are enumeration members (each with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that map to each part of the sum.</span></span> <span data-ttu-id="b73d0-150">このメンバーすべてのリストを送信します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-150">Send the list of all these members.</span></span> <span data-ttu-id="b73d0-151">注意してください、*最長一致アルゴリズム*をこのような合計を検索するために使用し、したがってでも存在する場合は、このような合計が表示される保証はありません。</span><span class="sxs-lookup"><span data-stu-id="b73d0-151">Note that the *greedy algorithm* is used to find such a sum, and thus there is no guarantee that such a sum is found even if it is present.</span></span> <span data-ttu-id="b73d0-152">この問題を回避するには、列挙メンバーの数値を必ず 2 の累乗数にします。</span><span class="sxs-lookup"><span data-stu-id="b73d0-152">To avoid this problem, make sure that the numeric values of the enumeration members are powers of two.</span></span>  
  
3.  <span data-ttu-id="b73d0-153">前の 2 つの手順が失敗し、数値がゼロ以外の場合、<xref:System.Runtime.Serialization.SerializationException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="b73d0-153">If the preceding two steps fail, and the numeric value is nonzero, throw a <xref:System.Runtime.Serialization.SerializationException>.</span></span> <span data-ttu-id="b73d0-154">数値がゼロの場合、空のリストを送信します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-154">If the numeric value is zero, send the empty list.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b73d0-155">例</span><span class="sxs-lookup"><span data-stu-id="b73d0-155">Example</span></span>  
 <span data-ttu-id="b73d0-156">フラグ操作で使用できる列挙の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b73d0-156">The following enumeration example can be used in a flag operation.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 <span data-ttu-id="b73d0-157">次の各値は、示されているようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="b73d0-157">The following example values are serialized as indicated.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b73d0-158">参照</span><span class="sxs-lookup"><span data-stu-id="b73d0-158">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="b73d0-159">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="b73d0-159">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="b73d0-160">サービス コントラクトでのデータ転送の指定</span><span class="sxs-lookup"><span data-stu-id="b73d0-160">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
