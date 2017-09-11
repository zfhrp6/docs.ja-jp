---
title: "Visual Basic での変数宣言 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables, declarations
- Dim statement, variable declaration
- declaring variables
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime, variables
- variables [Visual Basic], lifetime
- access levels, variables
- scope, declaration statements
- variables [Visual Basic], access level
- local variables, declarations
- scope, variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: dac536b99eb4515c75381dc4e28720a92e1001f0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="4a8d9-102">Visual Basic での変数宣言</span><span class="sxs-lookup"><span data-stu-id="4a8d9-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="4a8d9-103">名前と特性を指定する変数を宣言するとします。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="4a8d9-104">変数の宣言ステートメントは、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-104">The declaration statement for variables is the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="4a8d9-105">その場所や内容は、変数の特性を決定します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="4a8d9-106">変数の名前付け規則と考慮事項では、次を参照してください。[宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-106">For variable naming rules and considerations, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="4a8d9-107">宣言のレベル</span><span class="sxs-lookup"><span data-stu-id="4a8d9-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="4a8d9-108">ローカル変数とメンバー変数</span><span class="sxs-lookup"><span data-stu-id="4a8d9-108">Local and Member Variables</span></span>  
 <span data-ttu-id="4a8d9-109">A*ローカル変数*プロシージャ内で宣言されている&1; つです。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="4a8d9-110">A*メンバー変数*のメンバーである、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]型クラス、構造体、またはモジュールに内部プロシージャ内ではありませんが、クラス、構造体、またはモジュール内のモジュール レベルで宣言されています。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-110">A *member variable* is a member of a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="4a8d9-111">共有し、インスタンス変数</span><span class="sxs-lookup"><span data-stu-id="4a8d9-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="4a8d9-112">クラスまたは構造体のメンバー変数のカテゴリが共有されるかどうかに依存します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="4a8d9-113">宣言されている場合、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)は、キーワード、*共有変数*、1 つのコピーがクラスまたは構造体のすべてのインスタンス間で共有内に存在するとします。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-113">If it is declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="4a8d9-114">以外の場合は、*インスタンス変数*、およびクラスまたは構造体の各インスタンスの独立したコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="4a8d9-115">インスタンス変数のコピーは、クラスまたは構造体が作成されたインスタンスでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="4a8d9-116">これは、クラスまたは構造体の他の任意のインスタンスにインスタンス変数のコピーに依存しません。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="4a8d9-117">データ型の宣言</span><span class="sxs-lookup"><span data-stu-id="4a8d9-117">Declaring Data Type</span></span>  
 <span data-ttu-id="4a8d9-118">[として](../../../../visual-basic/language-reference/statements/as-clause.md)宣言ステートメントに句を使用すると、データ型またはオブジェクトを宣言する変数の型を定義します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-118">The [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="4a8d9-119">変数の種類を次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-119">You can specify any of the following types for a variable:</span></span>  
  
-   <span data-ttu-id="4a8d9-120">基本データ型など、 `Boolean`、 `Long`、または`Decimal`</span><span class="sxs-lookup"><span data-stu-id="4a8d9-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
-   <span data-ttu-id="4a8d9-121">配列や構造体などの複合データ型</span><span class="sxs-lookup"><span data-stu-id="4a8d9-121">A composite data type, such as an array or structure</span></span>  
  
-   <span data-ttu-id="4a8d9-122">オブジェクトの種類、または、アプリケーションまたは別のアプリケーションのいずれかを定義したクラス</span><span class="sxs-lookup"><span data-stu-id="4a8d9-122">An object type, or class, defined either in your application or in another application</span></span>  
  
