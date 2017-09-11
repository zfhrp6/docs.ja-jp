---
title: "複合データ型 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types
- composite data types
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures, composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5f0c6215ce45d724a7b5c8c4f8e34ea27bce8fe4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="bb87a-102">複合データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb87a-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="bb87a-103">基本データ型だけでなく[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]物資を作成するさまざまな種類の項目も組み合わせてできます*複合データ型*構造体、配列、およびクラスなどです。</span><span class="sxs-lookup"><span data-stu-id="bb87a-103">In addition to the elementary data types [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="bb87a-104">基本型およびその他の複合型、複合データ型を構築できます。</span><span class="sxs-lookup"><span data-stu-id="bb87a-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="bb87a-105">たとえば、配列メンバーを持つ、構造体または構造体の要素の配列を定義できます。</span><span class="sxs-lookup"><span data-stu-id="bb87a-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="bb87a-106">データ型</span><span class="sxs-lookup"><span data-stu-id="bb87a-106">Data Types</span></span>  
 <span data-ttu-id="bb87a-107">複合型は、そのコンポーネントのいずれかのデータ型と異なります。</span><span class="sxs-lookup"><span data-stu-id="bb87a-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="bb87a-108">たとえば、配列の`Integer`の要素ではありません、`Integer`データ型。</span><span class="sxs-lookup"><span data-stu-id="bb87a-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="bb87a-109">配列のデータ型は、通常、必要に応じて、要素の型、かっこ、およびコンマを使用して表されます。</span><span class="sxs-lookup"><span data-stu-id="bb87a-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="bb87a-110">1 次元の配列など`String`として表される要素`String()`と、2 次元の配列`Boolean`として表される要素`Boolean(,)`します。</span><span class="sxs-lookup"><span data-stu-id="bb87a-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="bb87a-111">構造体の型</span><span class="sxs-lookup"><span data-stu-id="bb87a-111">Structure Types</span></span>  
 <span data-ttu-id="bb87a-112">すべての構造を包括する&1; つのデータ型はありません。</span><span class="sxs-lookup"><span data-stu-id="bb87a-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="bb87a-113">代わりに、2 つの構造が同じ順序で同一要素を定義する場合でも、構造体の各定義は、固有のデータ型を表します。</span><span class="sxs-lookup"><span data-stu-id="bb87a-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="bb87a-114">ただし、同じ構造の&2; つ以上のインスタンスを作成する場合[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]はそれらを同じデータ型と見なします。</span><span class="sxs-lookup"><span data-stu-id="bb87a-114">However, if you create two or more instances of the same structure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considers them to be of the same data type.</span></span>  
  
## <a name="array-types"></a><span data-ttu-id="bb87a-115">配列型</span><span class="sxs-lookup"><span data-stu-id="bb87a-115">Array Types</span></span>  
 <span data-ttu-id="bb87a-116">すべての配列を包括する&1; つのデータ型はありません。</span><span class="sxs-lookup"><span data-stu-id="bb87a-116">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="bb87a-117">配列の特定のインスタンスのデータ型は、次のように決定されます。</span><span class="sxs-lookup"><span data-stu-id="bb87a-117">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="bb87a-118">配列であること</span><span class="sxs-lookup"><span data-stu-id="bb87a-118">The fact of being an array</span></span>  
  
-   <span data-ttu-id="bb87a-119">配列のランク (次元数)</span><span class="sxs-lookup"><span data-stu-id="bb87a-119">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="bb87a-120">配列の要素の型</span><span class="sxs-lookup"><span data-stu-id="bb87a-120">The element type of the array</span></span>  
  
 <span data-ttu-id="bb87a-121">特に、次元の長さは、インスタンスのデータ型の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="bb87a-121">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="bb87a-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="bb87a-122">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="bb87a-123">上記の例では、配列変数`arrayA`と`arrayB`、同じデータ型と見なされます: `Byte()` — 場合でも、異なる長さに初期化されます。</span><span class="sxs-lookup"><span data-stu-id="bb87a-123">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="bb87a-124">変数`arrayB`と`arrayC`は、同じ型のない、要素型が異なるためです。</span><span class="sxs-lookup"><span data-stu-id="bb87a-124">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="bb87a-125">変数`arrayC`と`arrayD`は、同じ型のない、ランクが異なるためです。</span><span class="sxs-lookup"><span data-stu-id="bb87a-125">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="bb87a-126">変数`arrayD`と`arrayE`同じ型を持つ — `Short(,)` -ランクと要素の型が同じなので、たとえ`arrayD`がまだ初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="bb87a-126">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="bb87a-127">配列の詳細については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="bb87a-127">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="bb87a-128">クラスの種類</span><span class="sxs-lookup"><span data-stu-id="bb87a-128">Class Types</span></span>  
 <span data-ttu-id="bb87a-129">すべてのクラスを包括する&1; つのデータ型はありません。</span><span class="sxs-lookup"><span data-stu-id="bb87a-129">There is no single data type comprising all classes.</span></span> <span data-ttu-id="bb87a-130">1 つのクラスが別のクラスから継承できる各は個別のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="bb87a-130">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="bb87a-131">同じクラスの複数のインスタンスでは、同じデータ型です。</span><span class="sxs-lookup"><span data-stu-id="bb87a-131">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="bb87a-132">クラスのインスタンスの&1; つの変数を割り当てるには別に、同じデータ型を持つ操作を行いますだけでなく、メモリ内の同じクラス インスタンスを指すようにします。</span><span class="sxs-lookup"><span data-stu-id="bb87a-132">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="bb87a-133">クラスの詳細については、次を参照してください。[オブジェクトおよびクラス](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="bb87a-133">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb87a-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb87a-134">See Also</span></span>  
 <span data-ttu-id="bb87a-135">[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="bb87a-135">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="bb87a-136"> [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="bb87a-136"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="bb87a-137"> [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="bb87a-137"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="bb87a-138"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="bb87a-138"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="bb87a-139"> [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="bb87a-139"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="bb87a-140"> [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="bb87a-140"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="bb87a-141"> [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="bb87a-141"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="bb87a-142"> [方法 : 変数内で複数の値を保持する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)</span><span class="sxs-lookup"><span data-stu-id="bb87a-142"> [How to: Hold More Than One Value in a Variable](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)</span></span>
