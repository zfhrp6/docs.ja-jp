---
title: "パラメーターの一覧 (Visual Basic) |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- parameters, Visual Basic
- parameters, lists
- parameter lists
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures, parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
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
ms.openlocfilehash: cc56d90db9a732928773fa549cb1456d368e1dbe
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="17dac-102">パラメーターの一覧 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17dac-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="17dac-103">プロシージャが呼び出された場合に想定パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="17dac-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="17dac-104">複数のパラメーターは、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="17dac-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="17dac-105">1 つのパラメーターの構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="17dac-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17dac-106">構文</span><span class="sxs-lookup"><span data-stu-id="17dac-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="17dac-107">指定項目</span><span class="sxs-lookup"><span data-stu-id="17dac-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="17dac-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="17dac-108">Optional.</span></span> <span data-ttu-id="17dac-109">このパラメーターに適用される属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="17dac-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="17dac-110">囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこで ("`<`「と」`>`") です。</span><span class="sxs-lookup"><span data-stu-id="17dac-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="17dac-111">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="17dac-111">Optional.</span></span> <span data-ttu-id="17dac-112">プロシージャが呼び出されたときに、このパラメーターは必要ないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="17dac-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="17dac-113">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="17dac-113">Optional.</span></span> <span data-ttu-id="17dac-114">プロシージャが置換または呼び出し元のコードで対応する引数の基になる変数の要素を再割り当てできませんを指定します。</span><span class="sxs-lookup"><span data-stu-id="17dac-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="17dac-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="17dac-115">Optional.</span></span> <span data-ttu-id="17dac-116">いるプロシージャ要素を変更できます、基になる変数、呼び出し元コードに呼び出し元コード自体と同じよう指定します。</span><span class="sxs-lookup"><span data-stu-id="17dac-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="17dac-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="17dac-117">Optional.</span></span> <span data-ttu-id="17dac-118">パラメーター リストの最後のパラメーターが指定されたデータ型の要素の省略可能な配列であることを示します。</span><span class="sxs-lookup"><span data-stu-id="17dac-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="17dac-119">これには、呼び出し元のコードをプロシージャに任意の数の引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="17dac-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="17dac-120">必須です。</span><span class="sxs-lookup"><span data-stu-id="17dac-120">Required.</span></span> <span data-ttu-id="17dac-121">パラメーターを表すローカル変数の名前です。</span><span class="sxs-lookup"><span data-stu-id="17dac-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="17dac-122">必要な場合`Option Strict`は`On`です。</span><span class="sxs-lookup"><span data-stu-id="17dac-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="17dac-123">パラメーターを表すローカル変数のデータ型。</span><span class="sxs-lookup"><span data-stu-id="17dac-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="17dac-124">必要な`Optional`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="17dac-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="17dac-125">パラメーターのデータ型に評価される定数または定数式です。</span><span class="sxs-lookup"><span data-stu-id="17dac-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="17dac-126">型の場合`Object`、クラス、インターフェイス、配列、または構造体では、既定値は、必ずまたは`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="17dac-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17dac-127">コメント</span><span class="sxs-lookup"><span data-stu-id="17dac-127">Remarks</span></span>  
 <span data-ttu-id="17dac-128">パラメーターはかっこで囲まれているし、コンマで区切っています。</span><span class="sxs-lookup"><span data-stu-id="17dac-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="17dac-129">パラメーターは、任意のデータ型で宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="17dac-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="17dac-130">指定しない場合`parametertype`、既定値は`Object`です。</span><span class="sxs-lookup"><span data-stu-id="17dac-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="17dac-131">呼び出し元のコードはプロシージャを呼び出す際に渡して、*引数*各必須パラメーターにします。</span><span class="sxs-lookup"><span data-stu-id="17dac-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="17dac-132">詳細については、次を参照してください。[の相違点の間でパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)します。</span><span class="sxs-lookup"><span data-stu-id="17dac-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="17dac-133">呼び出し元のコードは、各パラメーターに渡す引数は、呼び出し元のコード内の基になる要素へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="17dac-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="17dac-134">この要素は場合*不変*(定数、リテラル、列挙体、または式)、すべてのコードを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="17dac-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="17dac-135">ある場合、*変数*要素 (宣言された変数、フィールド、プロパティ、配列の要素、または構造体の要素)、呼び出し元のコードで変更できます。</span><span class="sxs-lookup"><span data-stu-id="17dac-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="17dac-136">詳細については、次を参照してください。[変更間の相違点と変更できない引数](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)します。</span><span class="sxs-lookup"><span data-stu-id="17dac-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="17dac-137">Variable 要素が渡された場合`ByRef`プロシージャが同様に変更できます。</span><span class="sxs-lookup"><span data-stu-id="17dac-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="17dac-138">詳細については、次を参照してください。[の相違点の間の値と参照渡しによって引数の渡し](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)します。</span><span class="sxs-lookup"><span data-stu-id="17dac-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="17dac-139">ルール</span><span class="sxs-lookup"><span data-stu-id="17dac-139">Rules</span></span>  
  
