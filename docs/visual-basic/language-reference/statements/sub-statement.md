---
title: "Sub ステートメント (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Sub
dev_langs:
- VB
helpviewer_keywords:
- Public keyword, Sub statements
- procedures, creating
- declaring procedures, Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword, Sub statements
- Optional keyword, Sub statements
- declarations, procedures
- Sub keyword
- Handles keyword, Sub statements
- Protected Friend keyword
- ParamArray keyword, Sub statements
- Implements keyword, Sub statements
- Sub statement
- subroutines
- ByRef keyword, Sub statements
- Sub procedures, Sub statement
- recursive procedures
- Private keyword, Sub statements
- Friend keyword, Sub statements
- Exit statement, Sub statements
- procedures, Sub
- End keyword, Sub statements
- ByVal keyword, Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
caps.latest.revision: 52
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
ms.openlocfilehash: 61853a4f2321837683997b8e4241b688bc9f622c
ms.contentlocale: ja-jp
ms.lasthandoff: 05/15/2017

---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="7db9c-102">Sub ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7db9c-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="7db9c-103">名前、パラメーター、および定義するコードを宣言して、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7db9c-104">構文</span><span class="sxs-lookup"><span data-stu-id="7db9c-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="7db9c-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="7db9c-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="7db9c-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-106">Optional.</span></span> <span data-ttu-id="7db9c-107">参照してください[属性一覧](attribute-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="7db9c-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-108">Optional.</span></span> <span data-ttu-id="7db9c-109">部分メソッドの定義を示します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="7db9c-110">参照してください[部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="7db9c-111">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-111">Optional.</span></span> <span data-ttu-id="7db9c-112">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="7db9c-113">Public</span><span class="sxs-lookup"><span data-stu-id="7db9c-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="7db9c-114">Protected</span><span class="sxs-lookup"><span data-stu-id="7db9c-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="7db9c-115">Friend</span><span class="sxs-lookup"><span data-stu-id="7db9c-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="7db9c-116">Private</span><span class="sxs-lookup"><span data-stu-id="7db9c-116">Private</span></span>](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="7db9c-117">参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-117">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="7db9c-118">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-118">Optional.</span></span> <span data-ttu-id="7db9c-119">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-119">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="7db9c-120">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="7db9c-120">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="7db9c-121">Overrides</span><span class="sxs-lookup"><span data-stu-id="7db9c-121">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="7db9c-122">Overridable</span><span class="sxs-lookup"><span data-stu-id="7db9c-122">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="7db9c-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="7db9c-123">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="7db9c-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="7db9c-124">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="7db9c-125">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-125">Optional.</span></span> <span data-ttu-id="7db9c-126">参照してください[共有](../modifiers/shared.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-126">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="7db9c-127">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-127">Optional.</span></span> <span data-ttu-id="7db9c-128">参照してください[シャドウ](../modifiers/shadows.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-128">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="7db9c-129">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-129">Optional.</span></span> <span data-ttu-id="7db9c-130">参照してください[Async](../modifiers/async.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-130">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="7db9c-131">必須です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-131">Required.</span></span> <span data-ttu-id="7db9c-132">プロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="7db9c-132">Name of the procedure.</span></span> <span data-ttu-id="7db9c-133">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-133">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="7db9c-134">クラスのコンス トラクターのプロシージャを作成するには、設定の名前、`Sub`する手順、`New`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-134">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="7db9c-135">詳細については、次を参照してください。[オブジェクトの有効期間: オブジェクトが作成と破棄方法](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-135">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="7db9c-136">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-136">Optional.</span></span> <span data-ttu-id="7db9c-137">手順については、ジェネリック型パラメーターの一覧です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-137">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="7db9c-138">参照してください[のリストを入力](type-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-138">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="7db9c-139">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-139">Optional.</span></span> <span data-ttu-id="7db9c-140">このプロシージャのパラメーターを表すローカル変数名の一覧です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-140">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="7db9c-141">参照してください[パラメーター リスト](parameter-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-141">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="7db9c-142">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-142">Optional.</span></span> <span data-ttu-id="7db9c-143">この手順が&1; つまたは複数を実装することを示します`Sub`の手順は、この手順を含むクラスまたは構造体によって実装されるインターフェイスで定義されている&1; つずつです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-143">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="7db9c-144">参照してください[ステートメントを実装します](implements-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-144">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="7db9c-145">`Implements` を指定する場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-145">Required if `Implements` is supplied.</span></span> <span data-ttu-id="7db9c-146">実装される `Sub` プロシージャのリストです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-146">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="7db9c-147">`implementedprocedure` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-147">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="7db9c-148">パーツ</span><span class="sxs-lookup"><span data-stu-id="7db9c-148">Part</span></span>|<span data-ttu-id="7db9c-149">説明</span><span class="sxs-lookup"><span data-stu-id="7db9c-149">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="7db9c-150">必須です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-150">Required.</span></span> <span data-ttu-id="7db9c-151">このプロシージャによって実装されるインターフェイスの名前には、クラスまたは構造体を含むのです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-151">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="7db9c-152">必須です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-152">Required.</span></span> <span data-ttu-id="7db9c-153">`interface` の中でプロシージャを定義するために使用する名前。</span><span class="sxs-lookup"><span data-stu-id="7db9c-153">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="7db9c-154">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-154">Optional.</span></span> <span data-ttu-id="7db9c-155">この手順が&1; つまたは複数の特定のイベントを処理できることを示します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-155">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="7db9c-156">参照してください[処理](handles-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-156">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="7db9c-157">`Handles` を指定する場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-157">Required if `Handles` is supplied.</span></span> <span data-ttu-id="7db9c-158">このプロシージャを処理するイベントのリスト。</span><span class="sxs-lookup"><span data-stu-id="7db9c-158">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="7db9c-159">`eventspecifier` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-159">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="7db9c-160">パーツ</span><span class="sxs-lookup"><span data-stu-id="7db9c-160">Part</span></span>|<span data-ttu-id="7db9c-161">説明</span><span class="sxs-lookup"><span data-stu-id="7db9c-161">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="7db9c-162">必須です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-162">Required.</span></span> <span data-ttu-id="7db9c-163">オブジェクト変数がクラスまたはイベントを発生させる構造体のデータ型で宣言します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-163">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="7db9c-164">必須です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-164">Required.</span></span> <span data-ttu-id="7db9c-165">このプロシージャを処理するイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="7db9c-165">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="7db9c-166">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-166">Optional.</span></span> <span data-ttu-id="7db9c-167">このプロシージャ内で実行するステートメントのブロックです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-167">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="7db9c-168">このプロシージャの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-168">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7db9c-169">コメント</span><span class="sxs-lookup"><span data-stu-id="7db9c-169">Remarks</span></span>  
 <span data-ttu-id="7db9c-170">すべての実行可能コードは、プロシージャの中にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7db9c-170">All executable code must be inside a procedure.</span></span> <span data-ttu-id="7db9c-171">使用して、`Sub`プロシージャは、呼び出し元のコードに値を返すしたくない場合。</span><span class="sxs-lookup"><span data-stu-id="7db9c-171">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="7db9c-172">使用して、`Function`プロシージャは、値を取得する場合。</span><span class="sxs-lookup"><span data-stu-id="7db9c-172">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="7db9c-173">Sub プロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="7db9c-173">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="7db9c-174">定義する、`Sub`手順をモジュール レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-174">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="7db9c-175">Sub プロシージャの宣言コンテキストは、そのため、必要があります、クラス、構造体、モジュールの場合、またはインターフェイスとソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7db9c-175">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="7db9c-176">詳細については、次を参照してください。[宣言コンテキストとアクセス レベルの既定の](declaration-contexts-and-default-access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-176">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="7db9c-177">`Sub`パブリック アクセスを既定値をプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-177">`Sub` procedures default to public access.</span></span> <span data-ttu-id="7db9c-178">アクセス修飾子を使用して、これらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="7db9c-178">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="7db9c-179">プロシージャで使用する場合、`Implements`キーワードを含むクラスまたは構造体が必要、`Implements`直後に続くステートメントの`Class`または`Structure`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-179">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="7db9c-180">`Implements`ステートメントで指定されている各インターフェイスを含める必要があります`implementslist`します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-180">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="7db9c-181">ただし、インターフェイスを定義する名前、 `Sub` (で`definedname`) このプロシージャの名前と一致する必要はありません (で`name`)。</span><span class="sxs-lookup"><span data-stu-id="7db9c-181">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="7db9c-182">Sub プロシージャから返す処理</span><span class="sxs-lookup"><span data-stu-id="7db9c-182">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="7db9c-183">ときに、`Sub`その呼び出し元ステートメントの後にステートメントを使用して、プロシージャ呼び出し元のコードに戻ると、実行が継続します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-183">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="7db9c-184">次の例から戻るとき、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-184">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="7db9c-185">`Exit Sub`と`Return`ステートメントからすぐに終了が発生する、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-185">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="7db9c-186">任意の数の`Exit Sub`と`Return`ステートメントが任意の場所で、手順と混在させることが`Exit Sub`と`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-186">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="7db9c-187">Sub プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="7db9c-187">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="7db9c-188">呼び出す、`Sub`をステートメントで、プロシージャ名を使用し、かっこで囲まれた、引数リストでその名前を次の手順です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-188">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="7db9c-189">すべての引数を指定しない場合にのみ、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="7db9c-189">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="7db9c-190">ただし、コードが読みやすく、かっこを挿入する場合です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-190">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="7db9c-191">A`Sub`プロシージャと`Function`プロシージャはパラメーターを持つし、一連のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-191">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="7db9c-192">ただし、`Function`値、およびプロシージャを返します。`Sub`プロシージャがありません。</span><span class="sxs-lookup"><span data-stu-id="7db9c-192">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="7db9c-193">したがって、使用することはできません、`Sub`式」の手順です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-193">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="7db9c-194">使用することができます、`Call`キーワードを呼び出したときに、`Sub`プロシージャが、そのキーワードは、ほとんどの用途をお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="7db9c-194">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="7db9c-195">詳細については、次を参照してください。 [Call ステートメント](call-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-195">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="7db9c-196">Visual Basic では、算術式内部の効率を向上させることがあります再配置します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-196">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="7db9c-197">そのため、引数リストには、その他のプロシージャを呼び出す式が含まれている場合を前提にしないでこれらの式が特定の順序で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="7db9c-197">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="7db9c-198">Async Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="7db9c-198">Async Sub Procedures</span></span>  
 <span data-ttu-id="7db9c-199">非同期機能を使用すると、明示的なコールバックの使用や複数の関数やラムダ式で、コードを手動で分割を行わず非同期関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7db9c-199">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="7db9c-200">使用してプロシージャをマークした場合、 [Async](../modifiers/async.md)修飾子は、使用できます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)プロシージャ内の演算子です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-200">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="7db9c-201">達するとを制御すると、`Await`内の式、`Async`手順が、呼び出し元に制御が戻るし、待機中のタスクが完了するまでの手順で進行状況が中断します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-201">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="7db9c-202">タスクが完了したら、プロシージャの実行を再開できます。</span><span class="sxs-lookup"><span data-stu-id="7db9c-202">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7db9c-203">`Async`のいずれか最初待機中のオブジェクトが完了していないことが検出された場合、呼び出し元へを返し、`Async`プロシージャに達すると、どちらかがします。</span><span class="sxs-lookup"><span data-stu-id="7db9c-203">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="7db9c-204">マークすることも、 [Function ステートメント](function-statement.md)で、`Async`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-204">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="7db9c-205">`Async`関数<xref:System.Threading.Tasks.Task%601>または<xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task></xref:System.Threading.Tasks.Task%601>の戻り値の型を設定できます</span><span class="sxs-lookup"><span data-stu-id="7db9c-205">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="7db9c-206">例を後で、このトピックでは、 `Async` <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601>の戻り値の型を持つ関数</span><span class="sxs-lookup"><span data-stu-id="7db9c-206">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="7db9c-207">`Async``Sub`プロシージャは、主に使用、イベント ハンドラーの値が返されることはできません。</span><span class="sxs-lookup"><span data-stu-id="7db9c-207">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="7db9c-208">`Async``Sub`プロシージャを待機することはできないと、呼び出し元の`Async``Sub`プロシージャは、例外をキャッチできませんを`Sub`プロシージャがスローされます。</span><span class="sxs-lookup"><span data-stu-id="7db9c-208">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="7db9c-209">`Async`プロシージャは、いずれかを宣言できません[ByRef](../modifiers/byref.md)パラメーター。</span><span class="sxs-lookup"><span data-stu-id="7db9c-209">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="7db9c-210">詳細については`Async`の手順を参照してください[Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同期プログラムにおける制御のフロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)、および[Async を返す型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-210">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7db9c-211">例</span><span class="sxs-lookup"><span data-stu-id="7db9c-211">Example</span></span>  
 <span data-ttu-id="7db9c-212">次の例では、`Sub`名、パラメーター、およびの本体を形成するコードを定義するステートメント、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-212">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="7db9c-213">[!code-vb[VbVbalrStatements #&58;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7db9c-213">[!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7db9c-214">例</span><span class="sxs-lookup"><span data-stu-id="7db9c-214">Example</span></span>  
 <span data-ttu-id="7db9c-215">次の例で`DelayAsync`、 `Async``Function` <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601>の戻り値の型を持つ</span><span class="sxs-lookup"><span data-stu-id="7db9c-215">In the following example, `DelayAsync` is an an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="7db9c-216">`DelayAsync` には、整数を返す `Return` ステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="7db9c-216">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="7db9c-217">したがって、関数宣言の`DelayAsync`の戻り値の型を持つ必要があります`Task(Of Integer)`します。</span><span class="sxs-lookup"><span data-stu-id="7db9c-217">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="7db9c-218">戻り値の型である`Task(Of Integer)`の評価、`Await`式`DoSomethingAsync`として次のステートメントに示す整数を生成する:`Dim result As Integer = Await delayTask`です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-218">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="7db9c-219">`startButton_Click`手順の例は、`Async Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="7db9c-219">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="7db9c-220">`DoSomethingAsync`は、`Async`関数への呼び出しのタスク`DoSomethingAsync`として次のステートメントに示す、待機する必要があります:`Await DoSomethingAsync()`です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-220">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="7db9c-221">`startButton_Click``Sub`でプロシージャを定義する必要があります、`Async`修飾子があるため、`Await`式です。</span><span class="sxs-lookup"><span data-stu-id="7db9c-221">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 <span data-ttu-id="7db9c-222">[!code-vb[csAsyncMethod&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7db9c-222">[!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db9c-223">関連項目</span><span class="sxs-lookup"><span data-stu-id="7db9c-223">See Also</span></span>  
 <span data-ttu-id="7db9c-224">[Implements ステートメント](implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7db9c-224">[Implements Statement](implements-statement.md) </span></span>  
<span data-ttu-id="7db9c-225"> [Function ステートメント](function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7db9c-225"> [Function Statement](function-statement.md) </span></span>  
<span data-ttu-id="7db9c-226"> [パラメーター リスト](parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="7db9c-226"> [Parameter List](parameter-list.md) </span></span>  
<span data-ttu-id="7db9c-227"> [Dim ステートメント](dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7db9c-227"> [Dim Statement](dim-statement.md) </span></span>  
<span data-ttu-id="7db9c-228"> [Call ステートメント](call-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7db9c-228"> [Call Statement](call-statement.md) </span></span>  
<span data-ttu-id="7db9c-229"> [Of](of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="7db9c-229"> [Of](of-clause.md) </span></span>  
<span data-ttu-id="7db9c-230"> [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="7db9c-230"> [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span></span>  
<span data-ttu-id="7db9c-231"> [方法: ジェネリック クラスを使用して](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="7db9c-231"> [How to: Use a Generic Class](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="7db9c-232"> [トラブルシューティングの手順](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7db9c-232"> [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="7db9c-233"> [部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)</span><span class="sxs-lookup"><span data-stu-id="7db9c-233"> [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)</span></span>

