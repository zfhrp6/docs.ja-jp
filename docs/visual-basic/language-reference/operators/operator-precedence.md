---
title: "Visual Basic における演算子の優先順位"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c0fb466b404cafdd4b91d061971fd683375c715
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="74f91-102">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="74f91-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="74f91-103">いくつかの操作は、式の中で発生した場合、各部分が評価されと呼ばれる事前に定義された順序で解決*演算子の優先順位*です。</span><span class="sxs-lookup"><span data-stu-id="74f91-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>  
  
## <a name="precedence-rules"></a><span data-ttu-id="74f91-104">優先順位の規則</span><span class="sxs-lookup"><span data-stu-id="74f91-104">Precedence Rules</span></span>  
 <span data-ttu-id="74f91-105">式に複数のカテゴリからの演算子が含まれている場合は、次の規則に従って評価されます。</span><span class="sxs-lookup"><span data-stu-id="74f91-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>  
  
-   <span data-ttu-id="74f91-106">算術演算子と連結演算子の優先順位が次のセクションで説明されているが、比較、論理より大きい優先順位とビットごとの演算子。</span><span class="sxs-lookup"><span data-stu-id="74f91-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>  
  
-   <span data-ttu-id="74f91-107">優先順位が等しく、すべてほど、優先順位、論理演算子およびビット演算子、算術演算子と連結演算子よりも優先順位が低く、すべての比較演算子があります。</span><span class="sxs-lookup"><span data-stu-id="74f91-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>  
  
-   <span data-ttu-id="74f91-108">論理/ビット処理演算子の優先順位が次のセクションで説明しますが、算術演算子、文字列連結演算子、および比較演算子よりも優先順位が低くします。</span><span class="sxs-lookup"><span data-stu-id="74f91-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>  
  
-   <span data-ttu-id="74f91-109">右に優先順位の等しい演算子は左評価式内に出現する順序で。</span><span class="sxs-lookup"><span data-stu-id="74f91-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>  
  
## <a name="precedence-order"></a><span data-ttu-id="74f91-110">優先順位</span><span class="sxs-lookup"><span data-stu-id="74f91-110">Precedence Order</span></span>  
 <span data-ttu-id="74f91-111">演算子は優先順位の次の順序で評価されます。</span><span class="sxs-lookup"><span data-stu-id="74f91-111">Operators are evaluated in the following order of precedence:</span></span>  
  
### <a name="await-operator"></a><span data-ttu-id="74f91-112">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="74f91-112">Await Operator</span></span>  
 <span data-ttu-id="74f91-113">Await </span><span class="sxs-lookup"><span data-stu-id="74f91-113">Await</span></span>  
  
### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="74f91-114">算術演算子と連結演算子</span><span class="sxs-lookup"><span data-stu-id="74f91-114">Arithmetic and Concatenation Operators</span></span>  
 <span data-ttu-id="74f91-115">指数演算 (`^`)</span><span class="sxs-lookup"><span data-stu-id="74f91-115">Exponentiation (`^`)</span></span>  
  
 <span data-ttu-id="74f91-116">単項 id および否定 (`+`、 `–`)</span><span class="sxs-lookup"><span data-stu-id="74f91-116">Unary identity and negation (`+`, `–`)</span></span>  
  
 <span data-ttu-id="74f91-117">乗算と浮動小数点除算 (`*`、 `/`)</span><span class="sxs-lookup"><span data-stu-id="74f91-117">Multiplication and floating-point division (`*`, `/`)</span></span>  
  
 <span data-ttu-id="74f91-118">整数の除算 (`\`)</span><span class="sxs-lookup"><span data-stu-id="74f91-118">Integer division (`\`)</span></span>  
  
 <span data-ttu-id="74f91-119">剰余演算 (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="74f91-119">Modulus arithmetic (`Mod`)</span></span>  
  
 <span data-ttu-id="74f91-120">加算と減算 (`+`、 `–`)</span><span class="sxs-lookup"><span data-stu-id="74f91-120">Addition and subtraction (`+`, `–`)</span></span>  
  
 <span data-ttu-id="74f91-121">文字列の連結 (`&`)</span><span class="sxs-lookup"><span data-stu-id="74f91-121">String concatenation (`&`)</span></span>  
  
 <span data-ttu-id="74f91-122">算術ビット シフト (`<<`、 `>>`)</span><span class="sxs-lookup"><span data-stu-id="74f91-122">Arithmetic bit shift (`<<`, `>>`)</span></span>  
  
### <a name="comparison-operators"></a><span data-ttu-id="74f91-123">比較演算子</span><span class="sxs-lookup"><span data-stu-id="74f91-123">Comparison Operators</span></span>  
 <span data-ttu-id="74f91-124">すべての比較演算子 (`=`、 `<>`、 `<`、 `<=`、 `>`、 `>=`、 `Is`、 `IsNot`、 `Like`、 `TypeOf`.`Is`)</span><span class="sxs-lookup"><span data-stu-id="74f91-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>  
  
### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="74f91-125">論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="74f91-125">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="74f91-126">否定 (`Not`)</span><span class="sxs-lookup"><span data-stu-id="74f91-126">Negation (`Not`)</span></span>  
  
 <span data-ttu-id="74f91-127">連携 (`And`、 `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="74f91-127">Conjunction (`And`, `AndAlso`)</span></span>  
  
 <span data-ttu-id="74f91-128">包括的論理和 (`Or`、 `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="74f91-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>  
  
 <span data-ttu-id="74f91-129">排他的論理和 (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="74f91-129">Exclusive disjunction (`Xor`)</span></span>  
  
### <a name="comments"></a><span data-ttu-id="74f91-130">コメント</span><span class="sxs-lookup"><span data-stu-id="74f91-130">Comments</span></span>  
 <span data-ttu-id="74f91-131">`=`演算子はのみ、等値比較演算子、代入演算子ではありません。</span><span class="sxs-lookup"><span data-stu-id="74f91-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="74f91-132">文字列連結演算子 (`&`) は、算術演算子ではありませんが、算術演算子を使用してグループ化の優先順位に従ってします。</span><span class="sxs-lookup"><span data-stu-id="74f91-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>  
  
 <span data-ttu-id="74f91-133">`Is`と`IsNot`演算子は、オブジェクト参照の比較演算子です。</span><span class="sxs-lookup"><span data-stu-id="74f91-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="74f91-134">これら 2 つのオブジェクトの値は比較されません。2 つのオブジェクト変数が同じオブジェクト インスタンスを参照しているかどうかを確認するためだけチェックします。</span><span class="sxs-lookup"><span data-stu-id="74f91-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>  
  
## <a name="associativity"></a><span data-ttu-id="74f91-135">結合規則</span><span class="sxs-lookup"><span data-stu-id="74f91-135">Associativity</span></span>  
 <span data-ttu-id="74f91-136">同じ優先順位の演算子は、式、乗算と除算では、たとえばにまとめて表示されます。 検出されると、左から右に、コンパイラは各操作を評価します。</span><span class="sxs-lookup"><span data-stu-id="74f91-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="74f91-137">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="74f91-137">The following example illustrates this.</span></span>  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 <span data-ttu-id="74f91-138">1 番目の式、除算 96/8 (これは、結果は 12) し、除算 12/4 で、結果は 3 です。</span><span class="sxs-lookup"><span data-stu-id="74f91-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="74f91-139">コンパイラは、操作を評価するため`n1`左から右の評価は、同じ場合、その注文が明示的に示されています`n2`です。</span><span class="sxs-lookup"><span data-stu-id="74f91-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="74f91-140">両方`n1`と`n2`3 つの結果になります。</span><span class="sxs-lookup"><span data-stu-id="74f91-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="74f91-141">これに対し、`n3`がかっこは、8 を評価するコンパイラを強制するために、48 の結果を保持する/4 最初。</span><span class="sxs-lookup"><span data-stu-id="74f91-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>  
  
 <span data-ttu-id="74f91-142">この動作のための演算子と呼ばれます*左結合*で[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="74f91-142">Because of this behavior, operators are said to be *left associative* in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="74f91-143">優先順位と結合規則のオーバーライド</span><span class="sxs-lookup"><span data-stu-id="74f91-143">Overriding Precedence and Associativity</span></span>  
 <span data-ttu-id="74f91-144">かっこを使用すると、他のユーザーの前に評価される式の一部を強制します。</span><span class="sxs-lookup"><span data-stu-id="74f91-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="74f91-145">これには、優先順位の順序と左の結合規則の両方をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="74f91-145">This can override both the order of precedence and the left associativity.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="74f91-146">常に外部の前にかっこで囲まれた演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="74f91-146"> always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="74f91-147">ただし、かっこ内で維持通常の優先順位と結合規則にかっこを使用する場合を除き、します。</span><span class="sxs-lookup"><span data-stu-id="74f91-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="74f91-148">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="74f91-148">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74f91-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="74f91-149">See Also</span></span>  
 [<span data-ttu-id="74f91-150">= 演算子</span><span class="sxs-lookup"><span data-stu-id="74f91-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [<span data-ttu-id="74f91-151">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="74f91-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="74f91-152">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="74f91-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="74f91-153">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="74f91-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="74f91-154">TypeOf 演算子</span><span class="sxs-lookup"><span data-stu-id="74f91-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="74f91-155">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="74f91-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="74f91-156">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="74f91-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="74f91-157">演算子および式</span><span class="sxs-lookup"><span data-stu-id="74f91-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
