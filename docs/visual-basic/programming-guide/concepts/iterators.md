---
title: "反復子 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c38609878c10ff3234b5a33ec44d678d24c11d7f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="iterators-visual-basic"></a><span data-ttu-id="65d43-102">反復子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65d43-102">Iterators (Visual Basic)</span></span>
<span data-ttu-id="65d43-103">*反復子*コレクションのステップ実行の一覧し、配列などに使用できます。</span><span class="sxs-lookup"><span data-stu-id="65d43-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="65d43-104">Iterator メソッドまたは`get`アクセサーは、コレクションに対するカスタム イテレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="65d43-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="65d43-105">Iterator メソッドを使用して、 [Yield](../../../visual-basic/language-reference/statements/yield-statement.md)ステートメントを一度に&1; つの各要素を返します。</span><span class="sxs-lookup"><span data-stu-id="65d43-105">An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="65d43-106">ときに、`Yield`ステートメントに達すると、コード内の現在位置が記憶されます。</span><span class="sxs-lookup"><span data-stu-id="65d43-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="65d43-107">次回の反復子関数が呼び出されたとき、その場所から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="65d43-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="65d43-108">使用してクライアント コードから反復子を使用する、[ごとにしています.次](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメント、または LINQ クエリを使用しています。</span><span class="sxs-lookup"><span data-stu-id="65d43-108">You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="65d43-109">次の例の最初のイテレーションで、`For Each`ループが実行を続行すると、`SomeNumbers`最初まで反復子メソッド`Yield`ステートメントに到達します。</span><span class="sxs-lookup"><span data-stu-id="65d43-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="65d43-110">このイテレーションは第 3 の値を返し、iterator メソッドの現在位置が保持されます。</span><span class="sxs-lookup"><span data-stu-id="65d43-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="65d43-111">ループの次の反復処理では、iterator メソッドの実行が場所から続行し、もう一度停止になったときに中断、`Yield`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="65d43-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="65d43-112">このイテレーションは 5 の値を返し、iterator メソッドの現在位置が保持されます再。</span><span class="sxs-lookup"><span data-stu-id="65d43-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="65d43-113">Iterator メソッドの終わりに達したときに、ループが完了します。</span><span class="sxs-lookup"><span data-stu-id="65d43-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In SomeNumbers()  
        Console.Write(number & " ")  
    Next  
    ' Output: 3 5 8  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function SomeNumbers() As System.Collections.IEnumerable  
    Yield 3  
    Yield 5  
    Yield 8  
End Function  
```  
  
 <span data-ttu-id="65d43-114">Iterator メソッドの戻り値の型または`get`アクセサーは、 <xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または<xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="65d43-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="65d43-115">使用することができます、`Exit Function`または`Return`ステートメント、反復を終了します。</span><span class="sxs-lookup"><span data-stu-id="65d43-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="65d43-116">Visual Basic の反復子関数または`get`アクセサー宣言が含まれる、[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)修飾子です。</span><span class="sxs-lookup"><span data-stu-id="65d43-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
 <span data-ttu-id="65d43-117">Visual Studio 2012 で Visual Basic では、反復子が導入されています。</span><span class="sxs-lookup"><span data-stu-id="65d43-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="65d43-118">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="65d43-118">**In this topic**</span></span>  
  
-   [<span data-ttu-id="65d43-119">単純な反復子</span><span class="sxs-lookup"><span data-stu-id="65d43-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
-   [<span data-ttu-id="65d43-120">コレクション クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="65d43-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
-   [<span data-ttu-id="65d43-121">Try ブロック</span><span class="sxs-lookup"><span data-stu-id="65d43-121">Try Blocks</span></span>](#BKMK_TryBlocks)  
  
-   [<span data-ttu-id="65d43-122">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="65d43-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)  
  
-   [<span data-ttu-id="65d43-123">ジェネリック リストと共に反復子の使用</span><span class="sxs-lookup"><span data-stu-id="65d43-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
-   [<span data-ttu-id="65d43-124">構文情報</span><span class="sxs-lookup"><span data-stu-id="65d43-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
-   [<span data-ttu-id="65d43-125">技術的な実装</span><span class="sxs-lookup"><span data-stu-id="65d43-125">Technical Implementation</span></span>](#BKMK_Technical)  
  
-   [<span data-ttu-id="65d43-126">反復子の使用</span><span class="sxs-lookup"><span data-stu-id="65d43-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  <span data-ttu-id="65d43-127">トピックの「単純な反復子の使用例を除くすべての例については、含める[Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ステートメントを、`System.Collections`と`System.Collections.Generic`名前空間。</span><span class="sxs-lookup"><span data-stu-id="65d43-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
##  <span data-ttu-id="65d43-128"><a name="BKMK_SimpleIterator"></a>単純な反復子</span><span class="sxs-lookup"><span data-stu-id="65d43-128"><a name="BKMK_SimpleIterator"></a> Simple Iterator</span></span>  
 <span data-ttu-id="65d43-129">次の例は、1 つ`Yield`ステートメント内にある、[にしています.次](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。</span><span class="sxs-lookup"><span data-stu-id="65d43-129">The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="65d43-130">`Main`の各反復処理、`For Each`ステートメント本体を次の手順を実行する反復子関数の呼び出しを作成`Yield`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="65d43-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    ' Output: 6 8 10 12 14 16 18  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As System.Collections.Generic.IEnumerable(Of Integer)  
  
    ' Yield even numbers in the range.  
    For number As Integer = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
##  <span data-ttu-id="65d43-131"><a name="BKMK_CollectionClass"></a>コレクション クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="65d43-131"><a name="BKMK_CollectionClass"></a> Creating a Collection Class</span></span>  
 <span data-ttu-id="65d43-132">次の例では、`DaysOfTheWeek`クラスが実装する、<xref:System.Collections.IEnumerable>インターフェイスを必要とする、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッド</xref:System.Collections.IEnumerable.GetEnumerator%2A></xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="65d43-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="65d43-133">コンパイラが暗黙的に呼び出す、 `GetEnumerator` <xref:System.Collections.IEnumerator>.</xref:System.Collections.IEnumerator>を返すメソッド</span><span class="sxs-lookup"><span data-stu-id="65d43-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="65d43-134">`GetEnumerator`メソッドを使用して、一度に&1; つの各文字列を返します、`Yield`ステートメント、および`Iterator`修飾子は関数宣言では。</span><span class="sxs-lookup"><span data-stu-id="65d43-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>  
  
```vb  
Sub Main()  
    Dim days As New DaysOfTheWeek()  
    For Each day As String In days  
        Console.Write(day & " ")  
    Next  
    ' Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey()  
End Sub  
  
Private Class DaysOfTheWeek  
    Implements IEnumerable  
  
    Public days =  
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        ' Yield each day of the week.  
        For i As Integer = 0 To days.Length - 1  
            Yield days(i)  
        Next  
    End Function  
End Class  
```  
  
 <span data-ttu-id="65d43-135">次の例を作成し、`Zoo`動物のコレクションを格納するクラス。</span><span class="sxs-lookup"><span data-stu-id="65d43-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="65d43-136">`For Each`クラスのインスタンスを参照するステートメント (`theZoo`) を暗黙的に呼び出す、`GetEnumerator`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="65d43-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="65d43-137">`For Each`を参照するステートメント、`Birds`と`Mammals`プロパティを使用して、 `AnimalsForType` iterator メソッドの名前します。</span><span class="sxs-lookup"><span data-stu-id="65d43-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
```vb  
Sub Main()  
    Dim theZoo As New Zoo()  
  
    theZoo.AddMammal("Whale")  
    theZoo.AddMammal("Rhinoceros")  
    theZoo.AddBird("Penguin")  
    theZoo.AddBird("Warbler")  
  
    For Each name As String In theZoo  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros Penguin Warbler  
  
    For Each name As String In theZoo.Birds  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Penguin Warbler  
  
    For Each name As String In theZoo.Mammals  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros  
  
    Console.ReadKey()  
End Sub  
  
Public Class Zoo  
    Implements IEnumerable  
  
    ' Private members.  
    Private animals As New List(Of Animal)  
  
    ' Public methods.  
    Public Sub AddMammal(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})  
    End Sub  
  
    Public Sub AddBird(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})  
    End Sub  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        For Each theAnimal As Animal In animals  
            Yield theAnimal.Name  
        Next  
    End Function  
  
    ' Public members.  
    Public ReadOnly Property Mammals As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Mammal)  
        End Get  
    End Property  
  
    Public ReadOnly Property Birds As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Bird)  
        End Get  
    End Property  
  
    ' Private methods.  
    Private Iterator Function AnimalsForType( _  
    ByVal type As Animal.TypeEnum) As IEnumerable  
        For Each theAnimal As Animal In animals  
            If (theAnimal.Type = type) Then  
                Yield theAnimal.Name  
            End If  
        Next  
    End Function  
  
    ' Private class.  
    Private Class Animal  
        Public Enum TypeEnum  
            Bird  
            Mammal  
        End Enum  
  
        Public Property Name As String  
        Public Property Type As TypeEnum  
    End Class  
