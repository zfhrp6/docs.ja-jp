---
title: Key (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20dbe4e67fb3e415ba0202555ace7fd5afed68d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="key-visual-basic"></a><span data-ttu-id="45fce-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45fce-102">Key (Visual Basic)</span></span>
<span data-ttu-id="45fce-103">`Key`キーワードでは、匿名型のプロパティの動作を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="45fce-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="45fce-104">匿名型のインスタンス、またはハッシュ コード値の計算の間の等値に関するテストでキー プロパティとしてを指定したプロパティのみです。</span><span class="sxs-lookup"><span data-stu-id="45fce-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="45fce-105">キー プロパティの値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="45fce-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="45fce-106">キー プロパティとして、キーワードを配置することで、匿名型のプロパティを指定する`Key`初期化リストでその宣言の前にします。</span><span class="sxs-lookup"><span data-stu-id="45fce-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="45fce-107">次の例では、`Airline`と`FlightNo`キーのプロパティが`Gate`はありません。</span><span class="sxs-lookup"><span data-stu-id="45fce-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 <span data-ttu-id="45fce-108">新しい匿名型を作成すると、する場合から直接継承<xref:System.Object>です。</span><span class="sxs-lookup"><span data-stu-id="45fce-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="45fce-109">コンパイラは、次の 3 つの継承されたメンバーをオーバーライドします。 <xref:System.Object.Equals%2A>、 <xref:System.Object.GetHashCode%2A>、および<xref:System.Object.ToString%2A>です。</span><span class="sxs-lookup"><span data-stu-id="45fce-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="45fce-110">オーバーライド コードの生成される<xref:System.Object.Equals%2A>と<xref:System.Object.GetHashCode%2A>キー プロパティに基づきます。</span><span class="sxs-lookup"><span data-stu-id="45fce-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="45fce-111">型のキー プロパティがない場合<xref:System.Object.GetHashCode%2A>と<xref:System.Object.Equals%2A>はオーバーライドされません。</span><span class="sxs-lookup"><span data-stu-id="45fce-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="45fce-112">等価比較</span><span class="sxs-lookup"><span data-stu-id="45fce-112">Equality</span></span>  
 <span data-ttu-id="45fce-113">同じ型のインスタンスと、主要なプロパティの値が等しい場合、匿名型の 2 つのインスタンスが等しい。</span><span class="sxs-lookup"><span data-stu-id="45fce-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="45fce-114">次の例についてで`flight2`と等しい`flight1`前の例から、同じ匿名のインスタンスがいるため、型と、一致している、キー プロパティの値。</span><span class="sxs-lookup"><span data-stu-id="45fce-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="45fce-115">ただし、`flight3`は等しくありません`flight1`キーのプロパティの値が異なるため`FlightNo`です。</span><span class="sxs-lookup"><span data-stu-id="45fce-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="45fce-116">インスタンス`flight4`と同じ型ではない`flight1`キー プロパティとしてさまざまなプロパティを指定するためです。</span><span class="sxs-lookup"><span data-stu-id="45fce-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 <span data-ttu-id="45fce-117">プロパティを持つのみ非キー、名前、種類、順序、および値で、同じ 2 つのインスタンスが宣言されている場合は 2 つのインスタンスが等しくありません。</span><span class="sxs-lookup"><span data-stu-id="45fce-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="45fce-118">キー プロパティを指定せず、インスタンス自体にのみ等価です。</span><span class="sxs-lookup"><span data-stu-id="45fce-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="45fce-119">匿名型の 2 つのインスタンスを同じ匿名型のインスタンスである条件の詳細については、次を参照してください。[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="45fce-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="45fce-120">ハッシュ コードの計算</span><span class="sxs-lookup"><span data-stu-id="45fce-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="45fce-121">同様に<xref:System.Object.Equals%2A>、ハッシュ関数で定義されている<xref:System.Object.GetHashCode%2A>匿名型は、型のキー プロパティに基づく。</span><span class="sxs-lookup"><span data-stu-id="45fce-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="45fce-122">次の例は、コードの値にハッシュ キーのプロパティ間の相互作用を示します。</span><span class="sxs-lookup"><span data-stu-id="45fce-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="45fce-123">すべてのキー プロパティに対して同じ値を持つ匿名型のインスタンスでは、非キー プロパティに一致する値があるない場合でも、同じハッシュ コード値があります。</span><span class="sxs-lookup"><span data-stu-id="45fce-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="45fce-124">次のステートメントから`True`です。</span><span class="sxs-lookup"><span data-stu-id="45fce-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 <span data-ttu-id="45fce-125">1 つまたは複数のキー プロパティに別の値を持つ匿名型のインスタンスでは、別のハッシュ コード値があります。</span><span class="sxs-lookup"><span data-stu-id="45fce-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="45fce-126">次のステートメントから`False`です。</span><span class="sxs-lookup"><span data-stu-id="45fce-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 <span data-ttu-id="45fce-127">キー プロパティとしてさまざまなプロパティを指定する匿名型のインスタンスは、同じ型のインスタンスではありません。</span><span class="sxs-lookup"><span data-stu-id="45fce-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="45fce-128">名前とすべてのプロパティの値が同じ場合でも、別のハッシュ コード値があります。</span><span class="sxs-lookup"><span data-stu-id="45fce-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="45fce-129">次のステートメントから`False`です。</span><span class="sxs-lookup"><span data-stu-id="45fce-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a><span data-ttu-id="45fce-130">読み取り専用の値</span><span class="sxs-lookup"><span data-stu-id="45fce-130">Read-Only Values</span></span>  
 <span data-ttu-id="45fce-131">キー プロパティの値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="45fce-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="45fce-132">たとえば、`flight1`前の例で、`Airline`と`FlightNo`フィールドは読み取り専用が`Gate`変更できます。</span><span class="sxs-lookup"><span data-stu-id="45fce-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="45fce-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="45fce-133">See Also</span></span>  
 [<span data-ttu-id="45fce-134">匿名型の定義</span><span class="sxs-lookup"><span data-stu-id="45fce-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [<span data-ttu-id="45fce-135">方法 : 匿名型の宣言におけるプロパティ名と型を推論する</span><span class="sxs-lookup"><span data-stu-id="45fce-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [<span data-ttu-id="45fce-136">匿名型</span><span class="sxs-lookup"><span data-stu-id="45fce-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
