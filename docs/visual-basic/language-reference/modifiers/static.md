---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2cbd99a026a5ebf0e215ee5732d62ccf639d3836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602055"
---
# <a name="static-visual-basic"></a><span data-ttu-id="6080d-102">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6080d-102">Static (Visual Basic)</span></span>
<span data-ttu-id="6080d-103">1 つまたは複数の宣言されたローカル変数を引き続き存在し、宣言されているプロシージャの終了後、最新の値を保持するように指定します。</span><span class="sxs-lookup"><span data-stu-id="6080d-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6080d-104">コメント</span><span class="sxs-lookup"><span data-stu-id="6080d-104">Remarks</span></span>  
 <span data-ttu-id="6080d-105">通常、プロシージャ内のローカル変数は、プロシージャは停止すると、すぐに存在しなくなります。</span><span class="sxs-lookup"><span data-stu-id="6080d-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="6080d-106">静的変数存在し、続け、最新の値を保持します。</span><span class="sxs-lookup"><span data-stu-id="6080d-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="6080d-107">コード、プロシージャを呼び出します。 次には、変数が再初期化されていないに割り当てられている最新の値をそのまま保持します。</span><span class="sxs-lookup"><span data-stu-id="6080d-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="6080d-108">静的変数で定義されているクラスまたはモジュールの有効期間中に存在し続けます。</span><span class="sxs-lookup"><span data-stu-id="6080d-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6080d-109">ルール</span><span class="sxs-lookup"><span data-stu-id="6080d-109">Rules</span></span>  
  
-   <span data-ttu-id="6080d-110">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="6080d-110">**Declaration Context.**</span></span> <span data-ttu-id="6080d-111">使用することができます`Static`ローカル変数に対してのみです。</span><span class="sxs-lookup"><span data-stu-id="6080d-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="6080d-112">つまりの宣言コンテキスト、`Static`変数は、プロシージャまたはプロシージャでは、ブロックに指定する必要があり、ソース ファイル、名前空間、クラス、構造体、またはモジュールにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6080d-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="6080d-113">使用することはできません`Static`プロシージャの内部で構造体。</span><span class="sxs-lookup"><span data-stu-id="6080d-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="6080d-114">データ型`Static`ローカル変数を推論することはできません。</span><span class="sxs-lookup"><span data-stu-id="6080d-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="6080d-115">詳細については、次を参照してください。[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。</span><span class="sxs-lookup"><span data-stu-id="6080d-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="6080d-116">**結合された修飾子。**</span><span class="sxs-lookup"><span data-stu-id="6080d-116">**Combined Modifiers.**</span></span> <span data-ttu-id="6080d-117">指定することはできません`Static`と共に`ReadOnly`、 `Shadows`、または`Shared`同じ宣言内で。</span><span class="sxs-lookup"><span data-stu-id="6080d-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6080d-118">動作</span><span class="sxs-lookup"><span data-stu-id="6080d-118">Behavior</span></span>  
 <span data-ttu-id="6080d-119">静的変数を宣言する場合、`Shared`プロシージャ、静的変数の 1 つだけのコピーは、アプリケーション全体の使用。</span><span class="sxs-lookup"><span data-stu-id="6080d-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="6080d-120">呼び出す、`Shared`クラスを使用してプロシージャ名、変数、クラスのインスタンスを指すではなくです。</span><span class="sxs-lookup"><span data-stu-id="6080d-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="6080d-121">ないプロシージャ内で静的変数を宣言する場合`Shared`変数の 1 つのコピーはクラスの各インスタンスの使用のみ。</span><span class="sxs-lookup"><span data-stu-id="6080d-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="6080d-122">クラスの特定のインスタンスが指す変数を使用して、非共有プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6080d-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6080d-123">例</span><span class="sxs-lookup"><span data-stu-id="6080d-123">Example</span></span>  
 <span data-ttu-id="6080d-124">次の例は、`Static` の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="6080d-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 <span data-ttu-id="6080d-125">`Static`変数`totalSales`1 つだけの時間は 0 に初期化します。</span><span class="sxs-lookup"><span data-stu-id="6080d-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="6080d-126">入力するたびに`updateSales`、`totalSales`まだを計算した最新の値。</span><span class="sxs-lookup"><span data-stu-id="6080d-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="6080d-127">`Static`修飾子は、このコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="6080d-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="6080d-128">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="6080d-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6080d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="6080d-129">See Also</span></span>  
 [<span data-ttu-id="6080d-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="6080d-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="6080d-131">Shared</span><span class="sxs-lookup"><span data-stu-id="6080d-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="6080d-132">Visual Basic における有効期間</span><span class="sxs-lookup"><span data-stu-id="6080d-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="6080d-133">変数宣言</span><span class="sxs-lookup"><span data-stu-id="6080d-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="6080d-134">構造体</span><span class="sxs-lookup"><span data-stu-id="6080d-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="6080d-135">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="6080d-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="6080d-136">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="6080d-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