End Class  
```  
  
##  <span data-ttu-id="65d43-138"><a name="BKMK_TryBlocks"></a>Try ブロック</span><span class="sxs-lookup"><span data-stu-id="65d43-138"><a name="BKMK_TryBlocks"></a> Try Blocks</span></span>  
 <span data-ttu-id="65d43-139">Visual Basic では、`Yield`内のステートメントで、`Try`のブロック、[しようとしています.キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="65d43-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="65d43-140">A`Try`がブロック、`Yield`ステートメントにはできます`Catch`ブロック、およびことができますが、`Finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="65d43-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="65d43-141">次の例が含まれます`Try`、 `Catch`、および`Finally`では、反復子関数をブロックします。</span><span class="sxs-lookup"><span data-stu-id="65d43-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="65d43-142">`Finally` Iterator 関数内のブロックを実行する前に、`For Each`イテレーションが完了するとします。</span><span class="sxs-lookup"><span data-stu-id="65d43-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In Test()  
        Console.WriteLine(number)  
    Next  
    Console.WriteLine("For Each is done.")  
  
    ' Output:  
    '  3  
    '  4  
    '  Something happened. Yields are done.  
    '  Finally is called.  
    '  For Each is done.  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function Test() As IEnumerable(Of Integer)  
    Try  
        Yield 3  
        Yield 4  
        Throw New Exception("Something happened. Yields are done.")  
        Yield 5  
        Yield 6  
    Catch ex As Exception  
        Console.WriteLine(ex.Message)  
    Finally  
        Console.WriteLine("Finally is called.")  
    End Try  
