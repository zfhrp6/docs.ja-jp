---
title: "方法: 自分で宣言した変数と同じ名前の変数を隠す (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af031f3ef134b2a509922e6ada28aa5b2b80d641
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="1f0be-102">方法: 自分で宣言した変数と同じ名前の変数を隠す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f0be-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>
<span data-ttu-id="1f0be-103">変数を非表示にすることができます*シャドウ*は、これによって、同じ名前の変数で再定義します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="1f0be-104">2 つの方法で非表示に変数をシャドウすることができます。</span><span class="sxs-lookup"><span data-stu-id="1f0be-104">You can shadow the variable you want to hide in two ways:</span></span>  
  
-   <span data-ttu-id="1f0be-105">**スコープによるシャドウします。**</span><span class="sxs-lookup"><span data-stu-id="1f0be-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="1f0be-106">その操作は、非表示に変数を含む領域のサブ領域内で再宣言することによってスコープによるシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="1f0be-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>  
  
-   <span data-ttu-id="1f0be-107">**継承によるシャドウします。**</span><span class="sxs-lookup"><span data-stu-id="1f0be-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="1f0be-108">非表示にする、変数がクラス レベルで定義されている場合することができます、継承によるシャドウで再宣言することによって、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)派生クラス内のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="1f0be-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>  
  
## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="1f0be-109">2 つの方法で変数を隠す</span><span class="sxs-lookup"><span data-stu-id="1f0be-109">Two Ways to Hide a Variable</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="1f0be-110">スコープによるシャドウで変数を非表示にするには</span><span class="sxs-lookup"><span data-stu-id="1f0be-110">To hide a variable by shadowing it through scope</span></span>  
  
