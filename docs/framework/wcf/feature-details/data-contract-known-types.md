---
title: "既知のデータ コントラクト型"
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
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24d26358c0bf0440b2fbba143629a0e4bda21cec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="data-contract-known-types"></a><span data-ttu-id="37630-102">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="37630-102">Data Contract Known Types</span></span>
<span data-ttu-id="37630-103"><xref:System.Runtime.Serialization.KnownTypeAttribute> クラスを使用すると、逆シリアル化において考慮する必要のある型を事前に指定できます。</span><span class="sxs-lookup"><span data-stu-id="37630-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="37630-104">実施例については、「 [Known Types](../../../../docs/framework/wcf/samples/known-types.md) 」の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37630-104">For a working example, see the [Known Types](../../../../docs/framework/wcf/samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="37630-105">通常は、クライアントとサービス間でパラメーターを渡したり、値を返したりするときに、転送するデータのデータ コントラクトのすべてが両方のエンドポイントで共有されます。</span><span class="sxs-lookup"><span data-stu-id="37630-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="37630-106">ただし、次の場合はこれが該当しません。</span><span class="sxs-lookup"><span data-stu-id="37630-106">However, this is not the case in the following circumstances:</span></span>  
  
-   <span data-ttu-id="37630-107">送信データ コントラクトが、予想データ コントラクトから派生する場合。</span><span class="sxs-lookup"><span data-stu-id="37630-107">The sent data contract is derived from the expected data contract.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="37630-108">継承に関するセクション[データ コントラクトの等価性](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md))。</span><span class="sxs-lookup"><span data-stu-id="37630-108"> the section about inheritance in [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span></span> <span data-ttu-id="37630-109">この場合、送信されるデータには、受信エンドポイントで予想しているデータ コントラクトが含まれません。</span><span class="sxs-lookup"><span data-stu-id="37630-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
-   <span data-ttu-id="37630-110">クラス、構造体、または列挙とは対照的に、送信される情報の宣言型がインターフェイスである場合。</span><span class="sxs-lookup"><span data-stu-id="37630-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="37630-111">したがって、インターフェイスを実装するどの型が実際に送信されるかを事前に知ることができないため、受信エンドポイントでは送信されるデータのデータ コントラクトを事前に確認することができません。</span><span class="sxs-lookup"><span data-stu-id="37630-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
-   <span data-ttu-id="37630-112">送信される情報の宣言型が <xref:System.Object>である場合。</span><span class="sxs-lookup"><span data-stu-id="37630-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="37630-113">すべての型が <xref:System.Object>から継承され、どの型が実際に送信されるかを事前に知ることができないため、受信エンドポイントでは送信されるデータのデータ コントラクトを事前に確認することができません。</span><span class="sxs-lookup"><span data-stu-id="37630-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="37630-114">これは最初の項目についての特殊なケースです。すべてのデータ コントラクトは既定で、 <xref:System.Object>に対して生成された空のデータ コントラクトから派生します。</span><span class="sxs-lookup"><span data-stu-id="37630-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="37630-115">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型を含む一部の型に、前述した 3 つのカテゴリの 1 つに分類されるメンバーが含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="37630-115">Some types, which include [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="37630-116">たとえば、 <xref:System.Collections.Hashtable> は <xref:System.Object> を使用して、ハッシュ テーブルに実際のオブジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="37630-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="37630-117">これらの型をシリアル化する場合、受信側ではこれらのメンバーのデータ コントラクトを事前に確認することができません。</span><span class="sxs-lookup"><span data-stu-id="37630-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="37630-118">KnownTypeAttribute クラス</span><span class="sxs-lookup"><span data-stu-id="37630-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="37630-119">データが受信エンドポイントに到着すると、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ランタイムはデータを共通言語ランタイム (CLR: Common Language Runtime) 型のインスタンスに逆シリアル化しようとします。</span><span class="sxs-lookup"><span data-stu-id="37630-119">When data arrives at a receiving endpoint, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="37630-120">逆シリアル化するためにインスタンス化される型は、まず受信メッセージを調べてメッセージの内容が従うデータ コントラクトを特定することで選択されます。</span><span class="sxs-lookup"><span data-stu-id="37630-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="37630-121">次に逆シリアル化エンジンは、メッセージの内容と互換性のあるデータ コントラクトを実装する CLR 型を探します。</span><span class="sxs-lookup"><span data-stu-id="37630-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="37630-122">逆シリアル化エンジンによってこの処理中に逆シリアル化の候補の型として許可される一連の型は、逆シリアル化の "既知の型" のセットと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="37630-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="37630-123">逆シリアル化エンジンに型の情報を知らせる方法として、 <xref:System.Runtime.Serialization.KnownTypeAttribute>を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="37630-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="37630-124">この属性は、データ コントラクト型全体に適用できるだけで、個々のデータ メンバーには適用できません。</span><span class="sxs-lookup"><span data-stu-id="37630-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="37630-125">この属性は、クラスまたは構造体にすることが可能な *外部型* に適用されます。</span><span class="sxs-lookup"><span data-stu-id="37630-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="37630-126">最も簡単な使用方法は、属性を適用するときに "既知の型" として型を指定することです。</span><span class="sxs-lookup"><span data-stu-id="37630-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="37630-127">これによって、外部型のオブジェクトまたはメンバーを通して参照される任意のオブジェクトが逆シリアル化されるときに、必ず、その既知の型が既知の型のセットに追加されます。</span><span class="sxs-lookup"><span data-stu-id="37630-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="37630-128">複数の <xref:System.Runtime.Serialization.KnownTypeAttribute> 属性を同じ型に適用することができます。</span><span class="sxs-lookup"><span data-stu-id="37630-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="37630-129">既知の型とプリミティブ</span><span class="sxs-lookup"><span data-stu-id="37630-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="37630-130">プリミティブとして扱われる特定の型 ( <xref:System.DateTime> 、 <xref:System.Xml.XmlElement>など) と同様に、プリミティブ型は、常に "既知" であり、このメカニズムを通して追加する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="37630-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="37630-131">ただし、プリミティブ型の配列は明示的に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37630-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="37630-132">ほとんどのコレクションは、配列と同等に扱われます。</span><span class="sxs-lookup"><span data-stu-id="37630-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="37630-133">(非ジェネリック コレクションは、 <xref:System.Object>の配列と同等に扱われます)。</span><span class="sxs-lookup"><span data-stu-id="37630-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="37630-134">プリミティブ、プリミティブ配列、およびプリミティブ コレクションの使用例については、例 4 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37630-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37630-135">他のプリミティブ型とは異なり、 <xref:System.DateTimeOffset> 構造は、既定では既知の型ではないため、既知の型のリストに手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37630-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="37630-136">使用例</span><span class="sxs-lookup"><span data-stu-id="37630-136">Examples</span></span>  
 <span data-ttu-id="37630-137"><xref:System.Runtime.Serialization.KnownTypeAttribute> クラスの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="37630-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="37630-138">例 1</span><span class="sxs-lookup"><span data-stu-id="37630-138">Example 1</span></span>  
 <span data-ttu-id="37630-139">継承関係にある 3 つのクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="37630-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="37630-140">次の `CompanyLogo` クラスはシリアル化できますが、 `ShapeOfLogo` メンバーが `CircleType` オブジェクトと `TriangleType` オブジェクトのどちらかに設定されている場合は、逆シリアル化エンジンが "Circle" や "Triangle" という名前のデータ コントラクト型を認識しないため、逆シリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="37630-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="37630-141">`CompanyLogo` 型の正しいコードの記述方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37630-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="37630-142">外部型の `CompanyLogo2` が逆シリアル化されるときは、必ず、逆シリアル化エンジンが `CircleType` と `TriangleType` を認識するため、"Circle" データ コントラクトおよび "Triangle" データ コントラクトと一致する型を検出できます。</span><span class="sxs-lookup"><span data-stu-id="37630-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="37630-143">例 2</span><span class="sxs-lookup"><span data-stu-id="37630-143">Example 2</span></span>  
 <span data-ttu-id="37630-144">次の例では、 `CustomerTypeA` と `CustomerTypeB` の両方が `Customer` データ コントラクトを持っている場合でも、逆シリアル化エンジンは `CustomerTypeB` だけを認識するため、 `PurchaseOrder` が逆シリアル化されるときは必ず `CustomerTypeB` のインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="37630-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="37630-145">例 3</span><span class="sxs-lookup"><span data-stu-id="37630-145">Example 3</span></span>  
 <span data-ttu-id="37630-146">次の例では、 <xref:System.Collections.Hashtable> が <xref:System.Object>として内部的にその内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="37630-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="37630-147">ハッシュ テーブルを正常に逆シリアル化するには、逆シリアル化エンジンがそのテーブルに現れる可能性のある型のセットを認識している必要があります。</span><span class="sxs-lookup"><span data-stu-id="37630-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="37630-148">この場合は、 `Book` オブジェクトと `Magazine` オブジェクトだけが `Catalog`に保存されているため、この 2 つが <xref:System.Runtime.Serialization.KnownTypeAttribute> 属性を使用して追加されることが事前にわかっています。</span><span class="sxs-lookup"><span data-stu-id="37630-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="37630-149">例 4</span><span class="sxs-lookup"><span data-stu-id="37630-149">Example 4</span></span>  
 <span data-ttu-id="37630-150">次の例では、データ コントラクトには数値と、その数値に基づいて実行する演算が含まれています。</span><span class="sxs-lookup"><span data-stu-id="37630-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="37630-151">`Numbers` データ メンバーは、整数、整数の配列、または整数を含む <xref:System.Collections.Generic.List%601> にすることができます。</span><span class="sxs-lookup"><span data-stu-id="37630-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="37630-152">この例は、WCF プロキシを生成するために SVCUTIL.EXE が使用されている場合にのみ、クライアント側で機能します。</span><span class="sxs-lookup"><span data-stu-id="37630-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="37630-153">SVCUTIL.EXE は、サービスからメタデータ (任意の既知の型を含む) を取得します。</span><span class="sxs-lookup"><span data-stu-id="37630-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="37630-154">この情報がない場合、クライアントは型を逆シリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="37630-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="37630-155">アプリケーション コードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37630-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="37630-156">既知の型、継承、およびインターフェイス</span><span class="sxs-lookup"><span data-stu-id="37630-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="37630-157">`KnownTypeAttribute` 属性を使用して既知の型を特定の型に関連付けると、その既知の型がその特定の型から派生したすべての型に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="37630-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="37630-158">たとえば、次のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37630-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="37630-159">`DoubleDrawing` クラスは、 `KnownTypeAttribute` フィールドで `Square` と `Circle` を使用するために `AdditionalShape` 属性を必要としません。これは、既に基本クラス (`Drawing`) にこれらの属性が適用されているためです。</span><span class="sxs-lookup"><span data-stu-id="37630-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="37630-160">既知の型は、クラスと構造体にのみ関連付けることができます。インターフェイスに関連付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="37630-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="37630-161">オープン ジェネリック メソッドを使用する既知の型</span><span class="sxs-lookup"><span data-stu-id="37630-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="37630-162">既知の型としてジェネリック型の追加が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="37630-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="37630-163">ただし、オープン ジェネリック型をパラメーターとして `KnownTypeAttribute` 属性に渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="37630-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="37630-164">この問題は、型の一覧を返すメソッドを作成して既知の型のコレクションに追加するという代替機構を使用することで解決できます。</span><span class="sxs-lookup"><span data-stu-id="37630-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="37630-165">次に、いくつかの制限事項があるため、このメソッドの名前を `KnownTypeAttribute` 属性への文字列引数として指定します。</span><span class="sxs-lookup"><span data-stu-id="37630-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="37630-166">このメソッドは、 `KnownTypeAttribute` 属性を適用する型上に存在し、静的で、パラメーターを必要とせず、 <xref:System.Collections.IEnumerable> の <xref:System.Type>に代入可能なオブジェクトを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="37630-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="37630-167">同じ型上で、メソッド名を持つ `KnownTypeAttribute` 属性と実際の型を持つ `KnownTypeAttribute` 属性を組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="37630-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="37630-168">また、メソッド名が同じ複数の `KnownTypeAttribute` を同じ型に適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="37630-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="37630-169">次のクラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37630-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="37630-170">`theDrawing` フィールドには、 `ColorDrawing` ジェネリック クラスおよび `BlackAndWhiteDrawing`ジェネリック クラスのインスタンスを格納でき、これらのクラスは両方とも `Drawing`ジェネリック クラスから継承されています。</span><span class="sxs-lookup"><span data-stu-id="37630-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="37630-171">通常、両クラスとも既知の型に追加する必要がありますが、次の属性の構文は無効です。</span><span class="sxs-lookup"><span data-stu-id="37630-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 <span data-ttu-id="37630-172">したがって、これらの型を返すメソッドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37630-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="37630-173">この型の正しいコードの記述方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37630-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="37630-174">既知の型を追加するその他の方法</span><span class="sxs-lookup"><span data-stu-id="37630-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="37630-175">また、既知の型は、構成ファイルを使用して追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="37630-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="37630-176">この方法は、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]でサードパーティ製の型ライブラリを使用する場合のように、既知の型の逆シリアル化が制御できない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="37630-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
 <span data-ttu-id="37630-177">構成ファイルで既知の型を指定する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="37630-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 <span data-ttu-id="37630-178">前の構成ファイルでは、 `MyCompany.Library.Shape` というコントラクト型が `MyCompany.Library.Circle` を既知の型として持つと宣言されています。</span><span class="sxs-lookup"><span data-stu-id="37630-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37630-179">参照</span><span class="sxs-lookup"><span data-stu-id="37630-179">See Also</span></span>  
 <xref:System.Runtime.Serialization.KnownTypeAttribute>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Object>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>  
 [<span data-ttu-id="37630-180">既知の型</span><span class="sxs-lookup"><span data-stu-id="37630-180">Known Types</span></span>](../../../../docs/framework/wcf/samples/known-types.md)  
 [<span data-ttu-id="37630-181">データ コントラクトの等価性</span><span class="sxs-lookup"><span data-stu-id="37630-181">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [<span data-ttu-id="37630-182">サービス コントラクトの設計</span><span class="sxs-lookup"><span data-stu-id="37630-182">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