End Function  
```  
  
 <span data-ttu-id="65d43-143">A`Yield`ステートメント内で使用できない、`Catch`ブロックまたは`Finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="65d43-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="65d43-144">場合、`For Each`本体 (iterator メソッド) ではなく、例外がスロー、 `Catch` iterator 関数内のブロックは実行されませんが、`Finally`反復子関数でのブロックを実行します。</span><span class="sxs-lookup"><span data-stu-id="65d43-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="65d43-145">A`Catch`反復子関数の内側のブロックは、反復子関数内で発生する例外だけをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="65d43-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
##  <span data-ttu-id="65d43-146"><a name="BKMK_AnonymousMethods"></a>匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="65d43-146"><a name="BKMK_AnonymousMethods"></a> Anonymous Methods</span></span>  
 <span data-ttu-id="65d43-147">Visual basic では、iterator 関数が匿名関数にできます。</span><span class="sxs-lookup"><span data-stu-id="65d43-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="65d43-148">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="65d43-148">The following example illustrates this.</span></span>  
  
```vb  
Dim iterateSequence = Iterator Function() _  
                      As IEnumerable(Of Integer)  
                          Yield 1  
                          Yield 2  
                      End Function  
  
For Each number As Integer In iterateSequence()  
    Console.Write(number & " ")  
Next  
' Output: 1 2  
Console.ReadKey()  
```  
  
 <span data-ttu-id="65d43-149">次の例では、引数を検証する非反復子メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="65d43-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="65d43-150">このメソッドは、匿名、コレクションの要素を示す反復子の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="65d43-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>  
  
