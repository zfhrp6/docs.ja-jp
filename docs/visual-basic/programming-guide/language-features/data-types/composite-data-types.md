---
title: 複合データ型 (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 73867a5881db7c94d258e8716c4ff4c5b1119e71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="ae894-102">複合データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae894-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="ae894-103">Visual Basic に用意されている基本データ型だけでなく、作成するさまざまな種類の項目を作成することができますも*複合データ型*構造体、配列、およびクラスなどです。</span><span class="sxs-lookup"><span data-stu-id="ae894-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="ae894-104">その他の複合型および基本型からは、複合データ型を構築できます。</span><span class="sxs-lookup"><span data-stu-id="ae894-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="ae894-105">たとえば、配列メンバーを持つ構造体の要素の配列または構造体を定義できます。</span><span class="sxs-lookup"><span data-stu-id="ae894-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="ae894-106">データの種類</span><span class="sxs-lookup"><span data-stu-id="ae894-106">Data Types</span></span>  
 <span data-ttu-id="ae894-107">複合型は、そのコンポーネントのいずれかのデータ型と異なるです。</span><span class="sxs-lookup"><span data-stu-id="ae894-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="ae894-108">たとえば、配列の`Integer`の要素ではありません、`Integer`データ型。</span><span class="sxs-lookup"><span data-stu-id="ae894-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="ae894-109">配列のデータ型は、通常、必要に応じて、要素の型、丸かっこ、コンマを使用して表されます。</span><span class="sxs-lookup"><span data-stu-id="ae894-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="ae894-110">たとえば、1 次元配列`String`として表される要素`String()`と、2 次元の配列`Boolean`として表される要素`Boolean(,)`です。</span><span class="sxs-lookup"><span data-stu-id="ae894-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="ae894-111">構造体の型</span><span class="sxs-lookup"><span data-stu-id="ae894-111">Structure Types</span></span>  
 <span data-ttu-id="ae894-112">すべての構造を包括する 1 つのデータ型はありません。</span><span class="sxs-lookup"><span data-stu-id="ae894-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="ae894-113">代わりに、2 つの構造が同じ順序で同一要素を定義する場合でも、構造体の各定義は、固有のデータ型を表します。</span><span class="sxs-lookup"><span data-stu-id="ae894-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="ae894-114">ただし、同じ構造の 2 つ以上のインスタンスを作成する場合は、Visual Basic は、同じデータ型のそれらと見なします。</span><span class="sxs-lookup"><span data-stu-id="ae894-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="ae894-115">タプル</span><span class="sxs-lookup"><span data-stu-id="ae894-115">Tuples</span></span>

<span data-ttu-id="ae894-116">組は、定義済みの型を持つ 2 つ以上のフィールドが含まれる軽量な構造です。</span><span class="sxs-lookup"><span data-stu-id="ae894-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="ae894-117">組は、以降 2017 年 Visual Basic でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ae894-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="ae894-118">組は、参照渡しの引数を渡さずにまたはより多量のクラスまたは構造体で返されるフィールドをパッケージ化せず、1 つのメソッドの呼び出しから複数の値を返す最もよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="ae894-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="ae894-119">参照してください、[組](tuples.md)組の詳細については、トピックです。</span><span class="sxs-lookup"><span data-stu-id="ae894-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="ae894-120">配列型</span><span class="sxs-lookup"><span data-stu-id="ae894-120">Array Types</span></span>  
 <span data-ttu-id="ae894-121">すべての配列を包括する 1 つのデータ型はありません。</span><span class="sxs-lookup"><span data-stu-id="ae894-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="ae894-122">配列の特定のインスタンスのデータ型は、次のように決定されます。</span><span class="sxs-lookup"><span data-stu-id="ae894-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="ae894-123">配列であること</span><span class="sxs-lookup"><span data-stu-id="ae894-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="ae894-124">配列のランク (次元数)</span><span class="sxs-lookup"><span data-stu-id="ae894-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="ae894-125">配列の要素の型</span><span class="sxs-lookup"><span data-stu-id="ae894-125">The element type of the array</span></span>  
  
 <span data-ttu-id="ae894-126">特に、指定した次元の長さは、インスタンスのデータ型の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="ae894-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="ae894-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ae894-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="ae894-128">上記の例では、配列変数`arrayA`と`arrayB`は、同じデータ型であると見なされます: `Byte()` — 場合でも、異なる長さに初期化されます。</span><span class="sxs-lookup"><span data-stu-id="ae894-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="ae894-129">変数`arrayB`と`arrayC`同じ種類が、要素型が異なるためです。</span><span class="sxs-lookup"><span data-stu-id="ae894-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="ae894-130">変数`arrayC`と`arrayD`ランクが異なるために、同じ型のされていません。</span><span class="sxs-lookup"><span data-stu-id="ae894-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="ae894-131">変数`arrayD`と`arrayE`同じ型を持つ — `Short(,)` — ランクと要素の型が同じなので、たとえ`arrayD`がまだ初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="ae894-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="ae894-132">配列の詳細については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="ae894-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="ae894-133">クラスの種類</span><span class="sxs-lookup"><span data-stu-id="ae894-133">Class Types</span></span>  
 <span data-ttu-id="ae894-134">すべてのクラスを構成する 1 つのデータ型はありません。</span><span class="sxs-lookup"><span data-stu-id="ae894-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="ae894-135">1 つのクラスは、別のクラスから継承できます、それぞれが個別のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="ae894-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="ae894-136">同じクラスの複数のインスタンスでは、同じデータ型です。</span><span class="sxs-lookup"><span data-stu-id="ae894-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="ae894-137">1 つのクラスのインスタンス変数を割り当てるには別に、同じデータ型がだけでなく、メモリ内で同じクラスのインスタンスを指すようにします。</span><span class="sxs-lookup"><span data-stu-id="ae894-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="ae894-138">クラスの詳細については、次を参照してください。[クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="ae894-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae894-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae894-139">See Also</span></span>  
 [<span data-ttu-id="ae894-140">データの種類</span><span class="sxs-lookup"><span data-stu-id="ae894-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="ae894-141">基本データ型</span><span class="sxs-lookup"><span data-stu-id="ae894-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="ae894-142">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="ae894-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="ae894-143">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="ae894-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="ae894-144">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="ae894-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="ae894-145">構造体</span><span class="sxs-lookup"><span data-stu-id="ae894-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="ae894-146">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="ae894-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="ae894-147">方法 : 変数内で複数の値を保持する</span><span class="sxs-lookup"><span data-stu-id="ae894-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
