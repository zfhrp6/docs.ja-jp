---
title: Const ステートメント (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 720a465f1459b663a1fca2a48856f51762328459
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="const-statement-visual-basic"></a><span data-ttu-id="d160e-102">Const ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d160e-102">Const Statement (Visual Basic)</span></span>
<span data-ttu-id="d160e-103">宣言し、1 つまたは複数の定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="d160e-103">Declares and defines one or more constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d160e-104">構文</span><span class="sxs-lookup"><span data-stu-id="d160e-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a><span data-ttu-id="d160e-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="d160e-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="d160e-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d160e-106">Optional.</span></span> <span data-ttu-id="d160e-107">すべての定数に適用される属性の一覧は、このステートメントで宣言します。</span><span class="sxs-lookup"><span data-stu-id="d160e-107">List of attributes that apply to all the constants declared in this statement.</span></span> <span data-ttu-id="d160e-108">参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ ("`<`「と」`>`") です。</span><span class="sxs-lookup"><span data-stu-id="d160e-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="d160e-109">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d160e-109">Optional.</span></span> <span data-ttu-id="d160e-110">これらの定数にアクセスできるコードを指定するのにには、これを使用します。</span><span class="sxs-lookup"><span data-stu-id="d160e-110">Use this to specify what code can access these constants.</span></span> <span data-ttu-id="d160e-111">指定できます[パブリック](../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)、 `Protected Friend`、または[プライベート](../../../visual-basic/language-reference/modifiers/private.md)です。</span><span class="sxs-lookup"><span data-stu-id="d160e-111">Can be [Public](../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span>  
  
 `Shadows`  
 <span data-ttu-id="d160e-112">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d160e-112">Optional.</span></span> <span data-ttu-id="d160e-113">再宣言して、基底クラスのプログラミング要素を非表示にするには、これを使用します。</span><span class="sxs-lookup"><span data-stu-id="d160e-113">Use this to redeclare and hide a programming element in a base class.</span></span> <span data-ttu-id="d160e-114">参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。</span><span class="sxs-lookup"><span data-stu-id="d160e-114">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
 `constantlist`  
 <span data-ttu-id="d160e-115">必須です。</span><span class="sxs-lookup"><span data-stu-id="d160e-115">Required.</span></span> <span data-ttu-id="d160e-116">このステートメントで宣言されている定数の一覧です。</span><span class="sxs-lookup"><span data-stu-id="d160e-116">List of constants being declared in this statement.</span></span>  
  
 <span data-ttu-id="d160e-117">`constant` `[ ,` `constant` `... ]`</span><span class="sxs-lookup"><span data-stu-id="d160e-117">`constant` `[ ,` `constant` `... ]`</span></span>  
  
 <span data-ttu-id="d160e-118">`constant` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d160e-118">Each `constant` has the following syntax and parts:</span></span>  
  
 <span data-ttu-id="d160e-119">`constantname``[ As``datatype``] =``initializer`</span><span class="sxs-lookup"><span data-stu-id="d160e-119">`constantname` `[ As` `datatype` `] =` `initializer`</span></span>  
  
|<span data-ttu-id="d160e-120">パーツ</span><span class="sxs-lookup"><span data-stu-id="d160e-120">Part</span></span>|<span data-ttu-id="d160e-121">説明</span><span class="sxs-lookup"><span data-stu-id="d160e-121">Description</span></span>|  
|----------|-----------------|  
|`constantname`|<span data-ttu-id="d160e-122">必須です。</span><span class="sxs-lookup"><span data-stu-id="d160e-122">Required.</span></span> <span data-ttu-id="d160e-123">定数の名前です。</span><span class="sxs-lookup"><span data-stu-id="d160e-123">Name of the constant.</span></span> <span data-ttu-id="d160e-124">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="d160e-124">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`datatype`|<span data-ttu-id="d160e-125">場合は必須`Option Strict`は`On`します。</span><span class="sxs-lookup"><span data-stu-id="d160e-125">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="d160e-126">定数のデータ型。</span><span class="sxs-lookup"><span data-stu-id="d160e-126">Data type of the constant.</span></span>|  
|`initializer`|<span data-ttu-id="d160e-127">必須です。</span><span class="sxs-lookup"><span data-stu-id="d160e-127">Required.</span></span> <span data-ttu-id="d160e-128">コンパイル時に評価され、式を定数に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="d160e-128">Expression that is evaluated at compile time and assigned to the constant.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d160e-129">コメント</span><span class="sxs-lookup"><span data-stu-id="d160e-129">Remarks</span></span>  
 <span data-ttu-id="d160e-130">アプリケーションで変更されない値があれば、名前付き定数を定義でき、リテラル値の代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="d160e-130">If you have a value that never changes in your application, you can define a named constant and use it in place of a literal value.</span></span> <span data-ttu-id="d160e-131">名前は、値よりも覚えやすくです。</span><span class="sxs-lookup"><span data-stu-id="d160e-131">A name is easier to remember than a value.</span></span> <span data-ttu-id="d160e-132">定数を 1 回だけ定義し、コードでのさまざまな場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d160e-132">You can define the constant just once and use it in many places in your code.</span></span> <span data-ttu-id="d160e-133">以降のバージョンでは、値を再定義する必要がある場合、`Const`ステートメントは、唯一の場所を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d160e-133">If in a later version you need to redefine the value, the `Const` statement is the only place you need to make a change.</span></span>  
  
 <span data-ttu-id="d160e-134">使用することができます`Const`モジュールまたはプロシージャ レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="d160e-134">You can use `Const` only at module or procedure level.</span></span> <span data-ttu-id="d160e-135">つまり、*宣言コンテキスト*変数はクラス、構造体、モジュール、プロシージャ、またはブロックする必要があり、ソース ファイル、名前空間、またはインターフェイスにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d160e-135">This means the *declaration context* for a variable must be a class, structure, module, procedure, or block, and cannot be a source file, namespace, or interface.</span></span> <span data-ttu-id="d160e-136">詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d160e-136">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="d160e-137">ローカル定数 (プロシージャ) 内の既定値は、パブリック アクセスとは、それらのアクセス修飾子を使用できません。</span><span class="sxs-lookup"><span data-stu-id="d160e-137">Local constants (inside a procedure) default to public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="d160e-138">クラスとモジュールのメンバー (プロシージャ) の外部の定数既定でプライベート アクセスは、および構造体メンバー定数とパブリック アクセスの既定値です。</span><span class="sxs-lookup"><span data-stu-id="d160e-138">Class and module member constants (outside any procedure) default to private access, and structure member constants default to public access.</span></span> <span data-ttu-id="d160e-139">アクセス修飾子を使用してこれらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="d160e-139">You can adjust their access levels with the access modifiers.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d160e-140">ルール</span><span class="sxs-lookup"><span data-stu-id="d160e-140">Rules</span></span>  
  
-   <span data-ttu-id="d160e-141">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="d160e-141">**Declaration Context.**</span></span> <span data-ttu-id="d160e-142">定数は、プロシージャの外部のモジュール レベルで宣言された、*メンバー定数*以外の場合は、クラス、構造体のメンバーであるかを宣言するモジュールです。</span><span class="sxs-lookup"><span data-stu-id="d160e-142">A constant declared at module level, outside any procedure, is a *member constant*; it is a member of the class, structure, or module that declares it.</span></span>  
  
     <span data-ttu-id="d160e-143">プロシージャ レベルで宣言されている定数は、*ローカル定数*; プロシージャまたはブロックを宣言したに対してローカルであります。</span><span class="sxs-lookup"><span data-stu-id="d160e-143">A constant declared at procedure level is a *local constant*; it is local to the procedure or block that declares it.</span></span>  
  
-   <span data-ttu-id="d160e-144">**属性。**</span><span class="sxs-lookup"><span data-stu-id="d160e-144">**Attributes.**</span></span> <span data-ttu-id="d160e-145">属性は、ローカル定数ではなく、メンバー定数にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="d160e-145">You can apply attributes only to member constants, not to local constants.</span></span> <span data-ttu-id="d160e-146">属性は、ローカル定数などの一時的なストレージの意味ではないアセンブリのメタデータに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d160e-146">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local constants.</span></span>  
  
-   <span data-ttu-id="d160e-147">**修飾子です。**</span><span class="sxs-lookup"><span data-stu-id="d160e-147">**Modifiers.**</span></span> <span data-ttu-id="d160e-148">すべての定数は、既定では、 `Shared`、 `Static`、および`ReadOnly`です。</span><span class="sxs-lookup"><span data-stu-id="d160e-148">By default, all constants are `Shared`, `Static`, and `ReadOnly`.</span></span> <span data-ttu-id="d160e-149">定数を宣言するときに、これらのキーワードのいずれかを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d160e-149">You cannot use any of these keywords when declaring a constant.</span></span>  
  
     <span data-ttu-id="d160e-150">プロシージャ レベルでは使用できません`Shadows`またはのいずれかのアクセス修飾子をローカル定数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="d160e-150">At procedure level, you cannot use `Shadows` or any access modifiers to declare local constants.</span></span>  
  
-   <span data-ttu-id="d160e-151">**複数の定数です。**</span><span class="sxs-lookup"><span data-stu-id="d160e-151">**Multiple Constants.**</span></span> <span data-ttu-id="d160e-152">同じ宣言ステートメントで複数の定数を宣言することができますを指定する、`constantname`それぞれの一部です。</span><span class="sxs-lookup"><span data-stu-id="d160e-152">You can declare several constants in the same declaration statement, specifying the `constantname` part for each one.</span></span> <span data-ttu-id="d160e-153">複数の定数は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="d160e-153">Multiple constants are separated by commas.</span></span>  
  
## <a name="data-type-rules"></a><span data-ttu-id="d160e-154">データ型のルール</span><span class="sxs-lookup"><span data-stu-id="d160e-154">Data Type Rules</span></span>  
  
-   <span data-ttu-id="d160e-155">**データ型。**</span><span class="sxs-lookup"><span data-stu-id="d160e-155">**Data Types.**</span></span> <span data-ttu-id="d160e-156">`Const`ステートメントは、変数のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d160e-156">The `Const` statement can declare the data type of a variable.</span></span> <span data-ttu-id="d160e-157">任意のデータ型または列挙型の名前を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d160e-157">You can specify any data type or the name of an enumeration.</span></span>  
  
-   <span data-ttu-id="d160e-158">**既定の型。**</span><span class="sxs-lookup"><span data-stu-id="d160e-158">**Default Type.**</span></span> <span data-ttu-id="d160e-159">指定しない場合`datatype`、定数のデータ型を受け取る`initializer`です。</span><span class="sxs-lookup"><span data-stu-id="d160e-159">If you do not specify `datatype`, the constant takes the data type of `initializer`.</span></span> <span data-ttu-id="d160e-160">両方を指定する場合`datatype`と`initializer`のデータ型`initializer`に変換できる必要があります`datatype`です。</span><span class="sxs-lookup"><span data-stu-id="d160e-160">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="d160e-161">どちらの場合`datatype`も`initializer`が含まれているデータ型の既定値は`Object`します。</span><span class="sxs-lookup"><span data-stu-id="d160e-161">If neither `datatype` nor `initializer` is present, the data type defaults to `Object`.</span></span>  
  
-   <span data-ttu-id="d160e-162">**さまざまな種類。**</span><span class="sxs-lookup"><span data-stu-id="d160e-162">**Different Types.**</span></span> <span data-ttu-id="d160e-163">個別を使用して複数の定数に異なるデータ型を指定することができます`As`それぞれの変数を宣言する句。</span><span class="sxs-lookup"><span data-stu-id="d160e-163">You can specify different data types for different constants by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="d160e-164">ただし、一般的に使われるを使用して同じ型にいくつかの定数を宣言することはできません`As`句。</span><span class="sxs-lookup"><span data-stu-id="d160e-164">However, you cannot declare several constants to be of the same type by using a common `As` clause.</span></span>  
  
-   <span data-ttu-id="d160e-165">**初期化します。**</span><span class="sxs-lookup"><span data-stu-id="d160e-165">**Initialization.**</span></span> <span data-ttu-id="d160e-166">すべての定数の値を初期化する必要があります`constantlist`です。</span><span class="sxs-lookup"><span data-stu-id="d160e-166">You must initialize the value of every constant in `constantlist`.</span></span> <span data-ttu-id="d160e-167">使用する`initializer`を定数に割り当てられる式を指定します。</span><span class="sxs-lookup"><span data-stu-id="d160e-167">You use `initializer` to supply an expression to be assigned to the constant.</span></span> <span data-ttu-id="d160e-168">式には、リテラル、既に定義されているその他の定数、および既に定義されている列挙型メンバーの任意の組み合わせを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d160e-168">The expression can be any combination of literals, other constants that are already defined, and enumeration members that are already defined.</span></span> <span data-ttu-id="d160e-169">算術演算子および論理演算子を使用すると、このような要素を結合します。</span><span class="sxs-lookup"><span data-stu-id="d160e-169">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
     <span data-ttu-id="d160e-170">変数または関数を使用することはできません`initializer`です。</span><span class="sxs-lookup"><span data-stu-id="d160e-170">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="d160e-171">変換キーワードなどを使用するただし、`CByte`と`CShort`です。</span><span class="sxs-lookup"><span data-stu-id="d160e-171">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="d160e-172">使用することも`AscW`定数で呼び出す場合は、`String`または`Char`引数、コンパイル時に評価できるためです。</span><span class="sxs-lookup"><span data-stu-id="d160e-172">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d160e-173">動作</span><span class="sxs-lookup"><span data-stu-id="d160e-173">Behavior</span></span>  
  
-   <span data-ttu-id="d160e-174">**スコープです。**</span><span class="sxs-lookup"><span data-stu-id="d160e-174">**Scope.**</span></span> <span data-ttu-id="d160e-175">ローカル定数は、そのプロシージャまたはブロック内からしかアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="d160e-175">Local constants are accessible only from within their procedure or block.</span></span> <span data-ttu-id="d160e-176">メンバー定数には、クラス、構造体、またはモジュール内で任意の場所からアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d160e-176">Member constants are accessible from anywhere within their class, structure, or module.</span></span>  
  
-   <span data-ttu-id="d160e-177">**パス名です。**</span><span class="sxs-lookup"><span data-stu-id="d160e-177">**Qualification.**</span></span> <span data-ttu-id="d160e-178">コードをクラスの外部構造体、またはモジュール修飾する必要がありますそのクラス、構造体、モジュールの名前を持つメンバー定数の名前。</span><span class="sxs-lookup"><span data-stu-id="d160e-178">Code outside a class, structure, or module must qualify a member constant's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="d160e-179">プロシージャまたはブロックは、そのプロシージャまたはブロック内であるローカル定数を参照できません外部をコードします。</span><span class="sxs-lookup"><span data-stu-id="d160e-179">Code outside a procedure or block cannot refer to any local constants within that procedure or block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d160e-180">例</span><span class="sxs-lookup"><span data-stu-id="d160e-180">Example</span></span>  
 <span data-ttu-id="d160e-181">次の例では、`Const`ステートメントをリテラル値の代わりに使用する定数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="d160e-181">The following example uses the `Const` statement to declare constants for use in place of literal values.</span></span>  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="d160e-182">例</span><span class="sxs-lookup"><span data-stu-id="d160e-182">Example</span></span>  
 <span data-ttu-id="d160e-183">データ型の定数を定義した場合`Object`、Visual Basic コンパイラは、の型を提供、`initializer`の代わりに`Object`です。</span><span class="sxs-lookup"><span data-stu-id="d160e-183">If you define a constant with data type `Object`, the Visual Basic compiler gives it the type of `initializer`, instead of `Object`.</span></span> <span data-ttu-id="d160e-184">次の例では、定数`naturalLogBase`実行時の型を持つ`Decimal`します。</span><span class="sxs-lookup"><span data-stu-id="d160e-184">In the following example, the constant `naturalLogBase` has the run-time type `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 <span data-ttu-id="d160e-185">前の例では、<xref:System.Type.ToString%2A>メソッドを<xref:System.Type>によって返されるオブジェクト、 [GetType 演算子](../../../visual-basic/language-reference/operators/gettype-operator.md)ため、<xref:System.Type>に変換できない`String`を使用して`CStr`です。</span><span class="sxs-lookup"><span data-stu-id="d160e-185">The preceding example uses the <xref:System.Type.ToString%2A> method on the <xref:System.Type> object returned by the [GetType Operator](../../../visual-basic/language-reference/operators/gettype-operator.md), because <xref:System.Type> cannot be converted to `String` using `CStr`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d160e-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="d160e-186">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [<span data-ttu-id="d160e-187">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="d160e-187">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="d160e-188">#Const ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="d160e-188">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="d160e-189">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="d160e-189">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="d160e-190">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="d160e-190">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="d160e-191">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="d160e-191">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="d160e-192">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="d160e-192">Constants and Enumerations</span></span>](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [<span data-ttu-id="d160e-193">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="d160e-193">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="d160e-194">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="d160e-194">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