```vb  
Sub Main()  
    For Each number As Integer In GetSequence(5, 10)  
        Console.Write(number & " ")  
    Next  
    ' Output: 5 6 7 8 9 10  
    Console.ReadKey()  
End Sub  
  
Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _  
As IEnumerable  
    ' Validate the arguments.  
    If low < 1 Then  
        Throw New ArgumentException("low is too low")  
    End If  
    If high > 140 Then  
        Throw New ArgumentException("high is too high")  
    End If  
  
    ' Return an anonymous iterator function.  
    Dim iterateSequence = Iterator Function() As IEnumerable  
                              For index = low To high  
                                  Yield index  
                              Next  
                          End Function  
    Return iterateSequence()  
End Function  
```  
  
 <span data-ttu-id="65d43-151">最初のイテレーションの開始まで、検証を実行できない検証が代わりに反復子関数の内部である場合は、`For Each`本文。</span><span class="sxs-lookup"><span data-stu-id="65d43-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>  
  
##  <span data-ttu-id="65d43-152"><a name="BKMK_GenericList"></a>ジェネリック リストと共に反復子の使用</span><span class="sxs-lookup"><span data-stu-id="65d43-152"><a name="BKMK_GenericList"></a> Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="65d43-153">次の例では、`Stack(Of T)`ジェネリック クラスが実装する、<xref:System.Collections.Generic.IEnumerable%601>ジェネリック インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="65d43-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="65d43-154">`Push`メソッドでは、型の配列に値を割り当てます`T`します。</span><span class="sxs-lookup"><span data-stu-id="65d43-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="65d43-155"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>メソッドを使用して配列の値を返す、`Yield`ステートメント</xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>。</span><span class="sxs-lookup"><span data-stu-id="65d43-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>  
  
 <span data-ttu-id="65d43-156">ジェネリックだけでなく<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>メソッドは、非ジェネリック<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドを実装することがもする必要があります</xref:System.Collections.IEnumerable.GetEnumerator%2A></xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>。</span><span class="sxs-lookup"><span data-stu-id="65d43-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="65d43-157">これは、ため<xref:System.Collections.Generic.IEnumerable%601><xref:System.Collections.IEnumerable>.</xref:System.Collections.IEnumerable>から継承</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="65d43-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="65d43-158">非ジェネリックの実装は、ジェネリックな実装に従います。</span><span class="sxs-lookup"><span data-stu-id="65d43-158">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="65d43-159">例では、さまざまなデータの同じコレクションを反復処理する方法をサポートするために名前付きの反復子を使用します。</span><span class="sxs-lookup"><span data-stu-id="65d43-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="65d43-160">これらの反復子を名前付き、`TopToBottom`と`BottomToTop`プロパティ、および`TopN`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="65d43-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="65d43-161">`BottomToTop`プロパティ宣言が含まれる、`Iterator`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="65d43-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>  
  
