---
title: "方法: 変数のスコープを制御する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7284d344e3bf0fdd0f900f2a820d6c8db4a4bf74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="12759-102">方法: 変数のスコープを制御する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12759-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="12759-103">変数が、通常、*スコープ*、リファレンスについては、それを宣言する領域全体で表示します。</span><span class="sxs-lookup"><span data-stu-id="12759-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="12759-104">場合によっては、変数の*アクセス レベル*そのスコープに影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="12759-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="12759-105">詳細については、次を参照してください。 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)です。</span><span class="sxs-lookup"><span data-stu-id="12759-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="12759-106">ブロックまたはプロシージャ レベルのスコープ</span><span class="sxs-lookup"><span data-stu-id="12759-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="12759-107">変数をブロック内でのみ表示されるようにするには</span><span class="sxs-lookup"><span data-stu-id="12759-107">To make a variable visible only within a block</span></span>  
  
-   <span data-ttu-id="12759-108">場所、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)の開始との間など、そのブロックの宣言ステートメントを終了して、変数、`For`と`Next`のステートメント、`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="12759-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="12759-109">ブロック内からのみ、変数を参照することができます。</span><span class="sxs-lookup"><span data-stu-id="12759-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="12759-110">変数をプロシージャ内でのみ表示されるようにするには</span><span class="sxs-lookup"><span data-stu-id="12759-110">To make a variable visible only within a procedure</span></span>  
  
-   <span data-ttu-id="12759-111">場所、 `Dim` 、変数、プロシージャ内では、任意のブロックの外側のステートメント (など、 `With`.`End With`ブロック) します。</span><span class="sxs-lookup"><span data-stu-id="12759-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="12759-112">プロシージャに含まれているすべてのブロックの内側など、プロシージャ内からのみ、変数を参照することができます。</span><span class="sxs-lookup"><span data-stu-id="12759-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="12759-113">モジュールまたは Namespace レベルのスコープ</span><span class="sxs-lookup"><span data-stu-id="12759-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="12759-114">便宜上、1 つの用語*モジュール レベル*モジュール、クラス、および構造体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="12759-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="12759-115">モジュール レベルの変数のアクセス レベルでは、そのスコープを決定します。</span><span class="sxs-lookup"><span data-stu-id="12759-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="12759-116">モジュール、クラスまたは構造体を含む名前空間もスコープに影響します。</span><span class="sxs-lookup"><span data-stu-id="12759-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="12759-117">変数をモジュール、クラスまたは構造体全体にわたって表示されるようにするには</span><span class="sxs-lookup"><span data-stu-id="12759-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1.  <span data-ttu-id="12759-118">場所、`Dim`変数、プロシージャの外部ではなく、モジュール、クラス、または構造体、内部のステートメント。</span><span class="sxs-lookup"><span data-stu-id="12759-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="12759-119">含める、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="12759-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3.  <span data-ttu-id="12759-120">ではなく、モジュール、クラス、または構造内で任意の場所から変数を参照することが外側にします。</span><span class="sxs-lookup"><span data-stu-id="12759-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="12759-121">変数を名前空間全体にわたって表示されるようにするには</span><span class="sxs-lookup"><span data-stu-id="12759-121">To make a variable visible throughout a namespace</span></span>  
  
1.  <span data-ttu-id="12759-122">場所、`Dim`変数、プロシージャの外部ではなく、モジュール、クラス、または構造体、内部のステートメント。</span><span class="sxs-lookup"><span data-stu-id="12759-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="12759-123">含める、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)または[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)キーワード、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="12759-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3.  <span data-ttu-id="12759-124">任意の場所から変数を参照できるモジュール、クラスまたは構造体を含む名前空間内で。</span><span class="sxs-lookup"><span data-stu-id="12759-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12759-125">例</span><span class="sxs-lookup"><span data-stu-id="12759-125">Example</span></span>  
 <span data-ttu-id="12759-126">次の例では、モジュール レベル変数を宣言し、モジュール内のコードを可視性を制限します。</span><span class="sxs-lookup"><span data-stu-id="12759-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="12759-127">前の例では、モジュールで定義されたすべてのプロシージャ`demonstrateScope`を参照できる、`String`変数`strMsg`です。</span><span class="sxs-lookup"><span data-stu-id="12759-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="12759-128">ときに、`usePrivateVariable`プロシージャが呼び出されると、文字列変数の内容を表示`strMsg`] ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="12759-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="12759-129">次の部分を変更前の例では、文字列変数に`strMsg`宣言の名前空間内の任意の場所のコードによって参照することができます。</span><span class="sxs-lookup"><span data-stu-id="12759-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="12759-130">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="12759-130">Robust Programming</span></span>  
 <span data-ttu-id="12759-131">同じ名前の別の変数の代わりに誤って参照することがある可能性は少なく、変数より狭いスコープ</span><span class="sxs-lookup"><span data-stu-id="12759-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="12759-132">参照の対応付けの問題を最小限に抑えることができますも。</span><span class="sxs-lookup"><span data-stu-id="12759-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="12759-133">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="12759-133">.NET Framework Security</span></span>  
 <span data-ttu-id="12759-134">変数のスコープが狭い、される可能性が少なく悪意のあるコードが不正にそれを使用します。</span><span class="sxs-lookup"><span data-stu-id="12759-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12759-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="12759-135">See Also</span></span>  
 [<span data-ttu-id="12759-136">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="12759-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="12759-137">Visual Basic における有効期間</span><span class="sxs-lookup"><span data-stu-id="12759-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="12759-138">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="12759-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="12759-139">変数</span><span class="sxs-lookup"><span data-stu-id="12759-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="12759-140">変数宣言</span><span class="sxs-lookup"><span data-stu-id="12759-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="12759-141">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="12759-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
