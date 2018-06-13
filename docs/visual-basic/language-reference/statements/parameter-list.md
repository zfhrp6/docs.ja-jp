---
title: パラメーターの一覧 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 147a2501219db9f1f1c10f9cf1a81aa395b5ec2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605057"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="5406b-102">パラメーターの一覧 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5406b-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="5406b-103">プロシージャが呼び出された場合を想定パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="5406b-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="5406b-104">複数のパラメーターは、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="5406b-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="5406b-105">1 つのパラメーターの構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5406b-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5406b-106">構文</span><span class="sxs-lookup"><span data-stu-id="5406b-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="5406b-107">指定項目</span><span class="sxs-lookup"><span data-stu-id="5406b-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="5406b-108">任意。</span><span class="sxs-lookup"><span data-stu-id="5406b-108">Optional.</span></span> <span data-ttu-id="5406b-109">このパラメーターに適用される属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="5406b-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="5406b-110">囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ ("`<`「と」`>`") です。</span><span class="sxs-lookup"><span data-stu-id="5406b-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="5406b-111">任意。</span><span class="sxs-lookup"><span data-stu-id="5406b-111">Optional.</span></span> <span data-ttu-id="5406b-112">プロシージャが呼び出されたときに、このパラメーターが必要ないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="5406b-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="5406b-113">任意。</span><span class="sxs-lookup"><span data-stu-id="5406b-113">Optional.</span></span> <span data-ttu-id="5406b-114">プロシージャが置換または呼び出し元のコードに対応する引数の基になる変数の要素を再割り当てできませんを指定します。</span><span class="sxs-lookup"><span data-stu-id="5406b-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="5406b-115">任意。</span><span class="sxs-lookup"><span data-stu-id="5406b-115">Optional.</span></span> <span data-ttu-id="5406b-116">プロシージャ要素を変更できます、基になる変数呼び出し元のコードに呼び出し元コード自体と同じようを指定します。</span><span class="sxs-lookup"><span data-stu-id="5406b-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="5406b-117">任意。</span><span class="sxs-lookup"><span data-stu-id="5406b-117">Optional.</span></span> <span data-ttu-id="5406b-118">パラメーター リストの最後のパラメーターが指定されたデータ型の要素の省略可能な配列であることを示します。</span><span class="sxs-lookup"><span data-stu-id="5406b-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="5406b-119">これにより、呼び出し元のコード、プロシージャに任意の数の引数を渡します。</span><span class="sxs-lookup"><span data-stu-id="5406b-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="5406b-120">必須。</span><span class="sxs-lookup"><span data-stu-id="5406b-120">Required.</span></span> <span data-ttu-id="5406b-121">パラメーターを表すローカル変数の名前です。</span><span class="sxs-lookup"><span data-stu-id="5406b-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="5406b-122">場合は必須`Option Strict`は`On`します。</span><span class="sxs-lookup"><span data-stu-id="5406b-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="5406b-123">パラメーターを表すローカル変数のデータ型。</span><span class="sxs-lookup"><span data-stu-id="5406b-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="5406b-124">必要な`Optional`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="5406b-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="5406b-125">パラメーターのデータ型に評価される定数または定数式です。</span><span class="sxs-lookup"><span data-stu-id="5406b-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="5406b-126">型の場合`Object`、クラス、インターフェイス、配列、または構造体では、既定値は、必ずまたは`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="5406b-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5406b-127">コメント</span><span class="sxs-lookup"><span data-stu-id="5406b-127">Remarks</span></span>  
 <span data-ttu-id="5406b-128">パラメーターはかっこで囲まれているし、コンマで区切られました。</span><span class="sxs-lookup"><span data-stu-id="5406b-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="5406b-129">パラメーターは、任意のデータ型で宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="5406b-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="5406b-130">指定しない場合`parametertype`、既定値は`Object`します。</span><span class="sxs-lookup"><span data-stu-id="5406b-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="5406b-131">呼び出し元のコードはプロシージャを呼び出すときに渡します、*引数*各必須パラメーターにします。</span><span class="sxs-lookup"><span data-stu-id="5406b-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="5406b-132">詳細については、次を参照してください。[の相違点の間でパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)です。</span><span class="sxs-lookup"><span data-stu-id="5406b-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="5406b-133">呼び出し元のコードは、各パラメーターに渡す引数は、呼び出し元のコード内の基になる要素へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="5406b-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="5406b-134">この要素は場合*不変*(定数、リテラル、列挙型、または式)、すべてのコードを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="5406b-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="5406b-135">ある場合、*変数*要素 (宣言された変数、フィールド、プロパティ、配列要素、または構造体の要素)、呼び出し元のコードで変更できます。</span><span class="sxs-lookup"><span data-stu-id="5406b-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="5406b-136">詳細については、次を参照してください。[の相違点の間で変更可能なと変更できない引数](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)です。</span><span class="sxs-lookup"><span data-stu-id="5406b-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="5406b-137">変数の要素が渡された場合`ByRef`プロシージャが同様に変更できます。</span><span class="sxs-lookup"><span data-stu-id="5406b-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="5406b-138">詳細については、次を参照してください。[の相違点の間で値と参照渡しによって引数の渡し](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)です。</span><span class="sxs-lookup"><span data-stu-id="5406b-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5406b-139">ルール</span><span class="sxs-lookup"><span data-stu-id="5406b-139">Rules</span></span>  
  
-   <span data-ttu-id="5406b-140">**かっこです。**</span><span class="sxs-lookup"><span data-stu-id="5406b-140">**Parentheses.**</span></span> <span data-ttu-id="5406b-141">パラメーター リストを指定する場合は、かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="5406b-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="5406b-142">パラメーターがない場合でも、空のリストを囲むかっこを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5406b-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="5406b-143">これにより、明確にすること、その要素は、プロシージャによって、コードの読みやすさが向上します。</span><span class="sxs-lookup"><span data-stu-id="5406b-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
-   <span data-ttu-id="5406b-144">**省略可能なパラメーターです。**</span><span class="sxs-lookup"><span data-stu-id="5406b-144">**Optional Parameters.**</span></span> <span data-ttu-id="5406b-145">使用する場合、`Optional`パラメーター修飾子は、リスト内のすべての後続のパラメーターはオプションもありを使用して宣言する、`Optional`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="5406b-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="5406b-146">省略可能なパラメーターのすべての宣言を指定する必要があります、`defaultvalue`句。</span><span class="sxs-lookup"><span data-stu-id="5406b-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="5406b-147">詳細については、次を参照してください。[省略可能なパラメーター](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)です。</span><span class="sxs-lookup"><span data-stu-id="5406b-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
-   <span data-ttu-id="5406b-148">**パラメーターの配列。**</span><span class="sxs-lookup"><span data-stu-id="5406b-148">**Parameter Arrays.**</span></span> <span data-ttu-id="5406b-149">指定する必要があります`ByVal`の`ParamArray`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="5406b-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="5406b-150">両方を使用することはできません`Optional`と`ParamArray`同じパラメーター リストにします。</span><span class="sxs-lookup"><span data-stu-id="5406b-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="5406b-151">詳細については、次を参照してください。[パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)です。</span><span class="sxs-lookup"><span data-stu-id="5406b-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
-   <span data-ttu-id="5406b-152">**値渡し。**</span><span class="sxs-lookup"><span data-stu-id="5406b-152">**Passing Mechanism.**</span></span> <span data-ttu-id="5406b-153">すべての引数に対して既定のメカニズムは`ByVal`プロシージャは、基になる変数要素を変更ことはできません。</span><span class="sxs-lookup"><span data-stu-id="5406b-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="5406b-154">ただし、要素が参照型の場合は、プロシージャが変更できます内容や、基になるオブジェクトのメンバーでも置換や、オブジェクト自体を再割り当てはできません。</span><span class="sxs-lookup"><span data-stu-id="5406b-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
-   <span data-ttu-id="5406b-155">**パラメーター名。**</span><span class="sxs-lookup"><span data-stu-id="5406b-155">**Parameter Names.**</span></span> <span data-ttu-id="5406b-156">次のパラメーターのデータ型が配列の場合は、`parametername`かっこの直後にします。</span><span class="sxs-lookup"><span data-stu-id="5406b-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="5406b-157">パラメーター名の詳細については、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="5406b-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5406b-158">例</span><span class="sxs-lookup"><span data-stu-id="5406b-158">Example</span></span>  
 <span data-ttu-id="5406b-159">次の例は、 `Function` 2 つのパラメーターを定義するプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="5406b-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5406b-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="5406b-160">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="5406b-161">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="5406b-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="5406b-162">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="5406b-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="5406b-163">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="5406b-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="5406b-164">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="5406b-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="5406b-165">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="5406b-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="5406b-166">属性の概要</span><span class="sxs-lookup"><span data-stu-id="5406b-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="5406b-167">方法 : コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="5406b-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