```vb  
Sub Main()  
    Dim theStack As New Stack(Of Integer)  
  
    ' Add items to the stack.  
    For number As Integer = 0 To 9  
        theStack.Push(number)  
    Next  
  
    ' Retrieve items from the stack.  
    ' For Each is allowed because theStack implements  
    ' IEnumerable(Of Integer).  
    For Each number As Integer In theStack  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    ' For Each is allowed, because theStack.TopToBottom  
    ' returns IEnumerable(Of Integer).  
    For Each number As Integer In theStack.TopToBottom  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    For Each number As Integer In theStack.BottomToTop  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 0 1 2 3 4 5 6 7 8 9   
  
    For Each number As Integer In theStack.TopN(7)  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey()  
End Sub  
  
Public Class Stack(Of T)  
    Implements IEnumerable(Of T)  
  
    Private values As T() = New T(99) {}  
    Private top As Integer = 0  
  
    Public Sub Push(ByVal t As T)  
        values(top) = t  
        top = top + 1  
    End Sub  
  
    Public Function Pop() As T  
        top = top - 1  
        Return values(top)  
    End Function  
  
    ' This function implements the GetEnumerator method. It allows  
    ' an instance of the class to be used in a For Each statement.  
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _  
        Implements IEnumerable(Of T).GetEnumerator  
  
        For index As Integer = top - 1 To 0 Step -1  
            Yield values(index)  
        Next  
    End Function  
  
    Public Iterator Function GetEnumerator1() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        Yield GetEnumerator()  
    End Function  
  
    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)  
        Get  
            Return Me  
        End Get  
    End Property  
  
    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)  
        Get  
            For index As Integer = 0 To top - 1  
                Yield values(index)  
            Next  
        End Get  
    End Property  
  
    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _  
        As IEnumerable(Of T)  
  
        ' Return less than itemsFromTop if necessary.  
        Dim startIndex As Integer =  
            If(itemsFromTop >= top, 0, top - itemsFromTop)  
  
        For index As Integer = top - 1 To startIndex Step -1  
            Yield values(index)  
        Next  
    End Function  
End Class  
  
```  
  
##  <span data-ttu-id="65d43-162"><a name="BKMK_SyntaxInformation"></a>構文情報</span><span class="sxs-lookup"><span data-stu-id="65d43-162"><a name="BKMK_SyntaxInformation"></a> Syntax Information</span></span>  
 <span data-ttu-id="65d43-163">メソッドとして発生することが、反復子または`get`アクセサー。</span><span class="sxs-lookup"><span data-stu-id="65d43-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="65d43-164">反復子は、イベント、コンス トラクター、静的コンス トラクターまたは静的のデストラクターで発生することはできません。</span><span class="sxs-lookup"><span data-stu-id="65d43-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="65d43-165">式の型から暗黙的な変換が存在する必要があります、`Yield`ステートメント、反復子の戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="65d43-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="65d43-166">Visual Basic では、iterator メソッドは指定できません`ByRef`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="65d43-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="65d43-167">Visual basic で「メリットをもたらす」予約語ではない、特別な意味で使用されている場合にのみ、`Iterator`メソッドまたは`get`アクセサー。</span><span class="sxs-lookup"><span data-stu-id="65d43-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>  
  
