---
title: "Dim ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a428f8be7b62600ca8fffd3160039c1de911e34e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="76032-102">Dim ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76032-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="76032-103">宣言し、1 つまたは複数の変数の記憶域を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="76032-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76032-104">構文</span><span class="sxs-lookup"><span data-stu-id="76032-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="76032-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="76032-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="76032-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-106">Optional.</span></span> <span data-ttu-id="76032-107">参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="76032-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-108">Optional.</span></span> <span data-ttu-id="76032-109">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="76032-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="76032-110">Public</span><span class="sxs-lookup"><span data-stu-id="76032-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="76032-111">Protected</span><span class="sxs-lookup"><span data-stu-id="76032-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="76032-112">Friend</span><span class="sxs-lookup"><span data-stu-id="76032-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="76032-113">Private</span><span class="sxs-lookup"><span data-stu-id="76032-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="76032-114">参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-114">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="76032-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-115">Optional.</span></span> <span data-ttu-id="76032-116">参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-116">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="76032-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-117">Optional.</span></span> <span data-ttu-id="76032-118">参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-118">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="76032-119">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-119">Optional.</span></span> <span data-ttu-id="76032-120">参照してください[静的](../../../visual-basic/language-reference/modifiers/static.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-120">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="76032-121">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-121">Optional.</span></span> <span data-ttu-id="76032-122">参照してください[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-122">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="76032-123">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-123">Optional.</span></span> <span data-ttu-id="76032-124">これらがイベントを発生させるクラスのインスタンスを参照するオブジェクト変数であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="76032-124">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="76032-125">参照してください[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-125">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="76032-126">必須です。</span><span class="sxs-lookup"><span data-stu-id="76032-126">Required.</span></span> <span data-ttu-id="76032-127">このステートメントで宣言されている変数の一覧です。</span><span class="sxs-lookup"><span data-stu-id="76032-127">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="76032-128">`variable` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="76032-128">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="76032-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="76032-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="76032-130">パーツ</span><span class="sxs-lookup"><span data-stu-id="76032-130">Part</span></span>|<span data-ttu-id="76032-131">説明</span><span class="sxs-lookup"><span data-stu-id="76032-131">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="76032-132">必須です。</span><span class="sxs-lookup"><span data-stu-id="76032-132">Required.</span></span> <span data-ttu-id="76032-133">変数の名前です。</span><span class="sxs-lookup"><span data-stu-id="76032-133">Name of the variable.</span></span> <span data-ttu-id="76032-134">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="76032-135">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-135">Optional.</span></span> <span data-ttu-id="76032-136">配列変数の各次元の境界の一覧です。</span><span class="sxs-lookup"><span data-stu-id="76032-136">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="76032-137">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-137">Optional.</span></span> <span data-ttu-id="76032-138">クラスの新しいインスタンスを作成時に、`Dim`ステートメントが実行されています。</span><span class="sxs-lookup"><span data-stu-id="76032-138">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="76032-139">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-139">Optional.</span></span> <span data-ttu-id="76032-140">変数のデータ型。</span><span class="sxs-lookup"><span data-stu-id="76032-140">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="76032-141">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-141">Optional.</span></span> <span data-ttu-id="76032-142">オブジェクト初期化子リストが導入されています。</span><span class="sxs-lookup"><span data-stu-id="76032-142">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="76032-143">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="76032-143">Optional.</span></span> <span data-ttu-id="76032-144">インスタンスを作成するクラスのプロパティの名前。</span><span class="sxs-lookup"><span data-stu-id="76032-144">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="76032-145">後に必要な`propertyname`= です。</span><span class="sxs-lookup"><span data-stu-id="76032-145">Required after `propertyname` =.</span></span> <span data-ttu-id="76032-146">評価され、プロパティ名に割り当てられている式です。</span><span class="sxs-lookup"><span data-stu-id="76032-146">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="76032-147">省略可能な場合`New`が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="76032-147">Optional if `New` is not specified.</span></span> <span data-ttu-id="76032-148">式が評価され、変数に割り当てが作成されるときです。</span><span class="sxs-lookup"><span data-stu-id="76032-148">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76032-149">コメント</span><span class="sxs-lookup"><span data-stu-id="76032-149">Remarks</span></span>  
 <span data-ttu-id="76032-150">Visual Basic コンパイラを使用して、`Dim`変数のデータ型とどのようなコードが変数にアクセスできるなど、他の情報を確認するステートメント。</span><span class="sxs-lookup"><span data-stu-id="76032-150">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="76032-151">次の例を保持する変数の宣言、`Integer`値。</span><span class="sxs-lookup"><span data-stu-id="76032-151">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="76032-152">任意のデータ型または列挙型、構造体、クラス、またはインターフェイスの名前を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="76032-152">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="76032-153">使用する参照型の場合、`New`データ型によって、クラスの新しいインスタンスを作成または構造体にキーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="76032-153">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="76032-154">使用する場合`New`、初期化子式を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="76032-154">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="76032-155">代わりに、これらが必要な場合、変数の作成元となるクラスのコンス トラクターに引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="76032-155">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="76032-156">プロシージャ、ブロック、クラス、構造体、またはモジュール内の変数を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="76032-156">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="76032-157">ソース ファイル、名前空間、またはインターフェイスの変数を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="76032-157">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="76032-158">詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76032-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="76032-159">プロシージャの外部のモジュール レベルで宣言された変数は、*メンバー変数*または*フィールド*です。</span><span class="sxs-lookup"><span data-stu-id="76032-159">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="76032-160">メンバー変数は、そのクラス、構造体、またはモジュール全体にわたってスコープでは。</span><span class="sxs-lookup"><span data-stu-id="76032-160">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="76032-161">プロシージャ レベルで宣言された変数は、*ローカル変数*です。</span><span class="sxs-lookup"><span data-stu-id="76032-161">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="76032-162">ローカル変数は、そのプロシージャまたはブロック内でのみスコープでは。</span><span class="sxs-lookup"><span data-stu-id="76032-162">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="76032-163">次のアクセス修飾子を使用して、プロシージャの外部変数を宣言します。 `Public`、 `Protected`、 `Friend`、 `Protected Friend`、および`Private`です。</span><span class="sxs-lookup"><span data-stu-id="76032-163">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="76032-164">詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-164">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="76032-165">`Dim`キーワードは省略可能な次の修飾子のいずれかを指定する場合、通常は省略して: `Public`、 `Protected`、 `Friend`、 `Protected Friend`、 `Private`、 `Shared`、 `Shadows`、 `Static`、`ReadOnly`、または`WithEvents`です。</span><span class="sxs-lookup"><span data-stu-id="76032-165">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="76032-166">場合`Option Explicit`はコンパイラ on (既定値) を使用するすべての変数の宣言が必要です。</span><span class="sxs-lookup"><span data-stu-id="76032-166">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="76032-167">詳細については、次を参照してください。 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-167">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="76032-168">初期値を指定します。</span><span class="sxs-lookup"><span data-stu-id="76032-168">Specifying an Initial Value</span></span>  
 <span data-ttu-id="76032-169">作成されるときに、変数に値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="76032-169">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="76032-170">値の型を使用する、*初期化子*を変数に割り当てられる式を指定します。</span><span class="sxs-lookup"><span data-stu-id="76032-170">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="76032-171">式は、コンパイル時に計算できる定数に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="76032-171">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="76032-172">初期化子が指定され、データ型がで指定されていない場合、`As`句、*型推論*初期化子からのデータ型を推論するために使用します。</span><span class="sxs-lookup"><span data-stu-id="76032-172">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="76032-173">次の例では、両方とも`num1`と`num2`整数値として厳密に型指定します。</span><span class="sxs-lookup"><span data-stu-id="76032-173">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="76032-174">2 番目の宣言では、型の推論は、値は 3 から型を推測します。</span><span class="sxs-lookup"><span data-stu-id="76032-174">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="76032-175">型の推論は、プロシージャ レベルで適用されます。</span><span class="sxs-lookup"><span data-stu-id="76032-175">Type inference applies at the procedure level.</span></span> <span data-ttu-id="76032-176">クラス、構造体、モジュール、またはインターフェイスのプロシージャの外側は適用されません。</span><span class="sxs-lookup"><span data-stu-id="76032-176">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="76032-177">型の推定の詳細については、次を参照してください。 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-177">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="76032-178">データ型または初期化子が指定されていない場合の動作方法については、次を参照してください。[既定のデータ型と値](../../../visual-basic/language-reference/statements/dim-statement.md#default)このトピックで後述します。</span><span class="sxs-lookup"><span data-stu-id="76032-178">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="76032-179">使用することができます、*オブジェクトの初期化子*匿名の名前付きの型のインスタンスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="76032-179">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="76032-180">次のコードがのインスタンスを作成、`Student`クラスし、プロパティを初期化するために、オブジェクト初期化子を使用します。</span><span class="sxs-lookup"><span data-stu-id="76032-180">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="76032-181">オブジェクト初期化子の詳細については、次を参照してください[する方法: オブジェクト初期化子を使用してオブジェクトを宣言](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)、[オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)、および[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="76032-181">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="76032-182">複数の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="76032-182">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="76032-183">かっこで次の各配列名と、それぞれの変数名を指定する 1 つの宣言ステートメントで複数の変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="76032-183">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="76032-184">複数の変数を指定するときは、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="76032-184">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="76032-185">いずれかで 1 つ以上の変数を宣言する場合`As`句、そのグループの変数の初期化子を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="76032-185">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="76032-186">個別を使用して別の変数の別のデータ型を指定することができます`As`それぞれの変数を宣言する句。</span><span class="sxs-lookup"><span data-stu-id="76032-186">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="76032-187">各変数は、最初に指定されたデータ型を受け取り`As`句の後に発生したその`variablename`一部です。</span><span class="sxs-lookup"><span data-stu-id="76032-187">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="76032-188">配列</span><span class="sxs-lookup"><span data-stu-id="76032-188">Arrays</span></span>  
 <span data-ttu-id="76032-189">保持する変数を宣言することができます、*配列*、複数の値を保持することができます。</span><span class="sxs-lookup"><span data-stu-id="76032-189">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="76032-190">次の変数は配列を保持することを指定する、`variablename`かっこですぐにします。</span><span class="sxs-lookup"><span data-stu-id="76032-190">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="76032-191">配列の詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-191">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="76032-192">配列の各次元の上限と下限を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="76032-192">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="76032-193">これを行うには、含める、`boundslist`かっこの中にします。</span><span class="sxs-lookup"><span data-stu-id="76032-193">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="76032-194">各ディメンションに対して、`boundslist`上限の境界と必要に応じて、下限を指定します。</span><span class="sxs-lookup"><span data-stu-id="76032-194">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="76032-195">下限とは常に 0 の場合か、指定するかどうか。</span><span class="sxs-lookup"><span data-stu-id="76032-195">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="76032-196">各インデックスは、0 ~ 上限値から変更できます。</span><span class="sxs-lookup"><span data-stu-id="76032-196">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="76032-197">次の 2 つのステートメントは同等です。</span><span class="sxs-lookup"><span data-stu-id="76032-197">The following two statements are equivalent.</span></span> <span data-ttu-id="76032-198">各ステートメントは、21 の配列を宣言`Integer`要素。</span><span class="sxs-lookup"><span data-stu-id="76032-198">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="76032-199">配列にアクセスするときにインデックスが 0 ~ 20 異なることができます。</span><span class="sxs-lookup"><span data-stu-id="76032-199">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="76032-200">次のステートメントは、型の 2 次元配列を宣言して`Double`です。</span><span class="sxs-lookup"><span data-stu-id="76032-200">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="76032-201">配列は、4 6 列 (5 + 1) 各の行 (3 + 1) です。</span><span class="sxs-lookup"><span data-stu-id="76032-201">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="76032-202">上限が、ディメンションの長さではなく、インデックスの最大値を表すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="76032-202">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="76032-203">次元の長さは、上限の境界と 1 つです。</span><span class="sxs-lookup"><span data-stu-id="76032-203">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="76032-204">配列は、1 から 32 次元を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="76032-204">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="76032-205">すべての境界を配列の宣言に空白にできます。</span><span class="sxs-lookup"><span data-stu-id="76032-205">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="76032-206">これを行う場合は、配列は、指定すると、ディメンションの数が初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="76032-206">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="76032-207">値がある`Nothing`には、少なくとも初期化するまでその要素の一部です。</span><span class="sxs-lookup"><span data-stu-id="76032-207">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="76032-208">`Dim`ステートメントは、境界内のすべてのディメンションまたはディメンションがありませんのいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76032-208">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="76032-209">配列に 1 つ以上のディメンションがある場合は、ディメンションの数を示すためにかっこで囲まれたコンマを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="76032-209">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="76032-210">宣言することができます、*長さ 0 の配列*-1 である配列の次元のいずれかを宣言することによりします。</span><span class="sxs-lookup"><span data-stu-id="76032-210">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="76032-211">長さ 0 の配列を保持する変数は、値を持たない`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="76032-211">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="76032-212">長さ 0 の配列は、共通言語ランタイムの一部の関数は必要です。</span><span class="sxs-lookup"><span data-stu-id="76032-212">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="76032-213">このような配列にアクセスしようとすると、ランタイム例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="76032-213">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="76032-214">詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-214">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="76032-215">配列リテラルを使用して、配列の値を初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="76032-215">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="76032-216">これを行うには、中かっこと初期化の値を囲む (`{}`)。</span><span class="sxs-lookup"><span data-stu-id="76032-216">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="76032-217">多次元配列は、各次元の初期化は、外側のディメンションの中かっこで囲まれます。</span><span class="sxs-lookup"><span data-stu-id="76032-217">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="76032-218">要素は、行優先順で指定されます。</span><span class="sxs-lookup"><span data-stu-id="76032-218">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="76032-219">配列リテラルの詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-219">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <a name="default"></a><span data-ttu-id="76032-220">既定のデータ型し、値</span><span class="sxs-lookup"><span data-stu-id="76032-220">Default Data Types and Values</span></span>  
 <span data-ttu-id="76032-221">次の表では、`Dim` ステートメントのデータ型と初期化子を指定するさまざまな組み合わせの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="76032-221">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="76032-222">データ型が指定されているか</span><span class="sxs-lookup"><span data-stu-id="76032-222">Data type specified?</span></span>|<span data-ttu-id="76032-223">初期化子が指定されているか</span><span class="sxs-lookup"><span data-stu-id="76032-223">Initializer specified?</span></span>|<span data-ttu-id="76032-224">例</span><span class="sxs-lookup"><span data-stu-id="76032-224">Example</span></span>|<span data-ttu-id="76032-225">結果</span><span class="sxs-lookup"><span data-stu-id="76032-225">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="76032-226">Ｘ</span><span class="sxs-lookup"><span data-stu-id="76032-226">No</span></span>|<span data-ttu-id="76032-227">いいえ</span><span class="sxs-lookup"><span data-stu-id="76032-227">No</span></span>|`Dim qty`|<span data-ttu-id="76032-228">場合[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)に設定されている変数 off (既定)、`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="76032-228">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="76032-229">`Option Strict` がオンの場合、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="76032-229">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="76032-230">Ｘ</span><span class="sxs-lookup"><span data-stu-id="76032-230">No</span></span>|<span data-ttu-id="76032-231">はい</span><span class="sxs-lookup"><span data-stu-id="76032-231">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="76032-232">場合[Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) on (既定値) は、変数は、データが初期化子の型します。</span><span class="sxs-lookup"><span data-stu-id="76032-232">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="76032-233">参照してください[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-233">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="76032-234">`Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。</span><span class="sxs-lookup"><span data-stu-id="76032-234">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="76032-235">`Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="76032-235">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="76032-236">○</span><span class="sxs-lookup"><span data-stu-id="76032-236">Yes</span></span>|<span data-ttu-id="76032-237">Ｘ</span><span class="sxs-lookup"><span data-stu-id="76032-237">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="76032-238">変数は、データ型の既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="76032-238">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="76032-239">このセクションの後半の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76032-239">See the table later in this section.</span></span>|  
|<span data-ttu-id="76032-240">はい</span><span class="sxs-lookup"><span data-stu-id="76032-240">Yes</span></span>|<span data-ttu-id="76032-241">○</span><span class="sxs-lookup"><span data-stu-id="76032-241">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="76032-242">初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="76032-242">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="76032-243">データ型を指定して、初期化子を指定しない場合[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]のデータ型の既定値に変数を初期化します。</span><span class="sxs-lookup"><span data-stu-id="76032-243">If you specify a data type but do not specify an initializer, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="76032-244">次の表は、既定値に初期化の値を示します。</span><span class="sxs-lookup"><span data-stu-id="76032-244">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="76032-245">データ型</span><span class="sxs-lookup"><span data-stu-id="76032-245">Data type</span></span>|<span data-ttu-id="76032-246">既定値</span><span class="sxs-lookup"><span data-stu-id="76032-246">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="76032-247">すべての数値型 (など`Byte`と`SByte`)</span><span class="sxs-lookup"><span data-stu-id="76032-247">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="76032-248">0</span><span class="sxs-lookup"><span data-stu-id="76032-248">0</span></span>|  
|`Char`|<span data-ttu-id="76032-249">バイナリ 0</span><span class="sxs-lookup"><span data-stu-id="76032-249">Binary 0</span></span>|  
|<span data-ttu-id="76032-250">参照型はすべて (含む`Object`、 `String`、およびすべての配列)</span><span class="sxs-lookup"><span data-stu-id="76032-250">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="76032-251">1 年 1 月 1 日の午前 12時 00分 (01/01/0001 12時 00分: 00 AM)</span><span class="sxs-lookup"><span data-stu-id="76032-251">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="76032-252">構造体の各要素は個別の変数の場合と同様に初期化します。</span><span class="sxs-lookup"><span data-stu-id="76032-252">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="76032-253">配列の長さを宣言でその要素を初期化しない場合、各要素は、個別の変数の場合と同様に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="76032-253">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="76032-254">静的ローカル変数有効期間</span><span class="sxs-lookup"><span data-stu-id="76032-254">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="76032-255">A`Static`ローカル変数が宣言されているプロシージャの場合よりも有効期間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="76032-255">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="76032-256">変数の有効期間の境界は、プロシージャが宣言されていると、かどうかによって異なります。`Shared`です。</span><span class="sxs-lookup"><span data-stu-id="76032-256">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="76032-257">プロシージャの宣言</span><span class="sxs-lookup"><span data-stu-id="76032-257">Procedure declaration</span></span>|<span data-ttu-id="76032-258">初期化された変数</span><span class="sxs-lookup"><span data-stu-id="76032-258">Variable initialized</span></span>|<span data-ttu-id="76032-259">既存の変数を停止します。</span><span class="sxs-lookup"><span data-stu-id="76032-259">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="76032-260">モジュールで</span><span class="sxs-lookup"><span data-stu-id="76032-260">In a module</span></span>|<span data-ttu-id="76032-261">最初に、プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="76032-261">The first time the procedure is called</span></span>|<span data-ttu-id="76032-262">プログラムが実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="76032-262">When your program stops execution</span></span>|  
|<span data-ttu-id="76032-263">手順は、クラスまたは構造体は、します。`Shared`</span><span class="sxs-lookup"><span data-stu-id="76032-263">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="76032-264">最初に、プロシージャを呼び出すか、特定のインスタンスまたはクラスまたは構造体自体</span><span class="sxs-lookup"><span data-stu-id="76032-264">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="76032-265">プログラムが実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="76032-265">When your program stops execution</span></span>|  
|<span data-ttu-id="76032-266">クラスまたは構造体では、プロシージャはありません。`Shared`</span><span class="sxs-lookup"><span data-stu-id="76032-266">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="76032-267">初めてプロシージャは特定のインスタンスで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="76032-267">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="76032-268">ガベージ コレクション (GC) のインスタンスを解放する場合</span><span class="sxs-lookup"><span data-stu-id="76032-268">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="76032-269">属性と修飾子</span><span class="sxs-lookup"><span data-stu-id="76032-269">Attributes and Modifiers</span></span>  
 <span data-ttu-id="76032-270">属性は、ローカル変数ではなく、メンバー変数にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="76032-270">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="76032-271">属性は、ローカル変数などの一時的なストレージの意味ではないアセンブリのメタデータに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="76032-271">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="76032-272">モジュール レベルで使用することはできません、`Static`修飾子メンバー変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="76032-272">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="76032-273">プロシージャ レベルでは使用できません`Shared`、 `Shadows`、 `ReadOnly`、`WithEvents`のいずれかのアクセス修飾子をローカル変数を宣言するか。</span><span class="sxs-lookup"><span data-stu-id="76032-273">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="76032-274">指定することによって、変数にアクセスできるコードを指定することができます、`accessmodifier`です。</span><span class="sxs-lookup"><span data-stu-id="76032-274">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="76032-275">クラスとモジュールのメンバー (プロシージャ) の外部変数既定でプライベート アクセスは、および構造体のメンバー変数の既定でパブリック アクセスです。</span><span class="sxs-lookup"><span data-stu-id="76032-275">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="76032-276">アクセス修飾子を使用してこれらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="76032-276">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="76032-277">(プロシージャ) 内のローカル変数にアクセス修飾子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="76032-277">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="76032-278">指定できます`WithEvents`のみメンバー変数ではなく、プロシージャ内のローカル変数。</span><span class="sxs-lookup"><span data-stu-id="76032-278">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="76032-279">指定した場合`WithEvents`、変数のデータ型では、特定のクラス型を解除する必要がある`Object`です。</span><span class="sxs-lookup"><span data-stu-id="76032-279">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="76032-280">格納された配列を宣言することはできません`WithEvents`です。</span><span class="sxs-lookup"><span data-stu-id="76032-280">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="76032-281">イベントの詳細については、次を参照してください。[イベント](../../../visual-basic/programming-guide/language-features/events/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="76032-281">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76032-282">コードをクラスの外部構造体、またはモジュール修飾する必要がありますそのクラス、構造体、モジュールの名前を持つメンバー変数の名前。</span><span class="sxs-lookup"><span data-stu-id="76032-282">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="76032-283">プロシージャまたはブロックは、そのプロシージャまたはブロック内のローカル変数を参照できません外部をコードします。</span><span class="sxs-lookup"><span data-stu-id="76032-283">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="76032-284">マネージ リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="76032-284">Releasing Managed Resources</span></span>  
 <span data-ttu-id="76032-285">ユーザーによる追加のコーディングなしに、.NET Framework のガベージ コレクターがマネージ リソースを破棄します。</span><span class="sxs-lookup"><span data-stu-id="76032-285">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="76032-286">ただし、ガベージ コレクターを待つ代わりにマネージ リソースの破棄を強制することができます。</span><span class="sxs-lookup"><span data-stu-id="76032-286">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="76032-287">クラスは、特に、不足しているリソース (データベース接続やファイル ハンドル) などの上に保持している場合、次のガベージ コレクションが不要で使用されるクラスのインスタンスをクリーンアップするまで待機することがないできます。</span><span class="sxs-lookup"><span data-stu-id="76032-287">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="76032-288">クラスが実装することが、<xref:System.IDisposable>ガベージ コレクションの前にリソースを解放する方法を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="76032-288">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="76032-289">そのインターフェイスを実装するクラスは、公開、`Dispose`貴重なリソースを直ちに解放を強制的に呼び出すことができるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="76032-289">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="76032-290">`Using`ステートメントは、リソースを取得する、一連のステートメントを実行およびリソースの破棄し、プロセスを自動化します。</span><span class="sxs-lookup"><span data-stu-id="76032-290">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="76032-291">ただし、リソースを実装する必要があります、<xref:System.IDisposable>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="76032-291">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="76032-292">詳細については、「[Using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76032-292">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76032-293">例</span><span class="sxs-lookup"><span data-stu-id="76032-293">Example</span></span>  
 <span data-ttu-id="76032-294">次の例では、変数を宣言を使用して、`Dim`さまざまなオプションを含むステートメント。</span><span class="sxs-lookup"><span data-stu-id="76032-294">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="76032-295">例</span><span class="sxs-lookup"><span data-stu-id="76032-295">Example</span></span>  
 <span data-ttu-id="76032-296">次の例は、1 ~ 30 の素数を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="76032-296">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="76032-297">ローカル変数のスコープには、コードのコメントが記載されています。</span><span class="sxs-lookup"><span data-stu-id="76032-297">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="76032-298">例</span><span class="sxs-lookup"><span data-stu-id="76032-298">Example</span></span>  
 <span data-ttu-id="76032-299">次の例で、`speedValue`変数はクラス レベルで宣言します。</span><span class="sxs-lookup"><span data-stu-id="76032-299">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="76032-300">`Private`変数を宣言するキーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="76032-300">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="76032-301">変数のいずれの手順によってアクセスできる、`Car`クラスです。</span><span class="sxs-lookup"><span data-stu-id="76032-301">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="76032-302">関連項目</span><span class="sxs-lookup"><span data-stu-id="76032-302">See Also</span></span>  
 [<span data-ttu-id="76032-303">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="76032-303">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="76032-304">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="76032-304">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="76032-305">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="76032-305">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="76032-306">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="76032-306">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="76032-307">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="76032-307">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 <span data-ttu-id="76032-308">[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="76032-308">[Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span></span>  
 [<span data-ttu-id="76032-309">変数宣言</span><span class="sxs-lookup"><span data-stu-id="76032-309">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="76032-310">配列</span><span class="sxs-lookup"><span data-stu-id="76032-310">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="76032-311">オブジェクト初期化子 : 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="76032-311">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="76032-312">匿名型</span><span class="sxs-lookup"><span data-stu-id="76032-312">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="76032-313">オブジェクト初期化子 : 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="76032-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="76032-314">方法 : オブジェクト初期化子を使用してオブジェクトを宣言する</span><span class="sxs-lookup"><span data-stu-id="76032-314">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [<span data-ttu-id="76032-315">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="76032-315">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
