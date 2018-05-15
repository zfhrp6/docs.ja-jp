---
title: 定数とリテラルのデータ型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 8d110ec17bcdb03f339d779b2950ba56d77957cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="b7262-102">定数とリテラルのデータ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7262-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="b7262-103">リテラルは、変数の値または数値 3 または文字列「こんにちは」など、式の結果ではなく自体として表される値です。</span><span class="sxs-lookup"><span data-stu-id="b7262-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="b7262-104">定数は、わかりやすい名前を受け取り、リテラルの代わりに値を変更することがあります、変数ではなく、プログラム全体で同じ値を保持します。</span><span class="sxs-lookup"><span data-stu-id="b7262-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="b7262-105">ときに[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)は`Off`と[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)は`On`データ型を持つすべての定数を明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7262-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="b7262-106">データ型を次の例では、`MyByte`データ型として明示的に宣言されて`Byte`:</span><span class="sxs-lookup"><span data-stu-id="b7262-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 <span data-ttu-id="b7262-107">ときに`Option Infer`は`On`または`Option Strict`は`Off`を持つデータ型を指定せずに定数を宣言することができます、`As`句。</span><span class="sxs-lookup"><span data-stu-id="b7262-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="b7262-108">コンパイラでは、定数式の型からの型を決定します。</span><span class="sxs-lookup"><span data-stu-id="b7262-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="b7262-109">既定でに整数リテラルをキャスト、`Integer`データ型。</span><span class="sxs-lookup"><span data-stu-id="b7262-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="b7262-110">既定のデータ型は、浮動小数点数の`Double`、およびキーワード`True`と`False`指定、`Boolean`定数。</span><span class="sxs-lookup"><span data-stu-id="b7262-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="b7262-111">リテラルおよび強制型変換</span><span class="sxs-lookup"><span data-stu-id="b7262-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="b7262-112">場合によってを特定のデータ型にリテラルを適用する場合があります。たとえば、型の変数に特に大きな整数リテラル値を割り当てる際`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="b7262-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="b7262-113">次の例では、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="b7262-113">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="b7262-114">リテラルの表現から、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b7262-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="b7262-115">`Decimal`データ型値を保持できるこの大きさがリテラルは暗黙的に表されてとして、 `Long`、することはできません。</span><span class="sxs-lookup"><span data-stu-id="b7262-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="b7262-116">2 つの方法で特定のデータ型をリテラルを強制することができます: に、型文字を追加することによって、または文字を囲む内に配置することによってです。</span><span class="sxs-lookup"><span data-stu-id="b7262-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="b7262-117">型文字または文字を囲む必要がありますすぐに前やなし、介在する領域または任意の種類の文字、リテラルに従います。</span><span class="sxs-lookup"><span data-stu-id="b7262-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="b7262-118">前の例を実行するために、追加することができます、`D`文字入力すると、リテラルとして表現されていること、 `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="b7262-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 <span data-ttu-id="b7262-119">次の例では、型文字と囲み文字の正しい使用法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b7262-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 <span data-ttu-id="b7262-120">次の表は、それを囲む文字と Visual Basic で使用可能な型宣言文字。</span><span class="sxs-lookup"><span data-stu-id="b7262-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="b7262-121">データの種類</span><span class="sxs-lookup"><span data-stu-id="b7262-121">Data type</span></span>|<span data-ttu-id="b7262-122">囲み文字</span><span class="sxs-lookup"><span data-stu-id="b7262-122">Enclosing character</span></span>|<span data-ttu-id="b7262-123">末尾の型文字</span><span class="sxs-lookup"><span data-stu-id="b7262-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="b7262-124">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-124">(none)</span></span>|<span data-ttu-id="b7262-125">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="b7262-126">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-126">(none)</span></span>|<span data-ttu-id="b7262-127">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="b7262-128">"</span><span class="sxs-lookup"><span data-stu-id="b7262-128">"</span></span>|<span data-ttu-id="b7262-129">C</span><span class="sxs-lookup"><span data-stu-id="b7262-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="b7262-130">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="b7262-131">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-131">(none)</span></span>|<span data-ttu-id="b7262-132">D または @</span><span class="sxs-lookup"><span data-stu-id="b7262-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="b7262-133">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-133">(none)</span></span>|<span data-ttu-id="b7262-134">R または #</span><span class="sxs-lookup"><span data-stu-id="b7262-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="b7262-135">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-135">(none)</span></span>|<span data-ttu-id="b7262-136">$I または %</span><span class="sxs-lookup"><span data-stu-id="b7262-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="b7262-137">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-137">(none)</span></span>|<span data-ttu-id="b7262-138">L または (& a)</span><span class="sxs-lookup"><span data-stu-id="b7262-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="b7262-139">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-139">(none)</span></span>|<span data-ttu-id="b7262-140">S</span><span class="sxs-lookup"><span data-stu-id="b7262-140">S</span></span>|  
|`Single`|<span data-ttu-id="b7262-141">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-141">(none)</span></span>|<span data-ttu-id="b7262-142">F または!</span><span class="sxs-lookup"><span data-stu-id="b7262-142">F or !</span></span>|  
|`String`|<span data-ttu-id="b7262-143">"</span><span class="sxs-lookup"><span data-stu-id="b7262-143">"</span></span>|<span data-ttu-id="b7262-144">(なし)</span><span class="sxs-lookup"><span data-stu-id="b7262-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7262-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7262-145">See Also</span></span>  
 [<span data-ttu-id="b7262-146">ユーザー定義定数</span><span class="sxs-lookup"><span data-stu-id="b7262-146">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [<span data-ttu-id="b7262-147">方法 : 定数を宣言する</span><span class="sxs-lookup"><span data-stu-id="b7262-147">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [<span data-ttu-id="b7262-148">定数の概要</span><span class="sxs-lookup"><span data-stu-id="b7262-148">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="b7262-149">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7262-149">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="b7262-150">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7262-150">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="b7262-151">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="b7262-151">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="b7262-152">方法: 列挙型を宣言</span><span class="sxs-lookup"><span data-stu-id="b7262-152">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="b7262-153">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="b7262-153">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="b7262-154">データの種類</span><span class="sxs-lookup"><span data-stu-id="b7262-154">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="b7262-155">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="b7262-155">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