##  <span data-ttu-id="65d43-168"><a name="BKMK_Technical"></a>技術的な実装</span><span class="sxs-lookup"><span data-stu-id="65d43-168"><a name="BKMK_Technical"></a> Technical Implementation</span></span>  
 <span data-ttu-id="65d43-169">メソッドとして、反復子を記述しても、コンパイラが il 変換を入れ子になったクラスには、実際には、ステート マシンです。</span><span class="sxs-lookup"><span data-stu-id="65d43-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="65d43-170">このクラスには、時間と反復子の位置の追跡`For Each...Next`クライアント コードでのループが継続されます。</span><span class="sxs-lookup"><span data-stu-id="65d43-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="65d43-171">コンパイラが何を表示するには、iterator メソッドに対して生成される Microsoft 中間言語コードを表示するのに、Ildasm.exe ツールを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="65d43-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="65d43-172">反復子を作成する場合、[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)、全体を実装する必要はありません<xref:System.Collections.IEnumerator>インターフェイス</xref:System.Collections.IEnumerator>。</span><span class="sxs-lookup"><span data-stu-id="65d43-172">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="65d43-173">自動的に生成されますコンパイラでは、反復子を検出すると、 `Current`、 `MoveNext`、および`Dispose`のメソッド、<xref:System.Collections.IEnumerator>または<xref:System.Collections.Generic.IEnumerator%601>インターフェイス</xref:System.Collections.Generic.IEnumerator%601></xref:System.Collections.IEnumerator>。</span><span class="sxs-lookup"><span data-stu-id="65d43-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="65d43-174">一連の各イテレーションで、`For Each…Next`ループ (または直接の呼び出し`IEnumerator.MoveNext`)、次の反復子コード本体が、前の後に再開`Yield`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="65d43-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="65d43-175">次に続きます`Yield`ステートメント、反復子本体の末尾に到達するまでになるか、`Exit Function`または`Return`ステートメントが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="65d43-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>  
  
 <span data-ttu-id="65d43-176">反復子をサポートしていない、<xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName>メソッド</xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="65d43-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="65d43-177">最初から再反復処理するには、新しい反復子を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65d43-177">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="65d43-178">詳細については、次を参照してください。、 [Visual Basic 言語仕様](../../../visual-basic/reference/language-specification.md)します。</span><span class="sxs-lookup"><span data-stu-id="65d43-178">For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md).</span></span>  
  
##  <span data-ttu-id="65d43-179"><a name="BKMK_UseOfIterators"></a>反復子の使用</span><span class="sxs-lookup"><span data-stu-id="65d43-179"><a name="BKMK_UseOfIterators"></a> Use of Iterators</span></span>  
 <span data-ttu-id="65d43-180">反復子を使用するの簡潔さを維持するために、`For Each`リストの順番を設定する複雑なコードを使用する必要がある場合をループします。</span><span class="sxs-lookup"><span data-stu-id="65d43-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="65d43-181">次の操作を実行するときに便利になります。</span><span class="sxs-lookup"><span data-stu-id="65d43-181">This can be useful when you want to do the following:</span></span>  
  
-   <span data-ttu-id="65d43-182">1 つ目後のリストの順番の変更`For Each`イテレーションをループします。</span><span class="sxs-lookup"><span data-stu-id="65d43-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>  
  
-   <span data-ttu-id="65d43-183">最初のイテレーションの前に大きなリストが完全に読み込まれないように、`For Each`ループします。</span><span class="sxs-lookup"><span data-stu-id="65d43-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="65d43-184">例では、テーブル行のバッチをロードするページのフェッチを示します。</span><span class="sxs-lookup"><span data-stu-id="65d43-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="65d43-185">別の例は、<xref:System.IO.DirectoryInfo.EnumerateFiles%2A>メソッドで、.NET Framework 内での反復子を実装します</xref:System.IO.DirectoryInfo.EnumerateFiles%2A>。</span><span class="sxs-lookup"><span data-stu-id="65d43-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
-   <span data-ttu-id="65d43-186">反復子のリストの作成をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="65d43-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="65d43-187">Iterator メソッドのリストを作成し、ループ内では、各結果を生成できます。</span><span class="sxs-lookup"><span data-stu-id="65d43-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d43-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="65d43-188">See Also</span></span>  
 <span data-ttu-id="65d43-189"><xref:System.Collections.Generic></xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="65d43-189"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="65d43-190"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="65d43-190"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="65d43-191"> [各.次のステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="65d43-191"> [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="65d43-192"> [Yield ステートメント](../../../visual-basic/language-reference/statements/yield-statement.md) </span><span class="sxs-lookup"><span data-stu-id="65d43-192"> [Yield Statement](../../../visual-basic/language-reference/statements/yield-statement.md) </span></span>  
<span data-ttu-id="65d43-193"> [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)</span><span class="sxs-lookup"><span data-stu-id="65d43-193"> [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)</span></span>
