---
title: "定数とリテラルのデータ型 (Visual Basic) |Microsoft ドキュメント"
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
- declaring constants, literal data types
- data types [Visual Basic], declaring
- constants, declaring
- explicit declarations
- literals, coercing data type
- declarations, data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
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
ms.openlocfilehash: 29a997ee0dd847e8505d1a5c24cacfdfdb0a42cc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="d2301-102">定数とリテラルのデータ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2301-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="d2301-103">リテラルは、変数の値または数値 3 または文字列「こんにちは」など、式の結果ではなく自体として表現される値です。</span><span class="sxs-lookup"><span data-stu-id="d2301-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="d2301-104">定数とは、リテラルの発生し、値が変化し、変数ではなく、プログラム全体で同じ値を保持するわかりやすい名前。</span><span class="sxs-lookup"><span data-stu-id="d2301-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="d2301-105">[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)は`Off`と[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)は`On`データ型を持つすべての定数を明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2301-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="d2301-106">データ型を次の例で`MyByte`データ型として明示的に宣言されて`Byte`:</span><span class="sxs-lookup"><span data-stu-id="d2301-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 <span data-ttu-id="d2301-107">[!code-vb[VbVbalrConstants&#1;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d2301-107">[!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]</span></span>  
  
 <span data-ttu-id="d2301-108">`Option Infer`は`On`または`Option Strict`は`Off`を持つデータ型を指定せずに定数を宣言することができます、`As`句。</span><span class="sxs-lookup"><span data-stu-id="d2301-108">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="d2301-109">コンパイラでは、式の型の定数の型を決定します。</span><span class="sxs-lookup"><span data-stu-id="d2301-109">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="d2301-110">既定で整数リテラルをキャスト、`Integer`データ型。</span><span class="sxs-lookup"><span data-stu-id="d2301-110">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="d2301-111">浮動小数点数は、の既定のデータ型`Double`、およびキーワード`True`と`False`指定、`Boolean`定数です。</span><span class="sxs-lookup"><span data-stu-id="d2301-111">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="d2301-112">リテラル値、および強制型変換</span><span class="sxs-lookup"><span data-stu-id="d2301-112">Literals and Type Coercion</span></span>  
 <span data-ttu-id="d2301-113">場合によっては、特定のデータ型をリテラルを強制する可能性があります。たとえば、型の変数を特に大きな整数リテラル値を割り当てる場合は`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="d2301-113">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="d2301-114">次の例では、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d2301-114">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="d2301-115">リテラルの形式から、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d2301-115">The error results from the representation of the literal.</span></span> <span data-ttu-id="d2301-116">`Decimal`データ型値を保持できるこの大きさが、リテラルが暗黙的として表される、 `Long`、することはできません。</span><span class="sxs-lookup"><span data-stu-id="d2301-116">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="d2301-117">2 つの方法で特定のデータ型のリテラルを強制することができます。 または文字を囲む内に配置することによって、型の文字を追加することによってです。</span><span class="sxs-lookup"><span data-stu-id="d2301-117">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="d2301-118">型文字または文字を囲む必要がありますすぐの前およびなしに余分な空白、または任意の種類の文字、リテラルに従います。</span><span class="sxs-lookup"><span data-stu-id="d2301-118">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="d2301-119">前の例を実行するために、追加することができます、`D`文字入力すると、表現されている場合は、リテラル、 `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="d2301-119">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 <span data-ttu-id="d2301-120">[!code-vb[VbVbalrConstants&#2;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d2301-120">[!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]</span></span>  
  
 <span data-ttu-id="d2301-121">次の例では、型の文字と囲み文字の正しい使用法を示します。</span><span class="sxs-lookup"><span data-stu-id="d2301-121">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 <span data-ttu-id="d2301-122">[!code-vb[VbVbalrConstants&#3;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d2301-122">[!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]</span></span>  
  
 <span data-ttu-id="d2301-123">周囲の文字と型の文字で使用できる次の表は[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d2301-123">The following table shows the enclosing characters and type characters available in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
|<span data-ttu-id="d2301-124">データ型</span><span class="sxs-lookup"><span data-stu-id="d2301-124">Data type</span></span>|<span data-ttu-id="d2301-125">囲み文字</span><span class="sxs-lookup"><span data-stu-id="d2301-125">Enclosing character</span></span>|<span data-ttu-id="d2301-126">末尾の型文字</span><span class="sxs-lookup"><span data-stu-id="d2301-126">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="d2301-127">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-127">(none)</span></span>|<span data-ttu-id="d2301-128">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-128">(none)</span></span>|  
|`Byte`|<span data-ttu-id="d2301-129">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-129">(none)</span></span>|<span data-ttu-id="d2301-130">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-130">(none)</span></span>|  
|`Char`|<span data-ttu-id="d2301-131">"</span><span class="sxs-lookup"><span data-stu-id="d2301-131">"</span></span>|<span data-ttu-id="d2301-132">C</span><span class="sxs-lookup"><span data-stu-id="d2301-132">C</span></span>|  
|`Date`|#|<span data-ttu-id="d2301-133">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-133">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="d2301-134">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-134">(none)</span></span>|<span data-ttu-id="d2301-135">D または @</span><span class="sxs-lookup"><span data-stu-id="d2301-135">D or @</span></span>|  
|`Double`|<span data-ttu-id="d2301-136">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-136">(none)</span></span>|<span data-ttu-id="d2301-137">R または</span><span class="sxs-lookup"><span data-stu-id="d2301-137">R or</span></span> #|  
|`Integer`|<span data-ttu-id="d2301-138">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-138">(none)</span></span>|<span data-ttu-id="d2301-139">I または %</span><span class="sxs-lookup"><span data-stu-id="d2301-139">I or %</span></span>|  
|`Long`|<span data-ttu-id="d2301-140">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-140">(none)</span></span>|<span data-ttu-id="d2301-141">L または >/documents/report1.rdl」の</span><span class="sxs-lookup"><span data-stu-id="d2301-141">L or &</span></span>|  
|`Short`|<span data-ttu-id="d2301-142">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-142">(none)</span></span>|<span data-ttu-id="d2301-143">S</span><span class="sxs-lookup"><span data-stu-id="d2301-143">S</span></span>|  
|`Single`|<span data-ttu-id="d2301-144">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-144">(none)</span></span>|<span data-ttu-id="d2301-145">F または!</span><span class="sxs-lookup"><span data-stu-id="d2301-145">F or !</span></span>|  
|`String`|<span data-ttu-id="d2301-146">"</span><span class="sxs-lookup"><span data-stu-id="d2301-146">"</span></span>|<span data-ttu-id="d2301-147">(なし)</span><span class="sxs-lookup"><span data-stu-id="d2301-147">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2301-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2301-148">See Also</span></span>  
 <span data-ttu-id="d2301-149">[ユーザー定義定数](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md) </span><span class="sxs-lookup"><span data-stu-id="d2301-149">[User-Defined Constants](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md) </span></span>  
<span data-ttu-id="d2301-150"> [方法: 定数の宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md) </span><span class="sxs-lookup"><span data-stu-id="d2301-150"> [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md) </span></span>  
<span data-ttu-id="d2301-151"> [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="d2301-151"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="d2301-152"> [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d2301-152"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="d2301-153"> [Option Explicit ステートメント](../../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d2301-153"> [Option Explicit Statement](../../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="d2301-154"> [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="d2301-154"> [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="d2301-155"> [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="d2301-155"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="d2301-156"> [列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="d2301-156"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="d2301-157"> [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="d2301-157"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="d2301-158"> [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="d2301-158"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
