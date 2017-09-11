---
title: "ステートメント (Visual Basic) の機能 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Function
dev_langs:
- VB
helpviewer_keywords:
- procedures, creating
- Function procedures, Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword, Function statements
- Private keyword, Function statements
- declarations, procedures
- procedures, declaration
- Public keyword, in Function statement
- ByVal keyword, Function statements
- procedures, recursive
- Implements keyword, Function statements
- procedures, returning values
- Exit statement, in Function procedures
- recursive procedures
- As keyword, in Function statement
- Optional keyword, Function statements
- Function statement
- Visual Basic code, Function procedures
- procedures, function
- ByRef keyword, Function statements
- Friend keyword, Function statements
- End keyword, Function statements
- Handles keyword, Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: 62
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
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: d875fe6df3ef7ac9390346588b1c2d48497d7116
ms.contentlocale: ja-jp
ms.lasthandoff: 05/15/2017

---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="32ade-102">Function ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32ade-102">Function Statement (Visual Basic)</span></span>
<span data-ttu-id="32ade-103">名前、パラメーター、および定義するコードを宣言して、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="32ade-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ade-104">構文</span><span class="sxs-lookup"><span data-stu-id="32ade-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="32ade-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="32ade-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="32ade-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-106">Optional.</span></span> <span data-ttu-id="32ade-107">参照してください[属性一覧](attribute-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="32ade-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-108">Optional.</span></span> <span data-ttu-id="32ade-109">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="32ade-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="32ade-110">Public</span><span class="sxs-lookup"><span data-stu-id="32ade-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="32ade-111">Protected</span><span class="sxs-lookup"><span data-stu-id="32ade-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="32ade-112">Friend</span><span class="sxs-lookup"><span data-stu-id="32ade-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="32ade-113">Private</span><span class="sxs-lookup"><span data-stu-id="32ade-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="32ade-114">参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-114">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="32ade-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-115">Optional.</span></span> <span data-ttu-id="32ade-116">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="32ade-116">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="32ade-117">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="32ade-117">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="32ade-118">Overrides</span><span class="sxs-lookup"><span data-stu-id="32ade-118">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="32ade-119">Overridable</span><span class="sxs-lookup"><span data-stu-id="32ade-119">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="32ade-120">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="32ade-120">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="32ade-121">MustOverride</span><span class="sxs-lookup"><span data-stu-id="32ade-121">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="32ade-122">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-122">Optional.</span></span> <span data-ttu-id="32ade-123">参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-123">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="32ade-124">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-124">Optional.</span></span> <span data-ttu-id="32ade-125">参照してください[シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-125">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="32ade-126">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-126">Optional.</span></span> <span data-ttu-id="32ade-127">参照してください[Async](../../../visual-basic/language-reference/modifiers/async.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-127">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="32ade-128">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-128">Optional.</span></span> <span data-ttu-id="32ade-129">参照してください[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-129">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="32ade-130">必須です。</span><span class="sxs-lookup"><span data-stu-id="32ade-130">Required.</span></span> <span data-ttu-id="32ade-131">プロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="32ade-131">Name of the procedure.</span></span> <span data-ttu-id="32ade-132">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-132">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="32ade-133">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-133">Optional.</span></span> <span data-ttu-id="32ade-134">手順については、ジェネリック型パラメーターの一覧です。</span><span class="sxs-lookup"><span data-stu-id="32ade-134">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="32ade-135">参照してください[のリストを入力](type-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-135">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="32ade-136">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-136">Optional.</span></span> <span data-ttu-id="32ade-137">このプロシージャのパラメーターを表すローカル変数名の一覧です。</span><span class="sxs-lookup"><span data-stu-id="32ade-137">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="32ade-138">参照してください[パラメーター リスト](parameter-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-138">See [Parameter List](parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="32ade-139">必要な場合`Option Strict`は`On`です。</span><span class="sxs-lookup"><span data-stu-id="32ade-139">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="32ade-140">このプロシージャによって返される値のデータ型。</span><span class="sxs-lookup"><span data-stu-id="32ade-140">Data type of the value returned by this procedure.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="32ade-141">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-141">Optional.</span></span> <span data-ttu-id="32ade-142">この手順が&1; つまたは複数を実装することを示します`Function`の手順は、この手順を含むクラスまたは構造体によって実装されるインターフェイスで定義されている&1; つずつです。</span><span class="sxs-lookup"><span data-stu-id="32ade-142">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="32ade-143">参照してください[ステートメントを実装します](implements-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-143">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="32ade-144">`Implements` を指定する場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="32ade-144">Required if `Implements` is supplied.</span></span> <span data-ttu-id="32ade-145">実装される `Function` プロシージャのリストです。</span><span class="sxs-lookup"><span data-stu-id="32ade-145">List of `Function` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="32ade-146">`implementedprocedure` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="32ade-146">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="32ade-147">パーツ</span><span class="sxs-lookup"><span data-stu-id="32ade-147">Part</span></span>|<span data-ttu-id="32ade-148">説明</span><span class="sxs-lookup"><span data-stu-id="32ade-148">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="32ade-149">必須です。</span><span class="sxs-lookup"><span data-stu-id="32ade-149">Required.</span></span> <span data-ttu-id="32ade-150">このプロシージャによって実装されるインターフェイスの名前には、クラスまたは構造体を含むのです。</span><span class="sxs-lookup"><span data-stu-id="32ade-150">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="32ade-151">必須です。</span><span class="sxs-lookup"><span data-stu-id="32ade-151">Required.</span></span> <span data-ttu-id="32ade-152">`interface` の中でプロシージャを定義するために使用する名前。</span><span class="sxs-lookup"><span data-stu-id="32ade-152">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="32ade-153">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-153">Optional.</span></span> <span data-ttu-id="32ade-154">この手順が&1; つまたは複数の特定のイベントを処理できることを示します。</span><span class="sxs-lookup"><span data-stu-id="32ade-154">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="32ade-155">参照してください[処理](handles-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-155">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="32ade-156">`Handles` を指定する場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="32ade-156">Required if `Handles` is supplied.</span></span> <span data-ttu-id="32ade-157">このプロシージャを処理するイベントのリスト。</span><span class="sxs-lookup"><span data-stu-id="32ade-157">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="32ade-158">`eventspecifier` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="32ade-158">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="32ade-159">パーツ</span><span class="sxs-lookup"><span data-stu-id="32ade-159">Part</span></span>|<span data-ttu-id="32ade-160">説明</span><span class="sxs-lookup"><span data-stu-id="32ade-160">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="32ade-161">必須です。</span><span class="sxs-lookup"><span data-stu-id="32ade-161">Required.</span></span> <span data-ttu-id="32ade-162">オブジェクト変数がクラスまたはイベントを発生させる構造体のデータ型で宣言します。</span><span class="sxs-lookup"><span data-stu-id="32ade-162">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="32ade-163">必須です。</span><span class="sxs-lookup"><span data-stu-id="32ade-163">Required.</span></span> <span data-ttu-id="32ade-164">このプロシージャを処理するイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="32ade-164">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="32ade-165">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32ade-165">Optional.</span></span> <span data-ttu-id="32ade-166">このプロシージャ内で実行されるステートメントのブロックです。</span><span class="sxs-lookup"><span data-stu-id="32ade-166">Block of statements to be executed within this procedure.</span></span>  
  
-   `End Function`  
  
     <span data-ttu-id="32ade-167">このプロシージャの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="32ade-167">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32ade-168">コメント</span><span class="sxs-lookup"><span data-stu-id="32ade-168">Remarks</span></span>  
 <span data-ttu-id="32ade-169">すべての実行可能コードは、プロシージャの中にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="32ade-169">All executable code must be inside a procedure.</span></span> <span data-ttu-id="32ade-170">さらに、各プロシージャは、クラス、構造体またはクラス、構造体、またはモジュールとして参照されているモジュール内で宣言されます。</span><span class="sxs-lookup"><span data-stu-id="32ade-170">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>  
  
 <span data-ttu-id="32ade-171">呼び出し元のコードに値を返すには使用、`Function`プロシージャです。 それ以外の場合、を使用して、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="32ade-171">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>  
  
## <a name="defining-a-function"></a><span data-ttu-id="32ade-172">関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="32ade-172">Defining a Function</span></span>  
 <span data-ttu-id="32ade-173">定義する、`Function`手順をモジュール レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="32ade-173">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="32ade-174">そのため、関数の宣言コンテキストを使用して、クラス、構造体、モジュールの場合、またはインターフェイスがあります、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="32ade-174">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="32ade-175">詳細については、次を参照してください。[宣言コンテキストとアクセス レベルの既定の](declaration-contexts-and-default-access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="32ade-175">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="32ade-176">`Function`パブリック アクセスを既定値をプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="32ade-176">`Function` procedures default to public access.</span></span> <span data-ttu-id="32ade-177">アクセス修飾子を使用してこれらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="32ade-177">You can adjust their access levels with the access modifiers.</span></span>  
  
 <span data-ttu-id="32ade-178">A`Function`プロシージャがプロシージャが返す値のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="32ade-178">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="32ade-179">任意のデータ型または列挙体、構造体、クラスまたはインターフェイスの名前を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="32ade-179">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="32ade-180">指定しない場合、`returntype`プロシージャは、パラメーターを返します`Object`します。</span><span class="sxs-lookup"><span data-stu-id="32ade-180">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>  
  
 <span data-ttu-id="32ade-181">この手順で使用する場合、`Implements`キーワードを含むクラスまたは構造体があります、`Implements`直後に続くステートメントの`Class`または`Structure`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="32ade-181">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="32ade-182">`Implements`ステートメントで指定されている各インターフェイスを含める必要があります`implementslist`します。</span><span class="sxs-lookup"><span data-stu-id="32ade-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="32ade-183">ただし、インターフェイスを定義する名前、 `Function` (で`definedname`) このプロシージャの名前と一致する必要はありません (で`name`)。</span><span class="sxs-lookup"><span data-stu-id="32ade-183">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32ade-184">ラムダ式を使用すると、関数の式のインラインを定義します。</span><span class="sxs-lookup"><span data-stu-id="32ade-184">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="32ade-185">詳細については、次を参照してください。[関数式](../../../visual-basic/language-reference/operators/function-expression.md)と[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-185">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="returning-from-a-function"></a><span data-ttu-id="32ade-186">関数から戻る</span><span class="sxs-lookup"><span data-stu-id="32ade-186">Returning from a Function</span></span>  
 <span data-ttu-id="32ade-187">ときに、`Function`プロシージャを呼び出したステートメントに続くステートメントを使用して、プロシージャ呼び出し元のコードに戻ると、実行が継続します。</span><span class="sxs-lookup"><span data-stu-id="32ade-187">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>  
  
 <span data-ttu-id="32ade-188">関数から値を返す、関数名に値を割り当てるか、含めることで、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="32ade-188">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>  
  
 <span data-ttu-id="32ade-189">`Return`ステートメントは、同時に戻り値を割り当てるし、次の例のように、関数が終了します。</span><span class="sxs-lookup"><span data-stu-id="32ade-189">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>  
  
 <span data-ttu-id="32ade-190">[!code-vb[VbVbalrStatements #&24;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="32ade-190">[!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="32ade-191">次の例では、戻り値を割り当てて、関数名に`myFunction`し、使用して、`Exit Function`を返すステートメントです。</span><span class="sxs-lookup"><span data-stu-id="32ade-191">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>  
  
 <span data-ttu-id="32ade-192">[!code-vb[VbVbalrStatements 第&23;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="32ade-192">[!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]</span></span>  
  
 <span data-ttu-id="32ade-193">`Exit Function`と`Return`ステートメントからすぐに終了が発生する、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="32ade-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="32ade-194">任意の数の`Exit Function`と`Return`ステートメントが任意の場所で、手順と混在させることが`Exit Function`と`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="32ade-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>  
  
 <span data-ttu-id="32ade-195">使用する場合`Exit Function`、値を割り当てることがなく`name`で指定されているデータ型の既定値を返し`returntype`します。</span><span class="sxs-lookup"><span data-stu-id="32ade-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="32ade-196">場合`returntype`を返し、指定されていない`Nothing`の既定値は`Object`です。</span><span class="sxs-lookup"><span data-stu-id="32ade-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>  
  
## <a name="calling-a-function"></a><span data-ttu-id="32ade-197">関数を呼び出す</span><span class="sxs-lookup"><span data-stu-id="32ade-197">Calling a Function</span></span>  
 <span data-ttu-id="32ade-198">呼び出す、`Function`プロシージャ名、式の中で、かっこで囲まれた引数のリストを使用してプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="32ade-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="32ade-199">すべての引数を指定していない場合にのみ、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="32ade-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="32ade-200">ただし、コードは常にかっこを含める場合は、読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="32ade-200">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="32ade-201">呼び出す、`Function`プロシージャなどの任意のライブラリを呼び出すことと同様の関数`Sqrt`、 `Cos`、または`ChrW`です。</span><span class="sxs-lookup"><span data-stu-id="32ade-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>  
  
 <span data-ttu-id="32ade-202">使用して関数を呼び出すことができます、`Call`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="32ade-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="32ade-203">その場合は、戻り値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="32ade-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="32ade-204">使用、`Call`キーワードは、ほとんどの場合にお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="32ade-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="32ade-205">詳細については、次を参照してください。 [Call ステートメント](call-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-205">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="32ade-206">Visual Basic では、算術式内部の効率を向上させることがあります再配置します。</span><span class="sxs-lookup"><span data-stu-id="32ade-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="32ade-207">そのため、使用しないでください、`Function`算術式、関数には、同じ式内の変数の値が変更されたときの手順です。</span><span class="sxs-lookup"><span data-stu-id="32ade-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>  
  
## <a name="async-functions"></a><span data-ttu-id="32ade-208">Async 関数</span><span class="sxs-lookup"><span data-stu-id="32ade-208">Async Functions</span></span>  
 <span data-ttu-id="32ade-209">*Async*機能は、明示的なコールバックの使用や複数の関数やラムダ式で、コードを手動で分割を行わず、非同期関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="32ade-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="32ade-210">持つ関数をマークした場合、 [Async](../../../visual-basic/language-reference/modifiers/async.md)修飾子は、使用できます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)関数内の演算子です。</span><span class="sxs-lookup"><span data-stu-id="32ade-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="32ade-211">達するとを制御すると、`Await`内の式、`Async`関数は、呼び出し元に制御が戻るし、関数で進展が待機中のタスクが完了するまでです。</span><span class="sxs-lookup"><span data-stu-id="32ade-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="32ade-212">タスクが完了すると、関数の実行を再開できます。</span><span class="sxs-lookup"><span data-stu-id="32ade-212">When the task is complete, execution can resume in the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32ade-213">`Async`がまだ完了していない最初の待機中のオブジェクトを検出するかとプロシージャを呼び出し元に返しますまたはの最後に、`Async`プロシージャか早い方です。</span><span class="sxs-lookup"><span data-stu-id="32ade-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>  
  
 <span data-ttu-id="32ade-214">`Async`関数<xref:System.Threading.Tasks.Task%601>または<xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task></xref:System.Threading.Tasks.Task%601>の戻り値の型を設定できます</span><span class="sxs-lookup"><span data-stu-id="32ade-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="32ade-215">例、`Async`関数の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>を次に示します</xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="32ade-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>  
  
 <span data-ttu-id="32ade-216">`Async`関数は、いずれかを宣言できません[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)パラメーター。</span><span class="sxs-lookup"><span data-stu-id="32ade-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="32ade-217">A [Sub ステートメント](sub-statement.md)でマークできるも、`Async`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="32ade-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="32ade-218">これは主に使用、イベント ハンドラーの値が返されることはできません。</span><span class="sxs-lookup"><span data-stu-id="32ade-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="32ade-219">`Async``Sub`プロシージャを待機することはできないと、呼び出し元の`Async``Sub`プロシージャによってスローされる例外をキャッチできません、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="32ade-219">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>  
  
 <span data-ttu-id="32ade-220">詳細については`Async`関数を参照してください[Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同期プログラムにおける制御のフロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)、および[Async を返す型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="32ade-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="iterator-functions"></a><span data-ttu-id="32ade-221">反復子関数</span><span class="sxs-lookup"><span data-stu-id="32ade-221">Iterator Functions</span></span>  
 <span data-ttu-id="32ade-222">*反復子*関数は、リストや配列などのコレクションに対するカスタムの反復を実行します。</span><span class="sxs-lookup"><span data-stu-id="32ade-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="32ade-223">Iterator 関数を使用して、 [Yield](yield-statement.md)ステートメントを一度に&1; つの各要素を返します。</span><span class="sxs-lookup"><span data-stu-id="32ade-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="32ade-224">ときに、 [Yield](yield-statement.md)ステートメントに達すると、コード内の現在位置が記憶されます。</span><span class="sxs-lookup"><span data-stu-id="32ade-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="32ade-225">次回の反復子関数が呼び出されたとき、その場所から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="32ade-225">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="32ade-226">使用して、クライアント コードから反復子を呼び出す、[ごとにしています.次](for-each-next-statement.md)ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="32ade-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>  
  
 <span data-ttu-id="32ade-227">反復子関数の戻り値の型を指定できます<xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または<xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="32ade-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="32ade-228">詳細については、「[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32ade-228">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32ade-229">例</span><span class="sxs-lookup"><span data-stu-id="32ade-229">Example</span></span>  
 <span data-ttu-id="32ade-230">次の例では、`Function`を名前、パラメーター、およびコードの本体を形成する宣言ステートメント、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="32ade-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="32ade-231">`ParamArray`修飾子により、可変個の引数を受け入れるように機能します。</span><span class="sxs-lookup"><span data-stu-id="32ade-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>  
  
 <span data-ttu-id="32ade-232">[!code-vb[VbVbalrStatements&#25;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="32ade-232">[!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="32ade-233">例</span><span class="sxs-lookup"><span data-stu-id="32ade-233">Example</span></span>  
 <span data-ttu-id="32ade-234">次の例では、前の例で宣言された関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="32ade-234">The following example invokes the function declared in the preceding example.</span></span>  
  
 <span data-ttu-id="32ade-235">[!code-vb[VbVbalrStatements #&26;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="32ade-235">[!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="32ade-236">例</span><span class="sxs-lookup"><span data-stu-id="32ade-236">Example</span></span>  
 <span data-ttu-id="32ade-237">次の例で`DelayAsync`は、 `Async``Function` <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601>の戻り値の型を持つ</span><span class="sxs-lookup"><span data-stu-id="32ade-237">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="32ade-238">`DelayAsync` には、整数を返す `Return` ステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="32ade-238">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="32ade-239">したがって、関数宣言の`DelayAsync`の戻り値の型を持っている必要がある`Task(Of Integer)`です。</span><span class="sxs-lookup"><span data-stu-id="32ade-239">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="32ade-240">戻り値の型である`Task(Of Integer)`の評価、`Await`式`DoSomethingAsync`整数値を生成します。</span><span class="sxs-lookup"><span data-stu-id="32ade-240">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="32ade-241">これを次のステートメントに示します:`Dim result As Integer = Await delayTask`です。</span><span class="sxs-lookup"><span data-stu-id="32ade-241">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="32ade-242">`startButton_Click`手順の例は、`Async Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="32ade-242">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="32ade-243">`DoSomethingAsync`は、`Async`関数への呼び出しのタスク`DoSomethingAsync`、次のステートメントで示すように、待機する必要があります:`Await DoSomethingAsync()`です。</span><span class="sxs-lookup"><span data-stu-id="32ade-243">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="32ade-244">`startButton_Click``Sub`でプロシージャを定義する必要があります、`Async`修飾子があるため、`Await`式です。</span><span class="sxs-lookup"><span data-stu-id="32ade-244">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 <span data-ttu-id="32ade-245">[!code-vb[csAsyncMethod&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="32ade-245">[!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ade-246">関連項目</span><span class="sxs-lookup"><span data-stu-id="32ade-246">See Also</span></span>  
 <span data-ttu-id="32ade-247">[Sub ステートメント](sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="32ade-247">[Sub Statement](sub-statement.md) </span></span>  
<span data-ttu-id="32ade-248"> [Function プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="32ade-248"> [Function Procedures](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) </span></span>  
<span data-ttu-id="32ade-249"> [パラメーター リスト](parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="32ade-249"> [Parameter List](parameter-list.md) </span></span>  
<span data-ttu-id="32ade-250"> [Dim ステートメント](dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="32ade-250"> [Dim Statement](dim-statement.md) </span></span>  
<span data-ttu-id="32ade-251"> [Call ステートメント](call-statement.md) </span><span class="sxs-lookup"><span data-stu-id="32ade-251"> [Call Statement](call-statement.md) </span></span>  
<span data-ttu-id="32ade-252"> [Of](of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="32ade-252"> [Of](of-clause.md) </span></span>  
<span data-ttu-id="32ade-253"> [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="32ade-253"> [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span></span>  
<span data-ttu-id="32ade-254"> [方法: ジェネリック クラスを使用して](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="32ade-254"> [How to: Use a Generic Class](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="32ade-255"> [トラブルシューティングの手順](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="32ade-255"> [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="32ade-256"> [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="32ade-256"> [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="32ade-257"> [Function 式](../../../visual-basic/language-reference/operators/function-expression.md)</span><span class="sxs-lookup"><span data-stu-id="32ade-257"> [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md)</span></span>

