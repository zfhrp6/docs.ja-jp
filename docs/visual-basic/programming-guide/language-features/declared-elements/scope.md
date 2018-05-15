---
title: Visual Basic におけるスコープ
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: d6692379626d787b728d6e92bd447c4a96e6680e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="816f4-102">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="816f4-102">Scope in Visual Basic</span></span>
<span data-ttu-id="816f4-103">*スコープ*一連の名前に修飾子またはを通じて使用できるようにせずに参照できるすべてのコードは、宣言された要素の[Imports ステートメント (.NET Namespace よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="816f4-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="816f4-104">要素は、次のレベルのいずれかのスコープを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="816f4-104">An element can have scope at one of the following levels:</span></span>  
  
|<span data-ttu-id="816f4-105">レベル</span><span class="sxs-lookup"><span data-stu-id="816f4-105">Level</span></span>|<span data-ttu-id="816f4-106">説明</span><span class="sxs-lookup"><span data-stu-id="816f4-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="816f4-107">ブロック スコープ</span><span class="sxs-lookup"><span data-stu-id="816f4-107">Block scope</span></span>|<span data-ttu-id="816f4-108">宣言されたブロック、コード内でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="816f4-108">Available only within the code block in which it is declared</span></span>|  
|<span data-ttu-id="816f4-109">プロシージャ スコープ</span><span class="sxs-lookup"><span data-stu-id="816f4-109">Procedure scope</span></span>|<span data-ttu-id="816f4-110">宣言されているプロシージャ内のすべてのコードで使用可能</span><span class="sxs-lookup"><span data-stu-id="816f4-110">Available to all code within the procedure in which it is declared</span></span>|  
|<span data-ttu-id="816f4-111">モジュール スコープ</span><span class="sxs-lookup"><span data-stu-id="816f4-111">Module scope</span></span>|<span data-ttu-id="816f4-112">モジュール、クラス、または構造体が宣言されているすべてのコードで使用可能</span><span class="sxs-lookup"><span data-stu-id="816f4-112">Available to all code within the module, class, or structure in which it is declared</span></span>|  
|<span data-ttu-id="816f4-113">Namespace スコープ</span><span class="sxs-lookup"><span data-stu-id="816f4-113">Namespace scope</span></span>|<span data-ttu-id="816f4-114">宣言されている名前空間内のすべてのコードに使用可能</span><span class="sxs-lookup"><span data-stu-id="816f4-114">Available to all code in the namespace in which it is declared</span></span>|  
  
 <span data-ttu-id="816f4-115">これらのレベルのスコープから進行状況を最も狭い (ブロック)、最も幅の広い (名前空間) に場所*狭いスコープ*修飾なしの要素に参照できるコードの最小セットのことを意味します。</span><span class="sxs-lookup"><span data-stu-id="816f4-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="816f4-116">詳細については、このページで「レベルのスコープ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816f4-116">For more information, see "Levels of Scope" on this page.</span></span>  
  
## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="816f4-117">スコープを指定して、変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="816f4-117">Specifying Scope and Defining Variables</span></span>  
 <span data-ttu-id="816f4-118">宣言する場合は、要素のスコープを指定します。</span><span class="sxs-lookup"><span data-stu-id="816f4-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="816f4-119">スコープは、次の要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="816f4-119">The scope can depend on the following factors:</span></span>  
  
-   <span data-ttu-id="816f4-120">要素を宣言する地域 (ブロック、プロシージャ、モジュール、クラスまたは構造体)</span><span class="sxs-lookup"><span data-stu-id="816f4-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>  
  
-   <span data-ttu-id="816f4-121">要素の宣言を含む名前空間</span><span class="sxs-lookup"><span data-stu-id="816f4-121">The namespace containing the element's declaration</span></span>  
  
-   <span data-ttu-id="816f4-122">要素の宣言するアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="816f4-122">The access level you declare for the element</span></span>  
  
 <span data-ttu-id="816f4-123">これを行うために名前が同じで別のスコープを持つ変数を定義するときは注意して、予期しない結果に可能性があります。</span><span class="sxs-lookup"><span data-stu-id="816f4-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="816f4-124">詳細については、「 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816f4-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="levels-of-scope"></a><span data-ttu-id="816f4-125">スコープのレベル</span><span class="sxs-lookup"><span data-stu-id="816f4-125">Levels of Scope</span></span>  
 <span data-ttu-id="816f4-126">プログラミング要素は、その宣言領域全体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="816f4-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="816f4-127">同じリージョン内のすべてのコードは、その名前を修飾せず、要素を参照できます。</span><span class="sxs-lookup"><span data-stu-id="816f4-127">All code in the same region can refer to the element without qualifying its name.</span></span>  
  
### <a name="block-scope"></a><span data-ttu-id="816f4-128">ブロック スコープ</span><span class="sxs-lookup"><span data-stu-id="816f4-128">Block Scope</span></span>  
 <span data-ttu-id="816f4-129">ブロックは、開始および終了して、次のような宣言ステートメントで囲まれたステートメントのセットを示します。</span><span class="sxs-lookup"><span data-stu-id="816f4-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>  
  
-   <span data-ttu-id="816f4-130">`Do` および `Loop`</span><span class="sxs-lookup"><span data-stu-id="816f4-130">`Do` and `Loop`</span></span>  
  
-   <span data-ttu-id="816f4-131">`For` [`Each`] と `Next`</span><span class="sxs-lookup"><span data-stu-id="816f4-131">`For` [`Each`] and `Next`</span></span>  
  
-   <span data-ttu-id="816f4-132">`If` および `End If`</span><span class="sxs-lookup"><span data-stu-id="816f4-132">`If` and `End If`</span></span>  
  
-   <span data-ttu-id="816f4-133">`Select` および `End Select`</span><span class="sxs-lookup"><span data-stu-id="816f4-133">`Select` and `End Select`</span></span>  
  
-   <span data-ttu-id="816f4-134">`SyncLock` および `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="816f4-134">`SyncLock` and `End SyncLock`</span></span>  
  
-   <span data-ttu-id="816f4-135">`Try` および `End Try`</span><span class="sxs-lookup"><span data-stu-id="816f4-135">`Try` and `End Try`</span></span>  
  
-   <span data-ttu-id="816f4-136">`While` および `End While`</span><span class="sxs-lookup"><span data-stu-id="816f4-136">`While` and `End While`</span></span>  
  
-   <span data-ttu-id="816f4-137">`With` および `End With`</span><span class="sxs-lookup"><span data-stu-id="816f4-137">`With` and `End With`</span></span>  
  
 <span data-ttu-id="816f4-138">ブロック内で変数を宣言する場合は、そのブロック内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="816f4-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="816f4-139">次の例では、整数型の変数のスコープで`cube`間ブロック`If`と`End If`を参照することが不要になったと`cube`ブロックからの実行のパスとします。</span><span class="sxs-lookup"><span data-stu-id="816f4-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  <span data-ttu-id="816f4-140">変数のスコープは、ブロックに制限されている場合でもその有効期間はまだ全体のプロシージャのです。</span><span class="sxs-lookup"><span data-stu-id="816f4-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="816f4-141">処理中に、ブロックを複数回入力した場合、各ブロック変数は、前の値を保持します。</span><span class="sxs-lookup"><span data-stu-id="816f4-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="816f4-142">このようなケースで予期しない結果を回避するのには、ブロックの先頭でブロック変数を初期化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="816f4-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>  
  
### <a name="procedure-scope"></a><span data-ttu-id="816f4-143">プロシージャ スコープ</span><span class="sxs-lookup"><span data-stu-id="816f4-143">Procedure Scope</span></span>  
 <span data-ttu-id="816f4-144">プロシージャ内で宣言された要素では、そのプロシージャの外部使用できません。</span><span class="sxs-lookup"><span data-stu-id="816f4-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="816f4-145">宣言を含むプロシージャのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="816f4-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="816f4-146">このレベルでの変数とも呼ばれる*ローカル変数*です。</span><span class="sxs-lookup"><span data-stu-id="816f4-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="816f4-147">宣言することで、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)、有無にかかわらず、[静的](../../../../visual-basic/language-reference/modifiers/static.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="816f4-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>  
  
 <span data-ttu-id="816f4-148">プロシージャとブロックのスコープは密接に関連します。</span><span class="sxs-lookup"><span data-stu-id="816f4-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="816f4-149">そのプロシージャ内で任意のブロックの外側ではなく、プロシージャ内部変数を宣言する場合は、プロシージャ全体をブロックがここでは、ブロック スコープを持つ、変数の考えることができます。</span><span class="sxs-lookup"><span data-stu-id="816f4-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="816f4-150">いる場合でも、すべてのローカル要素`Static`変数は、表示されている手順にプライベートです。</span><span class="sxs-lookup"><span data-stu-id="816f4-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="816f4-151">使用しているすべての要素を宣言することはできません、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)プロシージャ内でキーワード。</span><span class="sxs-lookup"><span data-stu-id="816f4-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>  
  
### <a name="module-scope"></a><span data-ttu-id="816f4-152">モジュール スコープ</span><span class="sxs-lookup"><span data-stu-id="816f4-152">Module Scope</span></span>  
 <span data-ttu-id="816f4-153">便宜上、1 つの用語*モジュール レベル*モジュール、クラス、および構造体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="816f4-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="816f4-154">このレベルの要素を宣言するには、モジュール、クラスまたは構造体が、すべてのプロシージャまたはブロックの外部で宣言ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="816f4-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>  
  
 <span data-ttu-id="816f4-155">モジュール レベルで宣言すると、選択したアクセス レベルは、スコープを決定します。</span><span class="sxs-lookup"><span data-stu-id="816f4-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="816f4-156">モジュール、クラスまたは構造体を含む名前空間もスコープに影響します。</span><span class="sxs-lookup"><span data-stu-id="816f4-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>  
  
 <span data-ttu-id="816f4-157">要素が宣言した[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)アクセス レベルがある別のモジュール内のコードではなく、そのモジュール内のすべてのプロシージャにします。</span><span class="sxs-lookup"><span data-stu-id="816f4-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="816f4-158">`Dim`モジュール レベルのステートメントの既定値`Private`場合は、アクセス レベル キーワードを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="816f4-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="816f4-159">ただし、行うことができます、スコープとアクセス レベルより明確を使用して、`Private`キーワード、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="816f4-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>  
  
 <span data-ttu-id="816f4-160">次の例では、モジュールで定義されているすべてのプロシージャが文字列変数を参照できます`strMsg`です。</span><span class="sxs-lookup"><span data-stu-id="816f4-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="816f4-161">2 番目のプロシージャが呼び出されると、文字列変数の内容が表示されます`strMsg` ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="816f4-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a><span data-ttu-id="816f4-162">Namespace スコープ</span><span class="sxs-lookup"><span data-stu-id="816f4-162">Namespace Scope</span></span>  
 <span data-ttu-id="816f4-163">モジュールを使用してレベルにある要素を宣言する場合、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)または[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)要素が宣言されている名前空間全体ですべてのプロシージャを使用可能になったら、キーワード。</span><span class="sxs-lookup"><span data-stu-id="816f4-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="816f4-164">次の部分を変更前の例では、文字列変数に`strMsg`宣言の名前空間内の任意の場所のコードによって参照することができます。</span><span class="sxs-lookup"><span data-stu-id="816f4-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 <span data-ttu-id="816f4-165">Namespace スコープには、入れ子になった名前空間が含まれています。</span><span class="sxs-lookup"><span data-stu-id="816f4-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="816f4-166">名前空間内で使用可能な要素もその名前空間内に入れ子に名前空間の中から使用できます。</span><span class="sxs-lookup"><span data-stu-id="816f4-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>  
  
 <span data-ttu-id="816f4-167">いずれかのプロジェクトが含まれない場合[Namespace ステートメント](../../../../visual-basic/language-reference/statements/namespace-statement.md)s、プロジェクト内のすべてが同じ名前空間。</span><span class="sxs-lookup"><span data-stu-id="816f4-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="816f4-168">ここでは、名前空間のスコープはようなもののプロジェクト スコープ。</span><span class="sxs-lookup"><span data-stu-id="816f4-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="816f4-169">`Public` モジュール、クラス、または構造内の要素も、プロジェクトを参照する他のプロジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="816f4-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>  
  
## <a name="choice-of-scope"></a><span data-ttu-id="816f4-170">スコープの選択</span><span class="sxs-lookup"><span data-stu-id="816f4-170">Choice of Scope</span></span>  
 <span data-ttu-id="816f4-171">変数を宣言するときにおく必要がありますに注意、次の点スコープを選択します。</span><span class="sxs-lookup"><span data-stu-id="816f4-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>  
  
### <a name="advantages-of-local-variables"></a><span data-ttu-id="816f4-172">ローカル変数の利点</span><span class="sxs-lookup"><span data-stu-id="816f4-172">Advantages of Local Variables</span></span>  
 <span data-ttu-id="816f4-173">ローカル変数は、次の理由ですべての種類の一時的な計算は、適切な選択を。</span><span class="sxs-lookup"><span data-stu-id="816f4-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>  
  
-   <span data-ttu-id="816f4-174">**名前の競合回避します。**</span><span class="sxs-lookup"><span data-stu-id="816f4-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="816f4-175">ローカルの変数名が競合を受けやすくなります。</span><span class="sxs-lookup"><span data-stu-id="816f4-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="816f4-176">たとえば、という名前の変数を含むいくつかの異なる手順を作成することができます`intTemp`です。</span><span class="sxs-lookup"><span data-stu-id="816f4-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="816f4-177">各いる限り`intTemp`各プロシージャが、独自のバージョンのみを認識する、ローカル変数として宣言されての`intTemp`します。</span><span class="sxs-lookup"><span data-stu-id="816f4-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="816f4-178">任意の 1 つのプロシージャは、ローカルの値を変更できます`intTemp`影響を与えずに`intTemp`他のプロシージャ内の変数です。</span><span class="sxs-lookup"><span data-stu-id="816f4-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>  
  
-   <span data-ttu-id="816f4-179">**メモリ使用量。**</span><span class="sxs-lookup"><span data-stu-id="816f4-179">**Memory Consumption.**</span></span> <span data-ttu-id="816f4-180">ローカル変数は、そのプロシージャの実行中にのみ、メモリを消費します。</span><span class="sxs-lookup"><span data-stu-id="816f4-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="816f4-181">プロシージャが呼び出し元のコードに戻るときに、自らのメモリは解放されます。</span><span class="sxs-lookup"><span data-stu-id="816f4-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="816f4-182">これに対し、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)と[静的](../../../../visual-basic/language-reference/modifiers/static.md)変数、アプリケーションの実行が停止されるまで、メモリ リソースを消費するので、使用に必要な場合のみです。</span><span class="sxs-lookup"><span data-stu-id="816f4-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="816f4-183">*インスタンス変数*間メモリを消費、インスタンスが存在しているが、ローカル変数より効率的な可能性のあるより効率的`Shared`または`Static`変数。</span><span class="sxs-lookup"><span data-stu-id="816f4-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>  
  
### <a name="minimizing-scope"></a><span data-ttu-id="816f4-184">スコープを最小限に抑える</span><span class="sxs-lookup"><span data-stu-id="816f4-184">Minimizing Scope</span></span>  
 <span data-ttu-id="816f4-185">一般に、すべての変数または定数を宣言するとき、推奨されるプログラミング可能な幅の狭いスコープを作成することを (ブロック スコープは最も狭いです)。</span><span class="sxs-lookup"><span data-stu-id="816f4-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="816f4-186">これにより、メモリを節約できます、誤って間違った変数を参照する、コードの可能性を最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="816f4-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="816f4-187">同様に、ある変数を宣言する必要があります[静的](../../../../visual-basic/language-reference/modifiers/static.md)プロシージャ呼び出しの間には、その値を保持するために必要な場合のみです。</span><span class="sxs-lookup"><span data-stu-id="816f4-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816f4-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="816f4-188">See Also</span></span>  
 [<span data-ttu-id="816f4-189">宣言された要素の特性</span><span class="sxs-lookup"><span data-stu-id="816f4-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="816f4-190">方法: 変数のスコープを制御する</span><span class="sxs-lookup"><span data-stu-id="816f4-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [<span data-ttu-id="816f4-191">Visual Basic における有効期間</span><span class="sxs-lookup"><span data-stu-id="816f4-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="816f4-192">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="816f4-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="816f4-193">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="816f4-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="816f4-194">変数宣言</span><span class="sxs-lookup"><span data-stu-id="816f4-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