-   <span data-ttu-id="17dac-140">**かっこです。**</span><span class="sxs-lookup"><span data-stu-id="17dac-140">**Parentheses.**</span></span> <span data-ttu-id="17dac-141">パラメーター リストを指定する場合は、かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="17dac-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="17dac-142">パラメーターがない場合、空のリストを囲むかっこを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="17dac-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="17dac-143">これにより、要素は、プロシージャを明確にすることによって、コードの読みやすさが向上します。</span><span class="sxs-lookup"><span data-stu-id="17dac-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
-   <span data-ttu-id="17dac-144">**省略可能なパラメーターです。**</span><span class="sxs-lookup"><span data-stu-id="17dac-144">**Optional Parameters.**</span></span> <span data-ttu-id="17dac-145">使用する場合、`Optional`パラメーターに対する修飾子は、一覧に続くすべてのパラメーターはオプションもありを使用して宣言する、`Optional`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="17dac-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="17dac-146">すべての省略可能なパラメーター宣言を指定する必要があります、`defaultvalue`句。</span><span class="sxs-lookup"><span data-stu-id="17dac-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="17dac-147">詳細については、次を参照してください。[省略可能なパラメーター](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)します。</span><span class="sxs-lookup"><span data-stu-id="17dac-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
-   <span data-ttu-id="17dac-148">**パラメーターの配列。**</span><span class="sxs-lookup"><span data-stu-id="17dac-148">**Parameter Arrays.**</span></span> <span data-ttu-id="17dac-149">指定する必要があります`ByVal`の`ParamArray`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="17dac-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="17dac-150">両方を使用することはできません`Optional`と`ParamArray`同じパラメーター リストにします。</span><span class="sxs-lookup"><span data-stu-id="17dac-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="17dac-151">詳細については、次を参照してください。[パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)します。</span><span class="sxs-lookup"><span data-stu-id="17dac-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
-   <span data-ttu-id="17dac-152">**値渡し。**</span><span class="sxs-lookup"><span data-stu-id="17dac-152">**Passing Mechanism.**</span></span> <span data-ttu-id="17dac-153">すべての引数に対して既定のメカニズムは`ByVal`プロシージャは基になる可変要素は変更できません。</span><span class="sxs-lookup"><span data-stu-id="17dac-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="17dac-154">ただし、要素が参照型の場合は、プロシージャが変更できます内容または基になるオブジェクトのメンバーでも置き換えることも、オブジェクト自体を再割り当てできません。</span><span class="sxs-lookup"><span data-stu-id="17dac-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
-   <span data-ttu-id="17dac-155">**パラメーター名。**</span><span class="sxs-lookup"><span data-stu-id="17dac-155">**Parameter Names.**</span></span> <span data-ttu-id="17dac-156">次のパラメーターのデータ型が配列の場合は、`parametername`かっこの直後にします。</span><span class="sxs-lookup"><span data-stu-id="17dac-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="17dac-157">パラメーター名の詳細については、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="17dac-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17dac-158">例</span><span class="sxs-lookup"><span data-stu-id="17dac-158">Example</span></span>  
 <span data-ttu-id="17dac-159">例を次に、 `Function`&2; つのパラメーターを定義するプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="17dac-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 <span data-ttu-id="17dac-160">[!code-vb[VbVbalrStatements&#2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="17dac-160">[!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17dac-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="17dac-161">See Also</span></span>  
 <span data-ttu-id="17dac-162"><xref:System.Runtime.InteropServices.DllImportAttribute></xref:System.Runtime.InteropServices.DllImportAttribute></span><span class="sxs-lookup"><span data-stu-id="17dac-162"><xref:System.Runtime.InteropServices.DllImportAttribute></span></span>   
<span data-ttu-id="17dac-163"> [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="17dac-163"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="17dac-164"> [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="17dac-164"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="17dac-165"> [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="17dac-165"> [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="17dac-166"> [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="17dac-166"> [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="17dac-167"> [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="17dac-167"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="17dac-168"> [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="17dac-168"> [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span></span>  
<span data-ttu-id="17dac-169"> [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="17dac-169"> [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)</span></span>
