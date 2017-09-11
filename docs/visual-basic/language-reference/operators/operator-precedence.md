---
title: "Visual Basic の演算子の優先順位 |Microsoft ドキュメント"
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
- arithmetic operators, precedence
- operator precedence
- logical operators, precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators
- operators [Visual Basic], precedence
- precedence, of operators
- comparison operators, precedence
- math operators
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
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
ms.openlocfilehash: f653dd83c9778dddfe0e52db27065f7d73866e37
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="14865-102">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="14865-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="14865-103">各部分が評価されと呼ばれる指定された順序で解決されるいくつかの操作は、式の中で発生した場合、*演算子の優先順位*します。</span><span class="sxs-lookup"><span data-stu-id="14865-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>  
  
## <a name="precedence-rules"></a><span data-ttu-id="14865-104">優先順位の規則</span><span class="sxs-lookup"><span data-stu-id="14865-104">Precedence Rules</span></span>  
 <span data-ttu-id="14865-105">式に複数のカテゴリから、演算子が含まれている場合は、次の規則に従って評価されます。</span><span class="sxs-lookup"><span data-stu-id="14865-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>  
  
-   <span data-ttu-id="14865-106">算術演算と文字列連結演算子の優先順位が次のセクションで説明したが、比較、論理、ほど、優先順位とビット処理演算子。</span><span class="sxs-lookup"><span data-stu-id="14865-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>  
  
-   <span data-ttu-id="14865-107">すべての比較演算子は、同じ優先順位と必要なは、ビットごとの論理演算子より優先順位の高いが、算術演算と文字列連結演算子よりも優先順位の低いがあります。</span><span class="sxs-lookup"><span data-stu-id="14865-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>  
  
-   <span data-ttu-id="14865-108">論理/ビット処理演算子の優先順位が次のセクションで説明しますが、算術演算子、文字列連結演算子、および比較演算子より優先されます。</span><span class="sxs-lookup"><span data-stu-id="14865-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>  
  
-   <span data-ttu-id="14865-109">左から右に優先順位の等しい演算子は評価式での出現順序で。</span><span class="sxs-lookup"><span data-stu-id="14865-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>  
  
## <a name="precedence-order"></a><span data-ttu-id="14865-110">優先順位</span><span class="sxs-lookup"><span data-stu-id="14865-110">Precedence Order</span></span>  
 <span data-ttu-id="14865-111">演算子は優先順位の次の順序で評価されます。</span><span class="sxs-lookup"><span data-stu-id="14865-111">Operators are evaluated in the following order of precedence:</span></span>  
  
### <a name="await-operator"></a><span data-ttu-id="14865-112">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="14865-112">Await Operator</span></span>  
 <span data-ttu-id="14865-113">Await </span><span class="sxs-lookup"><span data-stu-id="14865-113">Await</span></span>  
  
### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="14865-114">算術演算や文字列連結演算子</span><span class="sxs-lookup"><span data-stu-id="14865-114">Arithmetic and Concatenation Operators</span></span>  
 <span data-ttu-id="14865-115">指数演算 (`^`)</span><span class="sxs-lookup"><span data-stu-id="14865-115">Exponentiation (`^`)</span></span>  
  
 <span data-ttu-id="14865-116">単項の id と否定 (`+`、 `–`)</span><span class="sxs-lookup"><span data-stu-id="14865-116">Unary identity and negation (`+`, `–`)</span></span>  
  
 <span data-ttu-id="14865-117">乗算と除算の浮動小数点 (`*`、 `/`)</span><span class="sxs-lookup"><span data-stu-id="14865-117">Multiplication and floating-point division (`*`, `/`)</span></span>  
  
 <span data-ttu-id="14865-118">整数除算 (`\`)</span><span class="sxs-lookup"><span data-stu-id="14865-118">Integer division (`\`)</span></span>  
  
 <span data-ttu-id="14865-119">剰余演算 (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="14865-119">Modulus arithmetic (`Mod`)</span></span>  
  
 <span data-ttu-id="14865-120">加算と減算 (`+`、 `–`)</span><span class="sxs-lookup"><span data-stu-id="14865-120">Addition and subtraction (`+`, `–`)</span></span>  
  
 <span data-ttu-id="14865-121">文字列連結 (`&`)</span><span class="sxs-lookup"><span data-stu-id="14865-121">String concatenation (`&`)</span></span>  
  
 <span data-ttu-id="14865-122">算術ビット シフト (`<<`、 `>>`)</span><span class="sxs-lookup"><span data-stu-id="14865-122">Arithmetic bit shift (`<<`, `>>`)</span></span>  
  
### <a name="comparison-operators"></a><span data-ttu-id="14865-123">比較演算子</span><span class="sxs-lookup"><span data-stu-id="14865-123">Comparison Operators</span></span>  
 <span data-ttu-id="14865-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span><span class="sxs-lookup"><span data-stu-id="14865-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>  
  
### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="14865-125">論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="14865-125">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="14865-126">否定 (`Not`)</span><span class="sxs-lookup"><span data-stu-id="14865-126">Negation (`Not`)</span></span>  
  
 <span data-ttu-id="14865-127">連携 (`And`、 `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="14865-127">Conjunction (`And`, `AndAlso`)</span></span>  
  
 <span data-ttu-id="14865-128">包括的論理和 (`Or`、 `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="14865-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>  
  
 <span data-ttu-id="14865-129">排他的論理和 (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="14865-129">Exclusive disjunction (`Xor`)</span></span>  
  
### <a name="comments"></a><span data-ttu-id="14865-130">コメント</span><span class="sxs-lookup"><span data-stu-id="14865-130">Comments</span></span>  
 <span data-ttu-id="14865-131">`=`演算子は等値比較演算子のみ、代入演算子ではありません。</span><span class="sxs-lookup"><span data-stu-id="14865-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="14865-132">文字列連結演算子 (`&`)、算術演算子ではありませんが、算術演算子を使用して同じ優先順位。</span><span class="sxs-lookup"><span data-stu-id="14865-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>  
  
 <span data-ttu-id="14865-133">`Is`と`IsNot`演算子は、オブジェクト参照の比較演算子です。</span><span class="sxs-lookup"><span data-stu-id="14865-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="14865-134">2 つのオブジェクトの値を比較しないでこれらは、2 つのオブジェクト変数が同じオブジェクト インスタンスを参照しているかどうかのみを確認します。</span><span class="sxs-lookup"><span data-stu-id="14865-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>  
  
## <a name="associativity"></a><span data-ttu-id="14865-135">結合規則</span><span class="sxs-lookup"><span data-stu-id="14865-135">Associativity</span></span>  
 <span data-ttu-id="14865-136">乗算と除算、たとえば、式に同じ優先順位の演算子を並べてを検出すると、左から右に、コンパイラは各操作を評価します。</span><span class="sxs-lookup"><span data-stu-id="14865-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="14865-137">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="14865-137">The following example illustrates this.</span></span>  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 <span data-ttu-id="14865-138">1 番目の式では、除算 96/8 (これは、結果は 12) し、除算 12/4 で、結果は 3 です。</span><span class="sxs-lookup"><span data-stu-id="14865-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="14865-139">コンパイラは、操作を評価するため`n1`左から右から、評価は、同じ順がに対して明示的に指定された場合`n2`します。</span><span class="sxs-lookup"><span data-stu-id="14865-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="14865-140">両方とも`n1`と`n2`3 つの結果になります。</span><span class="sxs-lookup"><span data-stu-id="14865-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="14865-141">これに対し、`n3`かっこコンパイラは 8 の評価を強制するため、48 の結果がある/4 最初です。</span><span class="sxs-lookup"><span data-stu-id="14865-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>  
  
 <span data-ttu-id="14865-142">この動作のために演算子があると考え*結合関係が左*で[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="14865-142">Because of this behavior, operators are said to be *left associative* in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="14865-143">優先順位と結合規則をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="14865-143">Overriding Precedence and Associativity</span></span>  
 <span data-ttu-id="14865-144">かっこを使用して、他のユーザーの前に評価される式の一部を強制することができます。</span><span class="sxs-lookup"><span data-stu-id="14865-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="14865-145">これは、優先順位の順序と左の結合規則の両方に上書きすることができます。</span><span class="sxs-lookup"><span data-stu-id="14865-145">This can override both the order of precedence and the left associativity.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="14865-146">常に外部の前にかっこで囲まれた操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="14865-146"> always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="14865-147">一方、かっこ内で保持通常の優先順位と結合規則、かっこの中でかっこを使用していない場合。</span><span class="sxs-lookup"><span data-stu-id="14865-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="14865-148">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="14865-148">The following example illustrates this.</span></span>  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a><span data-ttu-id="14865-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="14865-149">See Also</span></span>  
 <span data-ttu-id="14865-150">[= 演算子](../../../visual-basic/language-reference/operators/assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="14865-150">[= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) </span></span>  
<span data-ttu-id="14865-151"> [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="14865-151"> [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="14865-152"> [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="14865-152"> [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="14865-153"> [Like 演算子](../../../visual-basic/language-reference/operators/like-operator.md) </span><span class="sxs-lookup"><span data-stu-id="14865-153"> [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md) </span></span>  
<span data-ttu-id="14865-154"> [TypeOf 演算子](../../../visual-basic/language-reference/operators/typeof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="14865-154"> [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md) </span></span>  
<span data-ttu-id="14865-155"> [Await 演算子](../../../visual-basic/language-reference/operators/await-operator.md) </span><span class="sxs-lookup"><span data-stu-id="14865-155"> [Await Operator](../../../visual-basic/language-reference/operators/await-operator.md) </span></span>  
<span data-ttu-id="14865-156"> [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="14865-156"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="14865-157"> [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span><span class="sxs-lookup"><span data-stu-id="14865-157"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span></span>
