---
title: NULL リテラルと型推論 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 74ff2b459488f896c5ea6af4f7d1e045da5a7983
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="a939b-102">NULL リテラルと型推論 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a939b-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="a939b-103">NULL リテラルは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 型システムのすべての型と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="a939b-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="a939b-104">ただし、正しく、推論される null リテラルの型の[!INCLUDE[esql](../../../../../../includes/esql-md.md)]null リテラルを使用できる場所で特定の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a939b-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="a939b-105">型指定された NULL</span><span class="sxs-lookup"><span data-stu-id="a939b-105">Typed Nulls</span></span>  
 <span data-ttu-id="a939b-106">型指定された NULL は任意の場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="a939b-107">型指定された NULL の場合、型が不明であるため、型推論は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a939b-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="a939b-108">たとえば、次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 構成要素を使用すると、Int16 型の NULL を作成できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="a939b-109">型指定されない NULL リテラル</span><span class="sxs-lookup"><span data-stu-id="a939b-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="a939b-110">型指定されない NULL リテラルは、次のようなコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="a939b-111">CAST 式または TREAT 式への引数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="a939b-112">これは、型指定された NULL 式を生成する場合に推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="a939b-112">This is the recommended way to produce a typed null expression.</span></span>  
  
-   <span data-ttu-id="a939b-113">メソッドまたは関数への引数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-113">As an argument to a method or a function.</span></span> <span data-ttu-id="a939b-114">標準のオーバーロード規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a939b-114">Standard overload rules apply.</span></span>  
  
-   <span data-ttu-id="a939b-115">+、-、/ などの算術式への引数の 1 つとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="a939b-116">他の引数に NULL リテラルを指定することはできません。指定した場合、型推論ができなくなります。</span><span class="sxs-lookup"><span data-stu-id="a939b-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
-   <span data-ttu-id="a939b-117">論理式 (AND、OR、または NOT) への引数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="a939b-118">引数はすべて Boolean 型であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="a939b-118">All the arguments are known to be of type Boolean.</span></span>  
  
-   <span data-ttu-id="a939b-119">IS NULL 式または IS NOT NULL 式への引数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
-   <span data-ttu-id="a939b-120">LIKE 式への 1 つ以上の引数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="a939b-121">引数はすべて文字列であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="a939b-121">All arguments are expected to be strings.</span></span>  
  
-   <span data-ttu-id="a939b-122">名前付きの型コンストラクターへの 1 つ以上の引数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
-   <span data-ttu-id="a939b-123">マルチセット コンストラクターへの 1 つ以上の引数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="a939b-124">マルチセット コンストラクターに渡す引数のうち、少なくとも 1 つは、NULL リテラルではない式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a939b-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
-   <span data-ttu-id="a939b-125">CASE 式の THEN 式または ELSE 式への 1 つ以上の引数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a939b-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="a939b-126">CASE 式の THEN 式または ELSE 式のうち、少なくとも一方は、NULL リテラルではない式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a939b-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="a939b-127">型指定されない NULL リテラルは、その他のシナリオでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a939b-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="a939b-128">たとえば、行コンストラクターへの引数として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a939b-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a939b-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a939b-129">See Also</span></span>  
 [<span data-ttu-id="a939b-130">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="a939b-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