-   <span data-ttu-id="4a8d9-123">A[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]クラスなど、<xref:System.Windows.Forms.Label>または<xref:System.Windows.Forms.TextBox></xref:System.Windows.Forms.TextBox></xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="4a8d9-123">A [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
-   <span data-ttu-id="4a8d9-124">インターフェイス型など、<xref:System.IComparable>または<xref:System.IDisposable></xref:System.IDisposable></xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="4a8d9-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="4a8d9-125">データ型を繰り返さなくても、1 つのステートメントで複数の変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="4a8d9-126">次のステートメントでは、変数で`i`、 `j`、および`k`型として宣言されて`Integer`、`l`と`m`として`Long`、および`x`と`y`として`Single`:</span><span class="sxs-lookup"><span data-stu-id="4a8d9-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="4a8d9-127">データ型の詳細については、次を参照してください。[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-127">For more information on data types, see [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span></span> <span data-ttu-id="4a8d9-128">オブジェクトの詳細については、次を参照してください。[オブジェクトおよびクラス](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)と[コンポーネントを使用したプログラミング](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-128">For more information on objects, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) and [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="4a8d9-129">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="4a8d9-129">Local Type Inference</span></span>  
 <span data-ttu-id="4a8d9-130">*型の推論*なしで宣言されたローカル変数のデータ型を決定するために使用、`As`句。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="4a8d9-131">コンパイラは、初期化式の型から変数の型を推論します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="4a8d9-132">これにより、型を明示的に指定せずに変数を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="4a8d9-133">次の例では両方とも`num1`と`num2`整数として厳密に型指定します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 <span data-ttu-id="4a8d9-134">[!code-vb[VbVbalrTypeInference&#1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4a8d9-134">[!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]</span></span>  
  
 <span data-ttu-id="4a8d9-135">ローカル型推論を使用する場合は、`Option Infer`に設定する必要があります`On`します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-135">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="4a8d9-136">詳細については、次を参照してください。[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)と[Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="4a8d9-137">宣言された変数の特性</span><span class="sxs-lookup"><span data-stu-id="4a8d9-137">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="4a8d9-138">*有効期間*変数は、一定時間その中に、使用可能です。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-138">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="4a8d9-139">一般に、変数は、(手順やクラスで) 宣言された要素が存在し続けます限り存在します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-139">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="4a8d9-140">変数がそのコンテナー要素の有効期間よりも長く必要がない場合は、宣言で特別な対応を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-140">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="4a8d9-141">含めることができますが、変数は、引き続きそのコンテナー要素よりも長く存在する必要がある場合、`Static`または`Shared`キーワードでその`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-141">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="4a8d9-142">詳細については、次を参照してください。 [Visual Basic における有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-142">For more information, see [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="4a8d9-143">*スコープ*の変数の名前を修飾せずに参照できるすべてのコードのセットです。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-143">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="4a8d9-144">変数のスコープは、宣言されている場所によって決まります。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-144">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="4a8d9-145">指定したリージョンに置かれているコードは、その名前を修飾しなくても、そのリージョンで定義されている変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-145">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="4a8d9-146">詳細については、次を参照してください。 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-146">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="4a8d9-147">変数の*アクセス レベル*へのアクセス許可のあるコードの範囲は、です。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-147">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="4a8d9-148">これは、アクセス修飾子によって決まります (よう[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)) で使用する、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-148">This is determined by the access modifier (such as [Public](../../../../visual-basic/language-reference/modifiers/public.md) or [Private](../../../../visual-basic/language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="4a8d9-149">詳細については、次を参照してください。 [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。</span><span class="sxs-lookup"><span data-stu-id="4a8d9-149">For more information, see [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a8d9-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a8d9-150">See Also</span></span>  
 <span data-ttu-id="4a8d9-151">[方法: 新しい変数を作成](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md) </span><span class="sxs-lookup"><span data-stu-id="4a8d9-151">[How to: Create a New Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md) </span></span>  
<span data-ttu-id="4a8d9-152"> [方法: 変数に出入りするデータを移動](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="4a8d9-152"> [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span></span>  
<span data-ttu-id="4a8d9-153"> [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="4a8d9-153"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="4a8d9-154"> [保護されています。](../../../../visual-basic/language-reference/modifiers/protected.md) </span><span class="sxs-lookup"><span data-stu-id="4a8d9-154"> [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) </span></span>  
<span data-ttu-id="4a8d9-155"> [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) </span><span class="sxs-lookup"><span data-stu-id="4a8d9-155"> [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) </span></span>  
<span data-ttu-id="4a8d9-156"> [静的](../../../../visual-basic/language-reference/modifiers/static.md) </span><span class="sxs-lookup"><span data-stu-id="4a8d9-156"> [Static](../../../../visual-basic/language-reference/modifiers/static.md) </span></span>  
<span data-ttu-id="4a8d9-157"> [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="4a8d9-157"> [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span></span>  
<span data-ttu-id="4a8d9-158"> [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="4a8d9-158"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="4a8d9-159"> [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)</span><span class="sxs-lookup"><span data-stu-id="4a8d9-159"> [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)</span></span>
