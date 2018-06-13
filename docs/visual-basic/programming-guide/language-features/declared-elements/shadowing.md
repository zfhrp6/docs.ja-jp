---
title: Visual Basic におけるシャドウ
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: fde6259b67a8d963ed8c30b87c94029fb2658664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656072"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="2d828-102">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="2d828-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="2d828-103">2 つのプログラミング要素は、同じ名前を共有する場合それらのいずれかの非表示に、または*シャドウ*、もう 1 つです。</span><span class="sxs-lookup"><span data-stu-id="2d828-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="2d828-104">このような状況で、シャドウされた要素は参照できません。代わりに、コードでは、要素名を使用する場合、Visual Basic コンパイラに解決されます、シャドウする要素。</span><span class="sxs-lookup"><span data-stu-id="2d828-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="2d828-105">目的</span><span class="sxs-lookup"><span data-stu-id="2d828-105">Purpose</span></span>  
 <span data-ttu-id="2d828-106">シャドウの主な目的は、クラス メンバーの定義を保護するのにです。</span><span class="sxs-lookup"><span data-stu-id="2d828-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="2d828-107">基本クラスがありますを変えることが定義されている 1 つとして同じ名前の要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="2d828-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="2d828-108">この場合、`Shadows`修飾子強制的に実行をするメンバーに解決するのには、クラスを参照する基本クラスの新しい要素の代わりに定義された、します。</span><span class="sxs-lookup"><span data-stu-id="2d828-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="2d828-109">シャドウの種類</span><span class="sxs-lookup"><span data-stu-id="2d828-109">Types of Shadowing</span></span>  
 <span data-ttu-id="2d828-110">要素は、2 つの異なる方法で別の要素をシャドウすることができます。</span><span class="sxs-lookup"><span data-stu-id="2d828-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="2d828-111">要素はシャドウ ケースを実現する、シャドウされた要素を含む領域のサブ領域内で宣言できます*スコープによる*です。</span><span class="sxs-lookup"><span data-stu-id="2d828-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="2d828-112">派生クラスは、シャドウ ケースが行われますが、基底クラスのメンバーを再定義できますまたは*継承によって*です。</span><span class="sxs-lookup"><span data-stu-id="2d828-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="2d828-113">スコープによるシャドウ</span><span class="sxs-lookup"><span data-stu-id="2d828-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="2d828-114">同じモジュール、クラス、または構造体に名前が同じで別のスコープ内の要素をプログラミングする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d828-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="2d828-115">狭いスコープを持つ要素が他の要素をシャドウするこの方法で 2 つの要素が宣言されているし、コードが共有されている名前を指す、(ブロック スコープは最も狭いです)。</span><span class="sxs-lookup"><span data-stu-id="2d828-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="2d828-116">たとえば、モジュールを定義できます、`Public`という名前の変数`temp`、モジュール内の手順もという名前のローカル変数を宣言できますと`temp`です。</span><span class="sxs-lookup"><span data-stu-id="2d828-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="2d828-117">参照`temp`プロシージャ内からへの参照中に、ローカル変数にアクセス`temp`からプロシージャへのアクセス、外部、`Public`変数。</span><span class="sxs-lookup"><span data-stu-id="2d828-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="2d828-118">この場合、プロシージャの変数`temp`モジュールの変数のシャドウ`temp`です。</span><span class="sxs-lookup"><span data-stu-id="2d828-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="2d828-119">次の図に、2 つの変数、という名前を`temp`です。</span><span class="sxs-lookup"><span data-stu-id="2d828-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="2d828-120">ローカル変数`temp`メンバー変数のシャドウ`temp`独自のプロシージャ内からアクセスするときに`p`です。</span><span class="sxs-lookup"><span data-stu-id="2d828-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="2d828-121">ただし、`MyClass`キーワードは、シャドウをバイパスし、メンバー変数にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2d828-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 <span data-ttu-id="2d828-122">![スコープによるシャドウのグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span><span class="sxs-lookup"><span data-stu-id="2d828-122">![Graphic diagram of shadowing through scope](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span></span>  
<span data-ttu-id="2d828-123">スコープによるシャドウ</span><span class="sxs-lookup"><span data-stu-id="2d828-123">Shadowing through scope</span></span>  
  
 <span data-ttu-id="2d828-124">スコープによるシャドウの例は、次を参照してください。[する方法: Your 変数と同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d828-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="2d828-125">継承によるシャドウ</span><span class="sxs-lookup"><span data-stu-id="2d828-125">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="2d828-126">派生クラスは、基本クラスから継承されたプログラミング要素を再定義を再定義する要素は、元の要素をシャドウします。</span><span class="sxs-lookup"><span data-stu-id="2d828-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="2d828-127">他の種類とは、任意の型の宣言された要素は、または一連のオーバー ロードされた要素をシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="2d828-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="2d828-128">たとえば、`Integer`変数をシャドウする、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2d828-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="2d828-129">別のプロシージャを持つプロシージャをシャドウする場合は、別のパラメーター リストと異なる戻り値の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d828-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="2d828-130">次の図は、基本クラス`b`と派生クラス`d`から継承する`b`です。</span><span class="sxs-lookup"><span data-stu-id="2d828-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="2d828-131">という名前のプロシージャが基本クラスで定義`proc`と、派生クラスは、同じ名前の別のプロシージャをシャドウします。</span><span class="sxs-lookup"><span data-stu-id="2d828-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="2d828-132">最初の`Call`シャドウ ステートメントにアクセスする`proc`派生クラスでします。</span><span class="sxs-lookup"><span data-stu-id="2d828-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="2d828-133">ただし、`MyBase`キーワードは、シャドウをバイパスし、基本クラスで影付きのプロシージャにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2d828-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 <span data-ttu-id="2d828-134">![継承によるシャドウのグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span><span class="sxs-lookup"><span data-stu-id="2d828-134">![Graphic diagram of shadowing through inheritance](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span></span>  
<span data-ttu-id="2d828-135">継承によるシャドウ</span><span class="sxs-lookup"><span data-stu-id="2d828-135">Shadowing through inheritance</span></span>  
  
 <span data-ttu-id="2d828-136">継承によるシャドウの例は、次を参照してください。[する方法: Your 変数と同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)と[する方法:、継承された変数を非表示に](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d828-136">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="2d828-137">シャドウとアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="2d828-137">Shadowing and Access Level</span></span>  
 <span data-ttu-id="2d828-138">要素は、常に、派生クラスを使用して、コードからアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="2d828-138">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="2d828-139">たとえば、宣言される可能性があります`Private`です。</span><span class="sxs-lookup"><span data-stu-id="2d828-139">For example, it might be declared `Private`.</span></span> <span data-ttu-id="2d828-140">このような場合は、シャドウは行われず、コンパイラは必要があります、同じ要素への参照を解決する場合がありますは行われません。</span><span class="sxs-lookup"><span data-stu-id="2d828-140">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="2d828-141">この要素は、最小の継承はステップ後方シャドウするクラスからアクセス可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="2d828-141">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="2d828-142">シャドウされた要素が、プロシージャの場合は、解像度が同じ名前、パラメーター リストを持つ最も近い利用可能なバージョンがあり、型を返すられます。</span><span class="sxs-lookup"><span data-stu-id="2d828-142">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="2d828-143">次の例では、3 つのクラスの継承階層を示します。</span><span class="sxs-lookup"><span data-stu-id="2d828-143">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="2d828-144">各クラスを定義、`Sub`プロシージャ`display`、および各派生したクラス shadows、`display`その基本クラスのプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2d828-144">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="2d828-145">前の例では、派生クラスで`secondClass`shadows`display`で、`Private`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2d828-145">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="2d828-146">ときにモジュール`callDisplay`呼び出し`display`で`secondClass`、呼び出し元のコードが範囲外`secondClass`と、プライベート アクセスできないため`display`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2d828-146">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="2d828-147">シャドウ処理は行われず、およびコンパイラが基底クラスへの参照を解決`display`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2d828-147">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="2d828-148">ただし、さらに、派生クラス`thirdClass`を宣言`display`として`Public`ため、コードで`callDisplay`にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2d828-148">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="2d828-149">シャドウとオーバーライド</span><span class="sxs-lookup"><span data-stu-id="2d828-149">Shadowing and Overriding</span></span>  
 <span data-ttu-id="2d828-150">シャドウとオーバーライドを混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="2d828-150">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="2d828-151">派生クラスは、基底クラスから継承し、1 つの宣言された要素と他の再定義時にどちらも使用されます。</span><span class="sxs-lookup"><span data-stu-id="2d828-151">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="2d828-152">2 つの重要な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="2d828-152">But there are significant differences between the two.</span></span> <span data-ttu-id="2d828-153">比較については、次を参照してください。[シャドウとの間の相違点およびオーバーライド](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d828-153">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="2d828-154">シャドウとオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="2d828-154">Shadowing and Overloading</span></span>  
 <span data-ttu-id="2d828-155">派生クラスで複数の要素を持つ同じ基底クラス要素をシャドウする場合は、その要素のオーバー ロードされたバージョンがシャドウする要素になります。</span><span class="sxs-lookup"><span data-stu-id="2d828-155">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="2d828-156">詳細については、次を参照してください。[プロシージャのオーバー ロード](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d828-156">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="2d828-157">シャドウされた要素へのアクセス</span><span class="sxs-lookup"><span data-stu-id="2d828-157">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="2d828-158">派生クラスからの要素をアクセスするときに通常これを行う、派生クラスの現在のインスタンスを要素名を修飾することにより、`Me`キーワード。</span><span class="sxs-lookup"><span data-stu-id="2d828-158">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="2d828-159">修飾基底クラス要素にアクセスする場合は、派生クラスでは、基本クラスで要素をシャドウを`MyBase`キーワード。</span><span class="sxs-lookup"><span data-stu-id="2d828-159">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="2d828-160">シャドウされた要素へのアクセスの例は、次を参照してください。[する方法: 派生クラスによって非表示変数にアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d828-160">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="2d828-161">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="2d828-161">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="2d828-162">派生クラスは、シャドウ要素またはシャドウされた要素にアクセスするかどうか、オブジェクト変数を作成する方法に影響もします。</span><span class="sxs-lookup"><span data-stu-id="2d828-162">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="2d828-163">次の例では、2 つのオブジェクトを作成、派生クラスからが 1 つのオブジェクトは、基底クラスと、他の派生クラスとして宣言されています。</span><span class="sxs-lookup"><span data-stu-id="2d828-163">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()   
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="2d828-164">前の例では、変数`basObj`は基底クラスとして宣言されています。</span><span class="sxs-lookup"><span data-stu-id="2d828-164">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="2d828-165">割り当て、`dervCls`オブジェクトをそれには、拡大変換であるためです。</span><span class="sxs-lookup"><span data-stu-id="2d828-165">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="2d828-166">基本クラスがシャドウされた変数にアクセスできませんただし、 `z` 、派生クラスで、コンパイラが解決するか`basObj.z`元の基本クラスの値にします。</span><span class="sxs-lookup"><span data-stu-id="2d828-166">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d828-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d828-167">See Also</span></span>  
 [<span data-ttu-id="2d828-168">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="2d828-168">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="2d828-169">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="2d828-169">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="2d828-170">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="2d828-170">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="2d828-171">Shadows</span><span class="sxs-lookup"><span data-stu-id="2d828-171">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="2d828-172">Overrides</span><span class="sxs-lookup"><span data-stu-id="2d828-172">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="2d828-173">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="2d828-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="2d828-174">継承の基本</span><span class="sxs-lookup"><span data-stu-id="2d828-174">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
