---
title: "Dim ステートメント (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Dim
- Dim
dev_langs:
- VB
helpviewer_keywords:
- Public keyword, in Dim statement
- Dim statement
- fixed-length strings, declaring
- variables [Visual Basic], declaring
- WithEvents keyword, Dim statement
- dynamic arrays, Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields, as member variables
- declarations, dynamic arrays
- member variables
- default values
- data types [Visual Basic], assigning
- braces {}
- As keyword, in Dim statement
- arrays [Visual Basic], declaring
- New keyword, Dim statement
- To keyword, in Dim statement
- storage, allocating
- local variables
- declaration statements
- Dim statement, syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
caps.latest.revision: 72
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
ms.openlocfilehash: 049ab1e82bac6c9f94bc411cd3e7c859e334d739
ms.contentlocale: ja-jp
ms.lasthandoff: 05/15/2017

---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="9c0ea-102">Dim ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c0ea-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="9c0ea-103">宣言し、1 つまたは複数の変数の記憶域を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c0ea-104">構文</span><span class="sxs-lookup"><span data-stu-id="9c0ea-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="9c0ea-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="9c0ea-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="9c0ea-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-106">Optional.</span></span> <span data-ttu-id="9c0ea-107">参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="9c0ea-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-108">Optional.</span></span> <span data-ttu-id="9c0ea-109">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="9c0ea-110">Public</span><span class="sxs-lookup"><span data-stu-id="9c0ea-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="9c0ea-111">Protected</span><span class="sxs-lookup"><span data-stu-id="9c0ea-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="9c0ea-112">Friend</span><span class="sxs-lookup"><span data-stu-id="9c0ea-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="9c0ea-113">Private</span><span class="sxs-lookup"><span data-stu-id="9c0ea-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="9c0ea-114">参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-114">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="9c0ea-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-115">Optional.</span></span> <span data-ttu-id="9c0ea-116">参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-116">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="9c0ea-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-117">Optional.</span></span> <span data-ttu-id="9c0ea-118">参照してください[シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-118">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="9c0ea-119">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-119">Optional.</span></span> <span data-ttu-id="9c0ea-120">参照してください[静的](../../../visual-basic/language-reference/modifiers/static.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-120">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="9c0ea-121">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-121">Optional.</span></span> <span data-ttu-id="9c0ea-122">参照してください[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-122">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="9c0ea-123">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-123">Optional.</span></span> <span data-ttu-id="9c0ea-124">これらがイベントを発生させるクラスのインスタンスを参照するオブジェクト変数であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-124">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="9c0ea-125">参照してください[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-125">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="9c0ea-126">必須です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-126">Required.</span></span> <span data-ttu-id="9c0ea-127">このステートメントで宣言されている変数の一覧です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-127">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="9c0ea-128">`variable` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-128">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="9c0ea-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="9c0ea-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="9c0ea-130">パーツ</span><span class="sxs-lookup"><span data-stu-id="9c0ea-130">Part</span></span>|<span data-ttu-id="9c0ea-131">説明</span><span class="sxs-lookup"><span data-stu-id="9c0ea-131">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="9c0ea-132">必須です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-132">Required.</span></span> <span data-ttu-id="9c0ea-133">変数名。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-133">Name of the variable.</span></span> <span data-ttu-id="9c0ea-134">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="9c0ea-135">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-135">Optional.</span></span> <span data-ttu-id="9c0ea-136">配列変数の各次元の境界のリストです。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-136">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="9c0ea-137">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-137">Optional.</span></span> <span data-ttu-id="9c0ea-138">クラスの新しいインスタンスを作成するときに、`Dim`ステートメントが実行されています。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-138">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="9c0ea-139">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-139">Optional.</span></span> <span data-ttu-id="9c0ea-140">変数のデータ型。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-140">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="9c0ea-141">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-141">Optional.</span></span> <span data-ttu-id="9c0ea-142">オブジェクト初期化子リストを紹介します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-142">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="9c0ea-143">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-143">Optional.</span></span> <span data-ttu-id="9c0ea-144">インスタンスを作成するクラスのプロパティの名前。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-144">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="9c0ea-145">後に必要な`propertyname`= です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-145">Required after `propertyname` =.</span></span> <span data-ttu-id="9c0ea-146">この式は評価され、プロパティ名に割り当てられているです。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-146">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="9c0ea-147">省略可能な場合`New`が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-147">Optional if `New` is not specified.</span></span> <span data-ttu-id="9c0ea-148">評価され、作成時に、変数に代入する式です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-148">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c0ea-149">コメント</span><span class="sxs-lookup"><span data-stu-id="9c0ea-149">Remarks</span></span>  
 <span data-ttu-id="9c0ea-150">Visual Basic コンパイラを使用して、`Dim`変数のデータ型と変数にアクセスできるコードなど、他の情報を確認するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-150">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="9c0ea-151">次の例を保持する変数の宣言、`Integer`値。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-151">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="9c0ea-152">任意のデータ型または列挙型、構造体、クラス、インターフェイスの名前を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-152">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="9c0ea-153">参照型を使用する、`New`データ型で、クラスの新しいインスタンスを作成または構造体にキーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-153">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="9c0ea-154">使用する場合`New`、初期化子式を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-154">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="9c0ea-155">代わりに、変数の作成元となるクラスのコンス トラクターに必要な場合は、引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-155">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="9c0ea-156">プロシージャ、ブロック、クラス、構造体、またはモジュール内の変数を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-156">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="9c0ea-157">ソース ファイル、名前空間、またはインターフェイスの変数を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-157">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="9c0ea-158">詳細については、次を参照してください。[宣言コンテキストとアクセス レベルの既定の](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="9c0ea-159">プロシージャの外部のモジュール レベルで宣言されている変数は、*メンバー変数*または*フィールド*します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-159">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="9c0ea-160">メンバー変数は、クラス、構造体、またはモジュール全体に及びます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-160">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="9c0ea-161">プロシージャ レベルで宣言されている変数は、*ローカル変数*します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-161">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="9c0ea-162">ローカル変数はそのプロシージャまたはブロック内でのみに及びます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-162">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="9c0ea-163">プロシージャの外の変数を宣言する次のアクセス修飾子を使用します。 `Public`、 `Protected`、 `Friend`、 `Protected Friend`、および`Private`です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-163">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="9c0ea-164">詳細については、次を参照してください。 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-164">For more information, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="9c0ea-165">`Dim`キーワードを省略し、次の修飾子のいずれかを指定する場合は通常省略: `Public`、 `Protected`、 `Friend`、 `Protected Friend`、 `Private`、 `Shared`、 `Shadows`、 `Static`、 `ReadOnly`、または`WithEvents`です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-165">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="9c0ea-166">場合`Option Explicit`はコンパイラ on (既定値) を使用するすべての変数の宣言が必要です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-166">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="9c0ea-167">詳細については、次を参照してください。 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-167">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="9c0ea-168">初期値を指定します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-168">Specifying an Initial Value</span></span>  
 <span data-ttu-id="9c0ea-169">作成されるときに、変数に値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-169">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="9c0ea-170">値の型を使用する、*初期化子*変数に割り当てられる式を指定します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-170">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="9c0ea-171">式は、コンパイル時に計算できる定数に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-171">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="9c0ea-172">初期化子が指定されており、データ型がで指定されていない場合、`As`句、*型の推論*は初期化子からのデータ型の推論に使用します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-172">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="9c0ea-173">次の例では両方とも`num1`と`num2`整数として厳密に型指定します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-173">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="9c0ea-174">2 番目の宣言では、型の推論は、値 3 から型を推測します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-174">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="9c0ea-175">型の推論は、プロシージャ レベルで適用されます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-175">Type inference applies at the procedure level.</span></span> <span data-ttu-id="9c0ea-176">これは、クラス、構造体、モジュール、またはインターフェイスのプロシージャの外側は適用されません。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-176">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="9c0ea-177">型の推定の詳細については、次を参照してください。 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-177">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="9c0ea-178">データ型または初期化子が指定されていないときの動作方法については、次を参照してください。[既定のデータ型や値](../../../visual-basic/language-reference/statements/dim-statement.md#default)このトピックで後述します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-178">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="9c0ea-179">使用することができます、*オブジェクト初期化子*匿名の名前付きの型のインスタンスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-179">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="9c0ea-180">次のコードは、のインスタンスを作成、`Student`クラスし、オブジェクト初期化子を使用してプロパティを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-180">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="9c0ea-181">オブジェクト初期化子の詳細については、次を参照してください。[方法: オブジェクト初期化子を使用してオブジェクトを宣言](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)、[オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)、および[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-181">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="9c0ea-182">複数の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-182">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="9c0ea-183">かっこを使用し、各配列名ごとに、変数名を指定する&1; つの宣言ステートメントで複数の変数を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-183">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="9c0ea-184">複数の変数を指定するときは、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-184">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="9c0ea-185">いずれかで&1; つ以上の変数を宣言する場合は、`As`句の変数には、そのグループの初期化子を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-185">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="9c0ea-186">別々 の異なる変数に異なるデータ型を指定する`As`を宣言する各変数の句。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-186">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="9c0ea-187">各変数は、最初に指定されているデータ型を受け取り`As`句の後に発生したその`variablename`部分です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-187">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="9c0ea-188">配列</span><span class="sxs-lookup"><span data-stu-id="9c0ea-188">Arrays</span></span>  
 <span data-ttu-id="9c0ea-189">保持する変数を宣言する、*配列*、複数の値を保持することができます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-189">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="9c0ea-190">変数は配列を保持することを指定するには、次の`variablename`直後のかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-190">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="9c0ea-191">配列の概要の詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-191">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="9c0ea-192">配列の各次元の上限と下限を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-192">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="9c0ea-193">これを行うには、含める、`boundslist`かっこ内にします。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-193">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="9c0ea-194">各ディメンションに対して、`boundslist`上限と下限の境界のオプションでを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-194">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="9c0ea-195">下限値は常に&0;、指定するかどうかどうか。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-195">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="9c0ea-196">各インデックスには、0 ~ 上限値は異なります。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-196">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="9c0ea-197">次の&2; つのステートメントは等価です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-197">The following two statements are equivalent.</span></span> <span data-ttu-id="9c0ea-198">各ステートメントが 21 の配列を宣言して`Integer`要素。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-198">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="9c0ea-199">配列にアクセスする場合は、インデックスが 0 ~ 20 異なることができます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-199">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="9c0ea-200">次のステートメントは、型の&2; 次元配列を宣言して`Double`します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-200">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="9c0ea-201">配列には、6 列 (5 + 1) ごとの 4 つの行 (3 + 1) があります。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-201">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="9c0ea-202">上限の境界がの次元の長さではなく、インデックスを指定できる最大値を表すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-202">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="9c0ea-203">次元の長さは、上限の境界と&1; つです。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-203">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="9c0ea-204">配列は、32 のディメンションに 1 ができます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-204">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="9c0ea-205">すべての境界に配列の宣言で空白しておきます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-205">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="9c0ea-206">これを行う場合は、配列は、指定したディメンションの数が初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-206">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="9c0ea-207">値がある`Nothing`には、少なくとも初期化しないと、その要素の一部です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-207">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="9c0ea-208">`Dim`ステートメントは、境界内のすべてのディメンションまたはディメンションがありませんのいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-208">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="9c0ea-209">配列に&1; つ以上のディメンションがある場合は、ディメンションの数を示すためにかっこで囲まれたコンマを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-209">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="9c0ea-210">宣言することができます、*長さ&0; の配列*を-1 配列の次元のいずれかを宣言することで。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-210">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="9c0ea-211">長さ&0; の配列を保持する変数は、値を持たない`Nothing`します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-211">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="9c0ea-212">共通言語ランタイムの一部の関数では、長さ&0; の配列が必要です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-212">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="9c0ea-213">このような配列にアクセスしようとすると、ランタイム例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-213">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="9c0ea-214">詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-214">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="9c0ea-215">配列の値を初期化するには、配列リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-215">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="9c0ea-216">これを行うには、初期化値を中かっこで囲みます (`{}`)。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-216">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="9c0ea-217">多次元配列の各次元の初期化は、外側のディメンションの中かっこで囲まれました。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-217">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="9c0ea-218">要素は、行優先順で指定されます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-218">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="9c0ea-219">配列リテラルの詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-219">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <span data-ttu-id="9c0ea-220"><a name="default"></a>既定のデータ型し、値</span><span class="sxs-lookup"><span data-stu-id="9c0ea-220"><a name="default"></a> Default Data Types and Values</span></span>  
 <span data-ttu-id="9c0ea-221">次の表では、`Dim` ステートメントのデータ型と初期化子を指定するさまざまな組み合わせの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-221">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="9c0ea-222">データ型が指定されているか</span><span class="sxs-lookup"><span data-stu-id="9c0ea-222">Data type specified?</span></span>|<span data-ttu-id="9c0ea-223">初期化子が指定されているか</span><span class="sxs-lookup"><span data-stu-id="9c0ea-223">Initializer specified?</span></span>|<span data-ttu-id="9c0ea-224">例</span><span class="sxs-lookup"><span data-stu-id="9c0ea-224">Example</span></span>|<span data-ttu-id="9c0ea-225">結果</span><span class="sxs-lookup"><span data-stu-id="9c0ea-225">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="9c0ea-226">Ｘ</span><span class="sxs-lookup"><span data-stu-id="9c0ea-226">No</span></span>|<span data-ttu-id="9c0ea-227">いいえ</span><span class="sxs-lookup"><span data-stu-id="9c0ea-227">No</span></span>|`Dim qty`|<span data-ttu-id="9c0ea-228">場合[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)に設定されている、変数、off (既定)、`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-228">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="9c0ea-229">`Option Strict` がオンの場合、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-229">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="9c0ea-230">Ｘ</span><span class="sxs-lookup"><span data-stu-id="9c0ea-230">No</span></span>|<span data-ttu-id="9c0ea-231">はい</span><span class="sxs-lookup"><span data-stu-id="9c0ea-231">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="9c0ea-232">場合[Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) on (既定値) は、変数は、データが、初期化子の型します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-232">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="9c0ea-233">参照してください[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-233">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="9c0ea-234">`Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-234">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="9c0ea-235">`Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-235">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="9c0ea-236">○</span><span class="sxs-lookup"><span data-stu-id="9c0ea-236">Yes</span></span>|<span data-ttu-id="9c0ea-237">Ｘ</span><span class="sxs-lookup"><span data-stu-id="9c0ea-237">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="9c0ea-238">変数は、データ型の既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-238">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="9c0ea-239">このセクションの後半の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-239">See the table later in this section.</span></span>|  
|<span data-ttu-id="9c0ea-240">はい</span><span class="sxs-lookup"><span data-stu-id="9c0ea-240">Yes</span></span>|<span data-ttu-id="9c0ea-241">○</span><span class="sxs-lookup"><span data-stu-id="9c0ea-241">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="9c0ea-242">初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-242">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="9c0ea-243">データ型を指定して、初期化子を指定しない場合[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は変数のデータ型の既定値を初期化します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-243">If you specify a data type but do not specify an initializer, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="9c0ea-244">次の表は、既定値に初期値を示します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-244">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="9c0ea-245">データ型</span><span class="sxs-lookup"><span data-stu-id="9c0ea-245">Data type</span></span>|<span data-ttu-id="9c0ea-246">既定値</span><span class="sxs-lookup"><span data-stu-id="9c0ea-246">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="9c0ea-247">すべての数値型 (を含む`Byte`と`SByte`)</span><span class="sxs-lookup"><span data-stu-id="9c0ea-247">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="9c0ea-248">0</span><span class="sxs-lookup"><span data-stu-id="9c0ea-248">0</span></span>|  
|`Char`|<span data-ttu-id="9c0ea-249">バイナリ 0</span><span class="sxs-lookup"><span data-stu-id="9c0ea-249">Binary 0</span></span>|  
|<span data-ttu-id="9c0ea-250">参照型はすべて (を含む`Object`、 `String`、およびすべての配列)</span><span class="sxs-lookup"><span data-stu-id="9c0ea-250">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="9c0ea-251">1 年 1 月 1 日の午前 12時 00分 (01/01/0001 12時 00分: 00 AM)</span><span class="sxs-lookup"><span data-stu-id="9c0ea-251">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="9c0ea-252">構造体の各要素は別々 の変数の場合と同様に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-252">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="9c0ea-253">配列の長さを宣言、要素を初期化しない場合は、各要素は別々 の変数の場合と同様に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-253">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="9c0ea-254">静的ローカル変数有効期間</span><span class="sxs-lookup"><span data-stu-id="9c0ea-254">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="9c0ea-255">A`Static`ローカル変数が宣言されているプロシージャの場合よりも有効期間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-255">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="9c0ea-256">変数の有効期間の境界は、プロシージャが宣言されていると、かどうかによって異なります。`Shared`します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-256">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="9c0ea-257">プロシージャの宣言</span><span class="sxs-lookup"><span data-stu-id="9c0ea-257">Procedure declaration</span></span>|<span data-ttu-id="9c0ea-258">初期化された変数</span><span class="sxs-lookup"><span data-stu-id="9c0ea-258">Variable initialized</span></span>|<span data-ttu-id="9c0ea-259">既存の変数を停止します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-259">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="9c0ea-260">モジュールで</span><span class="sxs-lookup"><span data-stu-id="9c0ea-260">In a module</span></span>|<span data-ttu-id="9c0ea-261">初めてのプロシージャが呼び出されたとき</span><span class="sxs-lookup"><span data-stu-id="9c0ea-261">The first time the procedure is called</span></span>|<span data-ttu-id="9c0ea-262">プログラムが実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-262">When your program stops execution</span></span>|  
|<span data-ttu-id="9c0ea-263">手順は、クラスまたは構造体は、します。`Shared`</span><span class="sxs-lookup"><span data-stu-id="9c0ea-263">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="9c0ea-264">最初に特定のインスタンスで、またはクラスまたは構造体自体でプロシージャが呼び出されます</span><span class="sxs-lookup"><span data-stu-id="9c0ea-264">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="9c0ea-265">プログラムが実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-265">When your program stops execution</span></span>|  
|<span data-ttu-id="9c0ea-266">クラスまたは構造体では、プロシージャはではありません。`Shared`</span><span class="sxs-lookup"><span data-stu-id="9c0ea-266">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="9c0ea-267">初めてのプロシージャが特定のインスタンスで呼び出されたとき</span><span class="sxs-lookup"><span data-stu-id="9c0ea-267">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="9c0ea-268">ガベージ コレクション (GC) のインスタンスを解放する場合</span><span class="sxs-lookup"><span data-stu-id="9c0ea-268">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="9c0ea-269">属性および修飾子</span><span class="sxs-lookup"><span data-stu-id="9c0ea-269">Attributes and Modifiers</span></span>  
 <span data-ttu-id="9c0ea-270">属性は、ローカル変数ではなく、メンバー変数にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-270">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="9c0ea-271">属性は、意味のあるローカル変数などの一時的なストレージではないアセンブリのメタデータに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-271">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="9c0ea-272">モジュール レベルでは使用できません、`Static`修飾子をメンバー変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-272">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="9c0ea-273">プロシージャ レベルでは使用できません`Shared`、 `Shadows`、 `ReadOnly`、 `WithEvents`、またはいずれかのアクセスをローカル変数を宣言する修飾子です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-273">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="9c0ea-274">指定することによって、変数にアクセスできるコードを指定する、`accessmodifier`です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-274">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="9c0ea-275">クラスとモジュールのメンバー (プロシージャ) の外部変数デフォルト プライベート アクセスには、構造体のメンバー変数の既定でパブリック アクセス。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-275">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="9c0ea-276">アクセス修飾子を使用してこれらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-276">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="9c0ea-277">ローカル変数 (プロシージャ) 内では、アクセス修飾子を使用できません。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-277">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="9c0ea-278">指定できます`WithEvents`のみメンバー変数ではなく、プロシージャ内のローカル変数。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-278">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="9c0ea-279">指定した場合`WithEvents`、変数のデータ型がない、特定のクラス型をする必要があります`Object`します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-279">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="9c0ea-280">配列を宣言することはできません`WithEvents`します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-280">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="9c0ea-281">イベントの詳細については、次を参照してください。[イベント](../../../visual-basic/programming-guide/language-features/events/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-281">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c0ea-282">コードをクラスの外部構造体、またはモジュール修飾する必要があります、クラス、構造体、モジュールの名前のメンバー変数の名前。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-282">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="9c0ea-283">プロシージャまたはブロックは、そのプロシージャまたはブロック内のローカル変数を参照できません外部をコードします。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-283">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="9c0ea-284">マネージ リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-284">Releasing Managed Resources</span></span>  
 <span data-ttu-id="9c0ea-285">ユーザー側でコードを追加せずに、.NET Framework のガベージ コレクターがマネージ リソースを破棄します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-285">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="9c0ea-286">ただし、ガベージ コレクターを待つことがなく管理されているリソースの破棄を強制できます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-286">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="9c0ea-287">クラスは、データベース接続やファイル ハンドル) などの特に役に立つと不足しているリソース上に保持している場合、次のガベージ コレクションが不要で使用されるクラスのインスタンスをクリーンアップするまで待機することがないできます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-287">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="9c0ea-288">クラスで実装が、<xref:System.IDisposable>ガベージ コレクションの前にリソースを解放する方法を提供するインターフェイス</xref:System.IDisposable>。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-288">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="9c0ea-289">そのインターフェイスを実装するクラスは、公開、`Dispose`メソッド強制的に貴重なリソースをすぐに解放するために呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-289">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="9c0ea-290">`Using`ステートメントがリソースを取得する、一連のステートメントを実行して、リソースを破棄し、プロセスを自動化します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-290">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="9c0ea-291">ただし、リソースを実装する必要があります、<xref:System.IDisposable>インターフェイス</xref:System.IDisposable>。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-291">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="9c0ea-292">詳細については、次を参照してください。 [Using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-292">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c0ea-293">例</span><span class="sxs-lookup"><span data-stu-id="9c0ea-293">Example</span></span>  
 <span data-ttu-id="9c0ea-294">次の例では、変数を宣言を使用して、`Dim`さまざまなオプションを含むステートメント。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-294">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 <span data-ttu-id="9c0ea-295">[!code-vb[VbVbalrStatements #&141;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9c0ea-295">[!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c0ea-296">例</span><span class="sxs-lookup"><span data-stu-id="9c0ea-296">Example</span></span>  
 <span data-ttu-id="9c0ea-297">次の例は、1 ~ 30 の素数を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-297">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="9c0ea-298">ローカル変数のスコープには、コードのコメントが記載されています。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-298">The scope of local variables is described in code comments.</span></span>  
  
 <span data-ttu-id="9c0ea-299">[!code-vb[VbVbalrStatements #&142;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="9c0ea-299">[!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c0ea-300">例</span><span class="sxs-lookup"><span data-stu-id="9c0ea-300">Example</span></span>  
 <span data-ttu-id="9c0ea-301">次の例では、`speedValue`変数はクラス レベルで宣言します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="9c0ea-302">`Private`変数を宣言するキーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="9c0ea-303">変数は、の任意のプロシージャからアクセスできる、`Car`クラスです。</span><span class="sxs-lookup"><span data-stu-id="9c0ea-303">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 <span data-ttu-id="9c0ea-304">[!code-vb[VbVbalrStatements #&144;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="9c0ea-304">[!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="9c0ea-305">[!code-vb[VbVbalrStatements #&145;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="9c0ea-305">[!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0ea-306">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c0ea-306">See Also</span></span>  
 <span data-ttu-id="9c0ea-307">[Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-307">[Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="9c0ea-308"> [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-308"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="9c0ea-309"> [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-309"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="9c0ea-310"> [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-310"> [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="9c0ea-311"> [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-311"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="9c0ea-312"> [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-312"> [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="9c0ea-313"> [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-313"> [Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="9c0ea-314"> [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-314"> [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="9c0ea-315"> [オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-315"> [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="9c0ea-316"> [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-316"> [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="9c0ea-317"> [オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-317"> [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="9c0ea-318"> [方法: オブジェクト初期化子を使用してオブジェクトを宣言](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md) </span><span class="sxs-lookup"><span data-stu-id="9c0ea-318"> [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md) </span></span>  
<span data-ttu-id="9c0ea-319"> [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="9c0ea-319"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span></span>