1.  <span data-ttu-id="1f0be-111">を非表示にする変数の定義のリージョンを特定し、変数を使用してを再定義するでサブ地域を決定します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>  
  
    |<span data-ttu-id="1f0be-112">変数の領域</span><span class="sxs-lookup"><span data-stu-id="1f0be-112">Variable's region</span></span>|<span data-ttu-id="1f0be-113">再定義が許容されるサブ地域</span><span class="sxs-lookup"><span data-stu-id="1f0be-113">Allowable subregion for redefining it</span></span>|  
    |-----------------------|-------------------------------------------|  
    |<span data-ttu-id="1f0be-114">モジュール</span><span class="sxs-lookup"><span data-stu-id="1f0be-114">Module</span></span>|<span data-ttu-id="1f0be-115">モジュール内のクラス</span><span class="sxs-lookup"><span data-stu-id="1f0be-115">A class within the module</span></span>|  
    |<span data-ttu-id="1f0be-116">クラス</span><span class="sxs-lookup"><span data-stu-id="1f0be-116">Class</span></span>|<span data-ttu-id="1f0be-117">クラス内のサブクラス</span><span class="sxs-lookup"><span data-stu-id="1f0be-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="1f0be-118">クラス内の手順</span><span class="sxs-lookup"><span data-stu-id="1f0be-118">A procedure within the class</span></span>|  
  
     <span data-ttu-id="1f0be-119">再定義できませんそのプロシージャ内のブロックでプロシージャの変数などの`If`しています.`End If`構築または`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="1f0be-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>  
  
2.  <span data-ttu-id="1f0be-120">既に存在しない場合は、サブ領域を作成します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-120">Create the subregion if it does not already exist.</span></span>  
  
3.  <span data-ttu-id="1f0be-121">その地区内では、書き込み、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)シャドウ変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>  
  
     <span data-ttu-id="1f0be-122">サブ領域内のコードは、変数名が参照されているとき、コンパイラは変数のシャドウへの参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>  
  
     <span data-ttu-id="1f0be-123">次の例では、シャドウ参照と同様に、スコープによるシャドウを示します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     <span data-ttu-id="1f0be-124">前の例は、変数を宣言して`num`モジュール レベルとプロシージャ レベルの両方 (の手順で`show`)。</span><span class="sxs-lookup"><span data-stu-id="1f0be-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="1f0be-125">ローカル変数`num`モジュール レベル変数をシャドウ`num`内`show`でローカル変数が 2 に設定されているため、します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="1f0be-126">ただし、シャドウをローカル変数がない`num`で、`useModuleLevelNum`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="1f0be-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="1f0be-127">したがって、`useModuleLevelNum`モジュール レベル変数の値を 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>  
  
     <span data-ttu-id="1f0be-128">`MsgBox`内で呼び出す`show`修飾することにより、シャドウ機構をバイパスする`num`モジュール名を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="1f0be-129">そのため、ローカル変数の代わりに、モジュール レベル変数を表示します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="1f0be-130">継承によるシャドウで変数を非表示にするには</span><span class="sxs-lookup"><span data-stu-id="1f0be-130">To hide a variable by shadowing it through inheritance</span></span>  
  
1.  <span data-ttu-id="1f0be-131">必ず、クラスでは、および (プロシージャ) の外側のクラス レベルで非表示にする、変数が宣言されてください。</span><span class="sxs-lookup"><span data-stu-id="1f0be-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="1f0be-132">それ以外の場合継承によるシャドウすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1f0be-132">Otherwise you cannot shadow it through inheritance.</span></span>  
  
2.  <span data-ttu-id="1f0be-133">既に存在しない場合、変数のクラスから派生するクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-133">Define a class derived from the variable's class if one does not already exist.</span></span>  
  
3.  <span data-ttu-id="1f0be-134">派生クラス内の書き込み、`Dim`変数を宣言するステートメント。</span><span class="sxs-lookup"><span data-stu-id="1f0be-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="1f0be-135">含める、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)宣言でキーワード。</span><span class="sxs-lookup"><span data-stu-id="1f0be-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="1f0be-136">派生クラス内のコードは、変数名が参照されているとき、コンパイラは、変数への参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="1f0be-137">次の例では、継承によるシャドウを示します。</span><span class="sxs-lookup"><span data-stu-id="1f0be-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="1f0be-138">これにより、2 つの参照変数のシャドウにアクセスして、シャドウをバイパスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="1f0be-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="1f0be-139">前の例は、変数を宣言`shadowString`基底クラスと派生クラスでシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="1f0be-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="1f0be-140">プロシージャ`showStrings`シャドウのバージョンの文字列が表示されます、派生クラスでときに名前`shadowString`が修飾されていません。</span><span class="sxs-lookup"><span data-stu-id="1f0be-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="1f0be-141">影付きのバージョンを次に、表示と`shadowString`で修飾されて、`MyBase`キーワード。</span><span class="sxs-lookup"><span data-stu-id="1f0be-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1f0be-142">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="1f0be-142">Robust Programming</span></span>  
 <span data-ttu-id="1f0be-143">シャドウ処理には、1 つ以上のバージョンの同じ名前の変数が導入されています。</span><span class="sxs-lookup"><span data-stu-id="1f0be-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="1f0be-144">コードのステートメントは、変数名が参照されているときに、コンパイラが参照を解決するバージョンは、コードのステートメントの場所が存在している修飾文字列のなどの要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="1f0be-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="1f0be-145">これにより、意図しないシャドウされた変数のバージョンを参照するリスクが増加することができます。</span><span class="sxs-lookup"><span data-stu-id="1f0be-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="1f0be-146">シャドウされた変数へのすべての参照を完全に修飾することによってそのリスクを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="1f0be-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f0be-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f0be-147">See Also</span></span>  
 [<span data-ttu-id="1f0be-148">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="1f0be-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="1f0be-149">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="1f0be-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="1f0be-150">シャドウとオーバーライドの違い</span><span class="sxs-lookup"><span data-stu-id="1f0be-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="1f0be-151">方法: 継承された変数を隠す</span><span class="sxs-lookup"><span data-stu-id="1f0be-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [<span data-ttu-id="1f0be-152">方法: 派生クラスによって非表示になっている変数にアクセスする</span><span class="sxs-lookup"><span data-stu-id="1f0be-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [<span data-ttu-id="1f0be-153">Overrides</span><span class="sxs-lookup"><span data-stu-id="1f0be-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="1f0be-154">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="1f0be-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="1f0be-155">継承の基本</span><span class="sxs-lookup"><span data-stu-id="1f0be-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
