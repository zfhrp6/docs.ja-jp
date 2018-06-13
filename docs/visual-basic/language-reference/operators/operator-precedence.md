---
title: Visual Basic における演算子の優先順位
ms.date: 07/20/2015
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
ms.openlocfilehash: 211a710f4dba2310ea1ae74decdb1926ce612a62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605005"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="2bc35-102">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="2bc35-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="2bc35-103">いくつかの操作は、式の中で発生した場合、各部分が評価されと呼ばれる事前に定義された順序で解決*演算子の優先順位*です。</span><span class="sxs-lookup"><span data-stu-id="2bc35-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>  
  
## <a name="precedence-rules"></a><span data-ttu-id="2bc35-104">優先順位の規則</span><span class="sxs-lookup"><span data-stu-id="2bc35-104">Precedence Rules</span></span>  
 <span data-ttu-id="2bc35-105">式に複数のカテゴリからの演算子が含まれている場合は、次の規則に従って評価されます。</span><span class="sxs-lookup"><span data-stu-id="2bc35-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>  
  
-   <span data-ttu-id="2bc35-106">算術演算子と連結演算子の優先順位が次のセクションで説明されているが、比較、論理より大きい優先順位とビットごとの演算子。</span><span class="sxs-lookup"><span data-stu-id="2bc35-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>  
  
-   <span data-ttu-id="2bc35-107">優先順位が等しく、すべてほど、優先順位、論理演算子およびビット演算子、算術演算子と連結演算子よりも優先順位が低く、すべての比較演算子があります。</span><span class="sxs-lookup"><span data-stu-id="2bc35-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>  
  
-   <span data-ttu-id="2bc35-108">論理/ビット処理演算子の優先順位が次のセクションで説明しますが、算術演算子、文字列連結演算子、および比較演算子よりも優先順位が低くします。</span><span class="sxs-lookup"><span data-stu-id="2bc35-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>  
  
-   <span data-ttu-id="2bc35-109">右に優先順位の等しい演算子は左評価式内に出現する順序で。</span><span class="sxs-lookup"><span data-stu-id="2bc35-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>  
  
## <a name="precedence-order"></a><span data-ttu-id="2bc35-110">優先順位</span><span class="sxs-lookup"><span data-stu-id="2bc35-110">Precedence Order</span></span>  
 <span data-ttu-id="2bc35-111">演算子は優先順位の次の順序で評価されます。</span><span class="sxs-lookup"><span data-stu-id="2bc35-111">Operators are evaluated in the following order of precedence:</span></span>  
  
### <a name="await-operator"></a><span data-ttu-id="2bc35-112">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="2bc35-112">Await Operator</span></span>  
 <span data-ttu-id="2bc35-113">Await </span><span class="sxs-lookup"><span data-stu-id="2bc35-113">Await</span></span>  
  
### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="2bc35-114">算術演算子と連結演算子</span><span class="sxs-lookup"><span data-stu-id="2bc35-114">Arithmetic and Concatenation Operators</span></span>  
 <span data-ttu-id="2bc35-115">指数演算 (`^`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-115">Exponentiation (`^`)</span></span>  
  
 <span data-ttu-id="2bc35-116">単項 id および否定 (`+`、 `–`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-116">Unary identity and negation (`+`, `–`)</span></span>  
  
 <span data-ttu-id="2bc35-117">乗算と浮動小数点除算 (`*`、 `/`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-117">Multiplication and floating-point division (`*`, `/`)</span></span>  
  
 <span data-ttu-id="2bc35-118">整数の除算 (`\`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-118">Integer division (`\`)</span></span>  
  
 <span data-ttu-id="2bc35-119">剰余演算 (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-119">Modulus arithmetic (`Mod`)</span></span>  
  
 <span data-ttu-id="2bc35-120">加算と減算 (`+`、 `–`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-120">Addition and subtraction (`+`, `–`)</span></span>  
  
 <span data-ttu-id="2bc35-121">文字列の連結 (`&`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-121">String concatenation (`&`)</span></span>  
  
 <span data-ttu-id="2bc35-122">算術ビット シフト (`<<`、 `>>`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-122">Arithmetic bit shift (`<<`, `>>`)</span></span>  
  
### <a name="comparison-operators"></a><span data-ttu-id="2bc35-123">比較演算子</span><span class="sxs-lookup"><span data-stu-id="2bc35-123">Comparison Operators</span></span>  
 <span data-ttu-id="2bc35-124">すべての比較演算子 (`=`、 `<>`、 `<`、 `<=`、 `>`、 `>=`、 `Is`、 `IsNot`、 `Like`、 `TypeOf`.`Is`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>  
  
### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="2bc35-125">論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="2bc35-125">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="2bc35-126">否定 (`Not`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-126">Negation (`Not`)</span></span>  
  
 <span data-ttu-id="2bc35-127">連携 (`And`、 `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-127">Conjunction (`And`, `AndAlso`)</span></span>  
  
 <span data-ttu-id="2bc35-128">包括的論理和 (`Or`、 `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>  
  
 <span data-ttu-id="2bc35-129">排他的論理和 (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="2bc35-129">Exclusive disjunction (`Xor`)</span></span>  
  
### <a name="comments"></a><span data-ttu-id="2bc35-130">コメント</span><span class="sxs-lookup"><span data-stu-id="2bc35-130">Comments</span></span>  
 <span data-ttu-id="2bc35-131">`=`演算子はのみ、等値比較演算子、代入演算子ではありません。</span><span class="sxs-lookup"><span data-stu-id="2bc35-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="2bc35-132">文字列連結演算子 (`&`) は、算術演算子ではありませんが、算術演算子を使用してグループ化の優先順位に従ってします。</span><span class="sxs-lookup"><span data-stu-id="2bc35-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>  
  
 <span data-ttu-id="2bc35-133">`Is`と`IsNot`演算子は、オブジェクト参照の比較演算子です。</span><span class="sxs-lookup"><span data-stu-id="2bc35-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="2bc35-134">これら 2 つのオブジェクトの値は比較されません。2 つのオブジェクト変数が同じオブジェクト インスタンスを参照しているかどうかを確認するためだけチェックします。</span><span class="sxs-lookup"><span data-stu-id="2bc35-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>  
  
## <a name="associativity"></a><span data-ttu-id="2bc35-135">結合規則</span><span class="sxs-lookup"><span data-stu-id="2bc35-135">Associativity</span></span>  
 <span data-ttu-id="2bc35-136">同じ優先順位の演算子は、式、乗算と除算では、たとえばにまとめて表示されます。 検出されると、左から右に、コンパイラは各操作を評価します。</span><span class="sxs-lookup"><span data-stu-id="2bc35-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="2bc35-137">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2bc35-137">The following example illustrates this.</span></span>  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 <span data-ttu-id="2bc35-138">1 番目の式、除算 96/8 (これは、結果は 12) し、除算 12/4 で、結果は 3 です。</span><span class="sxs-lookup"><span data-stu-id="2bc35-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="2bc35-139">コンパイラは、操作を評価するため`n1`左から右の評価は、同じ場合、その注文が明示的に示されています`n2`です。</span><span class="sxs-lookup"><span data-stu-id="2bc35-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="2bc35-140">両方`n1`と`n2`3 つの結果になります。</span><span class="sxs-lookup"><span data-stu-id="2bc35-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="2bc35-141">これに対し、`n3`がかっこは、8 を評価するコンパイラを強制するために、48 の結果を保持する/4 最初。</span><span class="sxs-lookup"><span data-stu-id="2bc35-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>  
  
 <span data-ttu-id="2bc35-142">この動作のための演算子と呼ばれます*左結合*Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="2bc35-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>  
  
## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="2bc35-143">優先順位と結合規則のオーバーライド</span><span class="sxs-lookup"><span data-stu-id="2bc35-143">Overriding Precedence and Associativity</span></span>  
 <span data-ttu-id="2bc35-144">かっこを使用すると、他のユーザーの前に評価される式の一部を強制します。</span><span class="sxs-lookup"><span data-stu-id="2bc35-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="2bc35-145">これには、優先順位の順序と左の結合規則の両方をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="2bc35-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="2bc35-146">Visual Basic は、常に外部の前にかっこで囲まれた演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="2bc35-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="2bc35-147">ただし、かっこ内で維持通常の優先順位と結合規則にかっこを使用する場合を除き、します。</span><span class="sxs-lookup"><span data-stu-id="2bc35-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="2bc35-148">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2bc35-148">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2bc35-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bc35-149">See Also</span></span>  
 [<span data-ttu-id="2bc35-150">= 演算子</span><span class="sxs-lookup"><span data-stu-id="2bc35-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [<span data-ttu-id="2bc35-151">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="2bc35-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="2bc35-152">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="2bc35-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="2bc35-153">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="2bc35-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="2bc35-154">TypeOf 演算子</span><span class="sxs-lookup"><span data-stu-id="2bc35-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="2bc35-155">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="2bc35-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="2bc35-156">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="2bc35-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="2bc35-157">演算子および式</span><span class="sxs-lookup"><span data-stu-id="2bc35-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
