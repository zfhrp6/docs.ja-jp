---
title: Shared (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fce13c308a449e63eacc2bc4c94c274c7e25506a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="shared-visual-basic"></a><span data-ttu-id="010fe-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="010fe-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="010fe-103">1 つまたは複数の宣言されたプログラミング要素がクラスまたは構造体全体、いないに関連付けられているクラスまたは構造体の特定のインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="010fe-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="010fe-104">コメント</span><span class="sxs-lookup"><span data-stu-id="010fe-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="010fe-105">共有を使用する場合</span><span class="sxs-lookup"><span data-stu-id="010fe-105">When to Use Shared</span></span>  
 <span data-ttu-id="010fe-106">クラスまたは構造体のメンバーを共有できるように、すべてのインスタンスではなくより*非共有*、各インスタンスが独自のコピーを保持します。</span><span class="sxs-lookup"><span data-stu-id="010fe-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="010fe-107">これは、変数の値は、アプリケーション全体に適用される場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="010fe-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="010fe-108">その変数を宣言する場合`Shared`、すべてのインスタンスが同じストレージの場所にアクセスし、およびすべてのインスタンスにアクセス、更新された値が 1 つのインスタンスは、変数の値を変更する場合。</span><span class="sxs-lookup"><span data-stu-id="010fe-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="010fe-109">共有しても、メンバーのアクセス レベルは変わりません。</span><span class="sxs-lookup"><span data-stu-id="010fe-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="010fe-110">たとえば、クラス メンバーを共有できるおよびプライベート (クラス内からのみアクセスできる)、または非共有と公開します。</span><span class="sxs-lookup"><span data-stu-id="010fe-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="010fe-111">詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="010fe-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="010fe-112">ルール</span><span class="sxs-lookup"><span data-stu-id="010fe-112">Rules</span></span>  
  
-   <span data-ttu-id="010fe-113">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="010fe-113">**Declaration Context.**</span></span> <span data-ttu-id="010fe-114">`Shared` は、モジュール レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="010fe-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="010fe-115">つまりの宣言コンテキスト、`Shared`要素は、クラスまたは構造体にある必要があるあり、ソース ファイル、名前空間、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="010fe-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="010fe-116">**結合された修飾子。**</span><span class="sxs-lookup"><span data-stu-id="010fe-116">**Combined Modifiers.**</span></span> <span data-ttu-id="010fe-117">指定することはできません`Shared`と共に[オーバーライド](../../../visual-basic/language-reference/modifiers/overrides.md)、 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)、 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)、または[静的](../../../visual-basic/language-reference/modifiers/static.md)同じ宣言内で。</span><span class="sxs-lookup"><span data-stu-id="010fe-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
-   <span data-ttu-id="010fe-118">**アクセスします。**</span><span class="sxs-lookup"><span data-stu-id="010fe-118">**Accessing.**</span></span> <span data-ttu-id="010fe-119">共有要素にアクセスするには、そのクラスまたは構造体の特定のインスタンスの変数名ではなく、そのクラスまたは構造体の名前を修飾します。</span><span class="sxs-lookup"><span data-stu-id="010fe-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="010fe-120">でも、クラスまたはその共有メンバーにアクセスする構造体のインスタンスを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="010fe-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="010fe-121">次の例には、共有プロシージャが呼び出される<xref:System.Double.IsNaN%2A>によって公開されている、<xref:System.Double>構造体。</span><span class="sxs-lookup"><span data-stu-id="010fe-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   <span data-ttu-id="010fe-122">**暗黙の型を共有します。**</span><span class="sxs-lookup"><span data-stu-id="010fe-122">**Implicit Sharing.**</span></span> <span data-ttu-id="010fe-123">使用することはできません、`Shared`の修飾子、 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)定数が暗黙的に共有しますが、できます。</span><span class="sxs-lookup"><span data-stu-id="010fe-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="010fe-124">同様に、するには、モジュールまたはインターフェイスのメンバーを宣言することはできません`Shared`、暗黙的に共有されますが、します。</span><span class="sxs-lookup"><span data-stu-id="010fe-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="010fe-125">動作</span><span class="sxs-lookup"><span data-stu-id="010fe-125">Behavior</span></span>  
  
-   <span data-ttu-id="010fe-126">**記憶域。**</span><span class="sxs-lookup"><span data-stu-id="010fe-126">**Storage.**</span></span> <span data-ttu-id="010fe-127">共有変数またはイベントは、そのクラスまたは構造体の数またはいくつかのインスタンスに関係なくを作成する、1 回だけメモリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="010fe-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="010fe-128">同様に、共有プロシージャまたはプロパティには、ローカル変数の 1 つだけのセットを保持します。</span><span class="sxs-lookup"><span data-stu-id="010fe-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
-   <span data-ttu-id="010fe-129">**アクセスするインスタンス変数を使用します。**</span><span class="sxs-lookup"><span data-stu-id="010fe-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="010fe-130">クラスまたは構造体の特定のインスタンスを格納する変数の名前で修飾することにより共有要素にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="010fe-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="010fe-131">この動作は通常どおり、コンパイラは警告メッセージを生成し、変数ではなく、クラスまたは構造体の名前を使ってアクセスします。</span><span class="sxs-lookup"><span data-stu-id="010fe-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
-   <span data-ttu-id="010fe-132">**インスタンス式からアクセスします。**</span><span class="sxs-lookup"><span data-stu-id="010fe-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="010fe-133">共有要素をそのクラスまたは構造体のインスタンスを返す式を使用してアクセスする場合、コンパイラで式を評価するのではなく、クラスまたは構造体の名前を使ってアクセスを行います。</span><span class="sxs-lookup"><span data-stu-id="010fe-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="010fe-134">その他のアクションだけでなく、インスタンスを返すことを実行する式を対象とした場合、予期しない結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="010fe-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="010fe-135">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="010fe-135">The following example illustrates this.</span></span>  
  
    ```  
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     <span data-ttu-id="010fe-136">上記の例では、コンパイラ警告メッセージを生成、共有変数にアクセスするコードのどちらの時刻`total`インスタンスを経由します。</span><span class="sxs-lookup"><span data-stu-id="010fe-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="010fe-137">クラスから直接アクセスは、各ケース`shareTotal`を行わないと、インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="010fe-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="010fe-138">プロシージャに目的の呼び出しの場合`returnClass`、つまりへの呼び出しも生成しません`returnClass`ので、"関数 returnClass() と呼ばれる"を表示する追加のアクションは実行されません。</span><span class="sxs-lookup"><span data-stu-id="010fe-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="010fe-139">`Shared` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="010fe-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="010fe-140">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="010fe-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="010fe-141">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="010fe-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="010fe-142">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="010fe-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="010fe-143">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="010fe-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="010fe-144">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="010fe-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="010fe-145">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="010fe-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="010fe-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="010fe-146">See Also</span></span>  
 [<span data-ttu-id="010fe-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="010fe-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="010fe-148">Static</span><span class="sxs-lookup"><span data-stu-id="010fe-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="010fe-149">Visual Basic における有効期間</span><span class="sxs-lookup"><span data-stu-id="010fe-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="010fe-150">手順</span><span class="sxs-lookup"><span data-stu-id="010fe-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="010fe-151">構造体</span><span class="sxs-lookup"><span data-stu-id="010fe-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="010fe-152">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="010fe-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
