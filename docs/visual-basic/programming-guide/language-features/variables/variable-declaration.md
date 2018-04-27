---
title: Visual Basic での変数宣言
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8edd0b65b08efd437cc35e8f58ed7ed423736920
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="202e6-102">Visual Basic での変数宣言</span><span class="sxs-lookup"><span data-stu-id="202e6-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="202e6-103">名前と特性を指定する変数を宣言するとします。</span><span class="sxs-lookup"><span data-stu-id="202e6-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="202e6-104">変数の宣言ステートメントは、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="202e6-104">The declaration statement for variables is the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="202e6-105">その場所と内容は、変数の特性を決定します。</span><span class="sxs-lookup"><span data-stu-id="202e6-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="202e6-106">変数の名前付け規則と考慮事項について、次を参照してください。[宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="202e6-106">For variable naming rules and considerations, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="202e6-107">宣言のレベル</span><span class="sxs-lookup"><span data-stu-id="202e6-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="202e6-108">ローカルとメンバー変数</span><span class="sxs-lookup"><span data-stu-id="202e6-108">Local and Member Variables</span></span>  
 <span data-ttu-id="202e6-109">A*ローカル変数*はプロシージャ内で宣言されている 1 つです。</span><span class="sxs-lookup"><span data-stu-id="202e6-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="202e6-110">A*メンバー変数*; Visual Basic の型のメンバーは、モジュール レベル、そのクラス、構造体、またはモジュールの内部プロシージャ内ではありませんが、クラス、構造体、またはモジュール内で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="202e6-110">A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="202e6-111">共有し、インスタンス変数</span><span class="sxs-lookup"><span data-stu-id="202e6-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="202e6-112">クラスまたは構造体のメンバー変数のカテゴリが共有されているかどうかに依存します。</span><span class="sxs-lookup"><span data-stu-id="202e6-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="202e6-113">宣言されている場合、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)キーワードでは、*共有変数*、1 つのコピーがクラスまたは構造体のすべてのインスタンス間で共有内に存在するとします。</span><span class="sxs-lookup"><span data-stu-id="202e6-113">If it is declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="202e6-114">以外の場合は、*インスタンス変数*、クラスまたは構造体のインスタンスごとの個別のコピーが作成されたとします。</span><span class="sxs-lookup"><span data-stu-id="202e6-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="202e6-115">インスタンス変数のコピーは、クラスまたは構造体が作成されたインスタンスでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="202e6-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="202e6-116">クラスまたは構造体のインスタンスをすべてのインスタンス変数のコピーの関係。</span><span class="sxs-lookup"><span data-stu-id="202e6-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="202e6-117">データ型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="202e6-117">Declaring Data Type</span></span>  
 <span data-ttu-id="202e6-118">[として](../../../../visual-basic/language-reference/statements/as-clause.md)宣言ステートメントの句では、データ型またはオブジェクトを宣言する変数の型を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="202e6-118">The [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="202e6-119">変数の種類は次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="202e6-119">You can specify any of the following types for a variable:</span></span>  
  
-   <span data-ttu-id="202e6-120">基本データ型など`Boolean`、 `Long`、または `Decimal`</span><span class="sxs-lookup"><span data-stu-id="202e6-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
-   <span data-ttu-id="202e6-121">配列や構造体などの複合データ型</span><span class="sxs-lookup"><span data-stu-id="202e6-121">A composite data type, such as an array or structure</span></span>  
  
-   <span data-ttu-id="202e6-122">オブジェクトの種類、または別のアプリケーションまたはアプリケーションで定義されているクラス</span><span class="sxs-lookup"><span data-stu-id="202e6-122">An object type, or class, defined either in your application or in another application</span></span>  
  
-   <span data-ttu-id="202e6-123">A[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラスなど<xref:System.Windows.Forms.Label>または <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="202e6-123">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
-   <span data-ttu-id="202e6-124">インターフェイス型など、<xref:System.IComparable>または <xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="202e6-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="202e6-125">データ型を繰り返すことがなく 1 つのステートメントで複数の変数を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="202e6-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="202e6-126">次のステートメントでは、変数で`i`、 `j`、および`k`型として宣言されて`Integer`、`l`と`m`として`Long`、および`x`と`y`として`Single`:</span><span class="sxs-lookup"><span data-stu-id="202e6-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="202e6-127">データ型の詳細については、次を参照してください。[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="202e6-127">For more information on data types, see [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span></span> <span data-ttu-id="202e6-128">オブジェクトの詳細については、次を参照してください。[クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)と[コンポーネントを使用したプログラミング](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)です。</span><span class="sxs-lookup"><span data-stu-id="202e6-128">For more information on objects, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) and [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="202e6-129">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="202e6-129">Local Type Inference</span></span>  
 <span data-ttu-id="202e6-130">*型推論*なしで宣言されたローカル変数のデータ型を決定するために使用、`As`句。</span><span class="sxs-lookup"><span data-stu-id="202e6-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="202e6-131">コンパイラは、初期化式の型から変数の型を推論します。</span><span class="sxs-lookup"><span data-stu-id="202e6-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="202e6-132">これにより、型を明示的に指定せずに変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="202e6-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="202e6-133">次の例では、両方とも`num1`と`num2`整数値として厳密に型指定します。</span><span class="sxs-lookup"><span data-stu-id="202e6-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 <span data-ttu-id="202e6-134">ローカル型推論を使用する場合は、`Option Infer`に設定する必要があります`On`です。</span><span class="sxs-lookup"><span data-stu-id="202e6-134">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="202e6-135">詳細については、「[ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」と「[Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="202e6-135">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="202e6-136">宣言された変数の特性</span><span class="sxs-lookup"><span data-stu-id="202e6-136">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="202e6-137">*有効期間*変数の期間が中に、使用可能です。</span><span class="sxs-lookup"><span data-stu-id="202e6-137">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="202e6-138">一般に、プロシージャまたはクラス) などを宣言した要素が存在し続けます限り、変数が存在します。</span><span class="sxs-lookup"><span data-stu-id="202e6-138">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="202e6-139">変数がそのコンテナー要素の有効期間よりも長く必要がない場合は、宣言で特別な処理を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="202e6-139">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="202e6-140">含めることができる場合は、変数は、引き続きそのコンテナー要素よりも長く存在する必要がある場合、`Static`または`Shared`キーワードでその`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="202e6-140">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="202e6-141">詳細については、次を参照してください。 [Visual Basic における有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)です。</span><span class="sxs-lookup"><span data-stu-id="202e6-141">For more information, see [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="202e6-142">*スコープ*変数の名前を修飾せずに参照できるすべてのコードのセットです。</span><span class="sxs-lookup"><span data-stu-id="202e6-142">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="202e6-143">変数のスコープは、宣言されている場所によって決まります。</span><span class="sxs-lookup"><span data-stu-id="202e6-143">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="202e6-144">特定の地域にあるコードでは、その名前を修飾することがなく、その地域で定義されている変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="202e6-144">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="202e6-145">詳細については、次を参照してください。 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)です。</span><span class="sxs-lookup"><span data-stu-id="202e6-145">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="202e6-146">変数の*アクセス レベル*へのアクセス許可のあるコードの範囲がします。</span><span class="sxs-lookup"><span data-stu-id="202e6-146">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="202e6-147">これは、アクセス修飾子によって決定されます (など[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)) で使用する、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="202e6-147">This is determined by the access modifier (such as [Public](../../../../visual-basic/language-reference/modifiers/public.md) or [Private](../../../../visual-basic/language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="202e6-148">詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="202e6-148">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202e6-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="202e6-149">See Also</span></span>  
 [<span data-ttu-id="202e6-150">方法 : 新しい変数を作成する</span><span class="sxs-lookup"><span data-stu-id="202e6-150">How to: Create a New Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)  
 [<span data-ttu-id="202e6-151">方法 : 変数に値を格納する、および変数から値を取得する</span><span class="sxs-lookup"><span data-stu-id="202e6-151">How to: Move Data Into and Out of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [<span data-ttu-id="202e6-152">データの種類</span><span class="sxs-lookup"><span data-stu-id="202e6-152">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="202e6-153">Protected</span><span class="sxs-lookup"><span data-stu-id="202e6-153">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="202e6-154">Friend</span><span class="sxs-lookup"><span data-stu-id="202e6-154">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="202e6-155">Static</span><span class="sxs-lookup"><span data-stu-id="202e6-155">Static</span></span>](../../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="202e6-156">宣言された要素の特性</span><span class="sxs-lookup"><span data-stu-id="202e6-156">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="202e6-157">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="202e6-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="202e6-158">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="202e6-158">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
