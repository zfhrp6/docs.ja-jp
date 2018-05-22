---
title: Sub ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 08be38cdbec82914b567ab5b86eed71181efcf57
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="de237-102">Sub ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de237-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="de237-103">宣言名、パラメーター、およびコードを定義する、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="de237-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de237-104">構文</span><span class="sxs-lookup"><span data-stu-id="de237-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="de237-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="de237-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="de237-106">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-106">Optional.</span></span> <span data-ttu-id="de237-107">参照してください[属性一覧](attribute-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="de237-108">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-108">Optional.</span></span> <span data-ttu-id="de237-109">部分メソッドの定義を示します。</span><span class="sxs-lookup"><span data-stu-id="de237-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="de237-110">参照してください[部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="de237-111">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-111">Optional.</span></span> <span data-ttu-id="de237-112">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="de237-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="de237-113">Public</span><span class="sxs-lookup"><span data-stu-id="de237-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="de237-114">Protected</span><span class="sxs-lookup"><span data-stu-id="de237-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="de237-115">Friend</span><span class="sxs-lookup"><span data-stu-id="de237-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="de237-116">Private</span><span class="sxs-lookup"><span data-stu-id="de237-116">Private</span></span>](../modifiers/private.md)  
  
    - [<span data-ttu-id="de237-117">保護されたフレンド</span><span class="sxs-lookup"><span data-stu-id="de237-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="de237-118">保護されたプライベート</span><span class="sxs-lookup"><span data-stu-id="de237-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="de237-119">参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="de237-120">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-120">Optional.</span></span> <span data-ttu-id="de237-121">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="de237-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="de237-122">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="de237-122">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="de237-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="de237-123">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="de237-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="de237-124">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="de237-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="de237-125">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="de237-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="de237-126">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="de237-127">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-127">Optional.</span></span> <span data-ttu-id="de237-128">参照してください[共有](../modifiers/shared.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-128">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="de237-129">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-129">Optional.</span></span> <span data-ttu-id="de237-130">参照してください[Shadows](../modifiers/shadows.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-130">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="de237-131">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-131">Optional.</span></span> <span data-ttu-id="de237-132">参照してください[Async](../modifiers/async.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-132">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="de237-133">必須。</span><span class="sxs-lookup"><span data-stu-id="de237-133">Required.</span></span> <span data-ttu-id="de237-134">プロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="de237-134">Name of the procedure.</span></span> <span data-ttu-id="de237-135">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="de237-136">クラスのコンス トラクターのプロシージャを作成するには、名前を設定、`Sub`する手順、`New`キーワード。</span><span class="sxs-lookup"><span data-stu-id="de237-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="de237-137">詳細については、次を参照してください。[オブジェクトの有効期間: オブジェクトが作成と破棄にはどのように](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="de237-138">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-138">Optional.</span></span> <span data-ttu-id="de237-139">ジェネリック プロシージャの型パラメーターの一覧です。</span><span class="sxs-lookup"><span data-stu-id="de237-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="de237-140">参照してください[のリストを入力](type-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-140">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="de237-141">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-141">Optional.</span></span> <span data-ttu-id="de237-142">このプロシージャのパラメーターを表すローカル変数名の一覧です。</span><span class="sxs-lookup"><span data-stu-id="de237-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="de237-143">参照してください[パラメーター リスト](parameter-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-143">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="de237-144">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-144">Optional.</span></span> <span data-ttu-id="de237-145">この手順には、1 つまたは複数が実装されていることを示します`Sub`プロシージャ、このプロシージャの包含クラスまたは構造体によって実装されるインターフェイスで定義されている 1 つずつです。</span><span class="sxs-lookup"><span data-stu-id="de237-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="de237-146">参照してください[ステートメントを実装します](implements-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-146">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="de237-147">`Implements` を指定する場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="de237-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="de237-148">実装される `Sub` プロシージャのリストです。</span><span class="sxs-lookup"><span data-stu-id="de237-148">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="de237-149">`implementedprocedure` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="de237-149">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="de237-150">パーツ</span><span class="sxs-lookup"><span data-stu-id="de237-150">Part</span></span>|<span data-ttu-id="de237-151">説明</span><span class="sxs-lookup"><span data-stu-id="de237-151">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="de237-152">必須。</span><span class="sxs-lookup"><span data-stu-id="de237-152">Required.</span></span> <span data-ttu-id="de237-153">このプロシージャによって実装されるインターフェイスの名前には、クラスまたは構造体を含むのです。</span><span class="sxs-lookup"><span data-stu-id="de237-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="de237-154">必須。</span><span class="sxs-lookup"><span data-stu-id="de237-154">Required.</span></span> <span data-ttu-id="de237-155">`interface` の中でプロシージャを定義するために使用する名前。</span><span class="sxs-lookup"><span data-stu-id="de237-155">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="de237-156">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-156">Optional.</span></span> <span data-ttu-id="de237-157">この手順が 1 つまたは複数の特定のイベントを処理できることを示します。</span><span class="sxs-lookup"><span data-stu-id="de237-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="de237-158">参照してください[処理](handles-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-158">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="de237-159">`Handles` を指定する場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="de237-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="de237-160">このプロシージャを処理するイベントの一覧です。</span><span class="sxs-lookup"><span data-stu-id="de237-160">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="de237-161">`eventspecifier` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="de237-161">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="de237-162">パーツ</span><span class="sxs-lookup"><span data-stu-id="de237-162">Part</span></span>|<span data-ttu-id="de237-163">説明</span><span class="sxs-lookup"><span data-stu-id="de237-163">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="de237-164">必須。</span><span class="sxs-lookup"><span data-stu-id="de237-164">Required.</span></span> <span data-ttu-id="de237-165">クラスまたはイベントを発生させる構造体のデータ型で宣言されたオブジェクト変数です。</span><span class="sxs-lookup"><span data-stu-id="de237-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="de237-166">必須。</span><span class="sxs-lookup"><span data-stu-id="de237-166">Required.</span></span> <span data-ttu-id="de237-167">このプロシージャを処理するイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="de237-167">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="de237-168">任意。</span><span class="sxs-lookup"><span data-stu-id="de237-168">Optional.</span></span> <span data-ttu-id="de237-169">このプロシージャ内で実行するステートメントのブロックです。</span><span class="sxs-lookup"><span data-stu-id="de237-169">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="de237-170">このプロシージャの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="de237-170">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de237-171">コメント</span><span class="sxs-lookup"><span data-stu-id="de237-171">Remarks</span></span>  
 <span data-ttu-id="de237-172">すべての実行可能コードは、プロシージャ内でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="de237-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="de237-173">使用して、`Sub`呼び出し元のコードに値を返すしたくない場合、そのプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="de237-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="de237-174">使用して、`Function`値を取得する場合、そのプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="de237-174">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="de237-175">Sub プロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="de237-175">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="de237-176">定義することができます、`Sub`手順モジュール レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="de237-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="de237-177">Sub プロシージャの宣言コンテキストは、そのため、必要があります、クラス、構造体、モジュールの場合、またはインターフェイスと、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="de237-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="de237-178">詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de237-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="de237-179">`Sub` パブリック アクセスにプロシージャの既定値です。</span><span class="sxs-lookup"><span data-stu-id="de237-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="de237-180">アクセス修飾子を使用して、これらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="de237-180">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="de237-181">プロシージャで使用する場合、`Implements`キーワードを含むクラスまたは構造体があります、`Implements`直後に続くステートメント、`Class`または`Structure`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="de237-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="de237-182">`Implements`ステートメントで指定されている各インターフェイスを含める必要があります`implementslist`です。</span><span class="sxs-lookup"><span data-stu-id="de237-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="de237-183">ただし、インターフェイスを定義する名前、 `Sub` (で`definedname`) このプロシージャの名前と一致する必要はありません (で`name`)。</span><span class="sxs-lookup"><span data-stu-id="de237-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="de237-184">Sub プロシージャから返す処理</span><span class="sxs-lookup"><span data-stu-id="de237-184">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="de237-185">ときに、`Sub`その呼び出し元ステートメントの後にステートメントを使用して、プロシージャ呼び出し元のコードに戻ると、実行が継続します。</span><span class="sxs-lookup"><span data-stu-id="de237-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="de237-186">次の例の戻り値を示しています、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="de237-186">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="de237-187">`Exit Sub`と`Return`ステートメントからすぐに終了が発生する、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="de237-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="de237-188">任意の数の`Exit Sub`と`Return`ステートメントがどこにでも表示、プロシージャとを混在させること`Exit Sub`と`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="de237-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="de237-189">Sub プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="de237-189">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="de237-190">呼び出す、`Sub`ステートメントで、プロシージャ名を使用し、かっこ内に、引数リストでその名前でプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="de237-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="de237-191">引数を指定しない場合にのみ、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="de237-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="de237-192">ただし、コードは、常にかっこを含める場合より読みやすいです。</span><span class="sxs-lookup"><span data-stu-id="de237-192">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="de237-193">A`Sub`プロシージャおよび`Function`プロシージャがパラメーターを持つし、一連のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="de237-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="de237-194">ただし、`Function`値、およびプロシージャを返します`Sub`プロシージャしません。</span><span class="sxs-lookup"><span data-stu-id="de237-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="de237-195">したがって、使用することはできません、`Sub`式」の手順です。</span><span class="sxs-lookup"><span data-stu-id="de237-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="de237-196">使用することができます、`Call`キーワードを呼び出すとき、`Sub`プロシージャが、そのキーワードはほとんどの用途をお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="de237-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="de237-197">詳細については、次を参照してください。 [Call ステートメント](call-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="de237-197">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="de237-198">Visual Basic では、算術式内部の効率を向上させることがあります再配置します。</span><span class="sxs-lookup"><span data-stu-id="de237-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="de237-199">そのため、引数リストには、他のプロシージャを呼び出す式が含まれている場合を前提にしないでそれらの式が特定の順序で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="de237-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="de237-200">Async Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="de237-200">Async Sub Procedures</span></span>  
 <span data-ttu-id="de237-201">非同期機能を使用すると、明示的なコールバックの使用や複数の関数やラムダ式で、コードを手動で分割を行わず非同期関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="de237-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="de237-202">使用するプロシージャをマークする場合、 [Async](../modifiers/async.md)修飾子、行うこともできます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)演算子プロシージャにします。</span><span class="sxs-lookup"><span data-stu-id="de237-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="de237-203">達するとを制御すると、`Await`内の式、`Async`プロシージャは、呼び出し元に制御が戻るし、待機中のタスクが完了するまでの手順で進行状況は中断します。</span><span class="sxs-lookup"><span data-stu-id="de237-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="de237-204">タスクが完了したら、プロシージャで実行を再開できます。</span><span class="sxs-lookup"><span data-stu-id="de237-204">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de237-205">`Async`プロシージャにどちらか最初待機中のオブジェクトが完了していないことが検出されたときに、呼び出し元のまたは末尾を返します、`Async`プロシージャに達すると、先に生じた方です。</span><span class="sxs-lookup"><span data-stu-id="de237-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="de237-206">マークすることも、[関数ステートメント](function-statement.md)で、`Async`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="de237-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="de237-207">`Async`関数の戻り値の型を持つことができます<xref:System.Threading.Tasks.Task%601>または<xref:System.Threading.Tasks.Task>です。</span><span class="sxs-lookup"><span data-stu-id="de237-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="de237-208">例を後でのこのトピックでは、`Async`関数の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>します。</span><span class="sxs-lookup"><span data-stu-id="de237-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="de237-209">`Async` `Sub` プロシージャは、主に、値が返されることはできません、イベント ハンドラーを使用します。</span><span class="sxs-lookup"><span data-stu-id="de237-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="de237-210">`Async``Sub`プロシージャを待機することはできませんとの呼び出し元、`Async``Sub`プロシージャは、例外をキャッチできませんを`Sub`プロシージャがスローされます。</span><span class="sxs-lookup"><span data-stu-id="de237-210">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="de237-211">`Async`プロシージャは、いずれかを宣言できません[ByRef](../modifiers/byref.md)パラメーター。</span><span class="sxs-lookup"><span data-stu-id="de237-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="de237-212">詳細については`Async`プロシージャを参照してください[Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同期プログラムにおける制御フロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)、および[Async 戻り値の型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="de237-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de237-213">例</span><span class="sxs-lookup"><span data-stu-id="de237-213">Example</span></span>  
 <span data-ttu-id="de237-214">次の例では、`Sub`を名前、パラメーター、およびの本体を構成するコードを定義するステートメント、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="de237-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="de237-215">例</span><span class="sxs-lookup"><span data-stu-id="de237-215">Example</span></span>  
 <span data-ttu-id="de237-216">次の例では、`DelayAsync`は、`Async``Function`の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>します。</span><span class="sxs-lookup"><span data-stu-id="de237-216">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="de237-217">`DelayAsync` には、整数を返す `Return` ステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="de237-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="de237-218">したがって、関数宣言の`DelayAsync`の戻り値の型を持つ必要があります`Task(Of Integer)`です。</span><span class="sxs-lookup"><span data-stu-id="de237-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="de237-219">戻り値の型があるため`Task(Of Integer)`の評価、`Await`式`DoSomethingAsync`ステートメントを次に示すように整数が生成されます:`Dim result As Integer = Await delayTask`です。</span><span class="sxs-lookup"><span data-stu-id="de237-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="de237-220">`startButton_Click`プロシージャは、の例、`Async Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="de237-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="de237-221">`DoSomethingAsync`は、`Async`関数では、タスクへの呼び出しを`DoSomethingAsync`ステートメントを次に示すように待機する必要があります:`Await DoSomethingAsync()`です。</span><span class="sxs-lookup"><span data-stu-id="de237-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="de237-222">`startButton_Click``Sub`でプロシージャを定義する必要があります、`Async`修飾子があるため、`Await`式。</span><span class="sxs-lookup"><span data-stu-id="de237-222">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="de237-223">関連項目</span><span class="sxs-lookup"><span data-stu-id="de237-223">See Also</span></span>  
 [<span data-ttu-id="de237-224">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="de237-224">Implements Statement</span></span>](implements-statement.md)  
 [<span data-ttu-id="de237-225">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="de237-225">Function Statement</span></span>](function-statement.md)  
 [<span data-ttu-id="de237-226">パラメーター リスト</span><span class="sxs-lookup"><span data-stu-id="de237-226">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="de237-227">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="de237-227">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="de237-228">Call ステートメント</span><span class="sxs-lookup"><span data-stu-id="de237-228">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="de237-229">Of</span><span class="sxs-lookup"><span data-stu-id="de237-229">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="de237-230">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="de237-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="de237-231">方法 : ジェネリック クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="de237-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="de237-232">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="de237-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="de237-233">部分メソッド</span><span class="sxs-lookup"><span data-stu-id="de237-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
