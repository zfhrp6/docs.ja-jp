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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4ea1e21bd8cc392889c477e78338384ed05d4cbb
ms.lasthandoff: 03/13/2017

---
# <a name="iterators-visual-basic"></a>反復子 (Visual Basic)
*反復子*コレクションのステップ実行の一覧し、配列などに使用できます。  
  
 Iterator メソッドまたは`get`アクセサーは、コレクションに対するカスタム イテレーションを実行します。 Iterator メソッドを使用して、 [Yield](../../../visual-basic/language-reference/statements/yield-statement.md)ステートメントを一度に&1; つの各要素を返します。 ときに、`Yield`ステートメントに達すると、コード内の現在位置が記憶されます。 次回の反復子関数が呼び出されたとき、その場所から実行が再開されます。  
  
 使用してクライアント コードから反復子を使用する、[ごとにしています.次](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメント、または LINQ クエリを使用しています。  
  
 次の例の最初のイテレーションで、`For Each`ループが実行を続行すると、`SomeNumbers`最初まで反復子メソッド`Yield`ステートメントに到達します。 このイテレーションは第 3 の値を返し、iterator メソッドの現在位置が保持されます。 ループの次の反復処理では、iterator メソッドの実行が場所から続行し、もう一度停止になったときに中断、`Yield`ステートメントです。 このイテレーションは 5 の値を返し、iterator メソッドの現在位置が保持されます再。 Iterator メソッドの終わりに達したときに、ループが完了します。  
  
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
  
 Iterator メソッドの戻り値の型または`get`アクセサーは、 <xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または<xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable>  
  
 使用することができます、`Exit Function`または`Return`ステートメント、反復を終了します。  
  
 Visual Basic の反復子関数または`get`アクセサー宣言が含まれる、[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)修飾子です。  
  
 Visual Studio 2012 で Visual Basic では、反復子が導入されています。  
  
 **このトピックの内容**  
  
-   [単純な反復子](#BKMK_SimpleIterator)  
  
-   [コレクション クラスを作成します。](#BKMK_CollectionClass)  
  
-   [Try ブロック](#BKMK_TryBlocks)  
  
-   [匿名メソッド](#BKMK_AnonymousMethods)  
  
-   [ジェネリック リストと共に反復子の使用](#BKMK_GenericList)  
  
-   [構文情報](#BKMK_SyntaxInformation)  
  
-   [技術的な実装](#BKMK_Technical)  
  
-   [反復子の使用](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  トピックの「単純な反復子の使用例を除くすべての例については、含める[Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ステートメントを、`System.Collections`と`System.Collections.Generic`名前空間。  
  
##  <a name="BKMK_SimpleIterator"></a>単純な反復子  
 次の例は、1 つ`Yield`ステートメント内にある、[にしています.次](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。 `Main`の各反復処理、`For Each`ステートメント本体を次の手順を実行する反復子関数の呼び出しを作成`Yield`ステートメントです。  
  
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
  
##  <a name="BKMK_CollectionClass"></a>コレクション クラスを作成します。  
 次の例では、`DaysOfTheWeek`クラスが実装する、<xref:System.Collections.IEnumerable>インターフェイスを必要とする、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッド</xref:System.Collections.IEnumerable.GetEnumerator%2A></xref:System.Collections.IEnumerable>。 コンパイラが暗黙的に呼び出す、 `GetEnumerator` <xref:System.Collections.IEnumerator>.</xref:System.Collections.IEnumerator>を返すメソッド  
  
 `GetEnumerator`メソッドを使用して、一度に&1; つの各文字列を返します、`Yield`ステートメント、および`Iterator`修飾子は関数宣言では。  
  
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
  
 次の例を作成し、`Zoo`動物のコレクションを格納するクラス。  
  
 `For Each`クラスのインスタンスを参照するステートメント (`theZoo`) を暗黙的に呼び出す、`GetEnumerator`メソッドです。 `For Each`を参照するステートメント、`Birds`と`Mammals`プロパティを使用して、 `AnimalsForType` iterator メソッドの名前します。  
  
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
  
##  <a name="BKMK_TryBlocks"></a>Try ブロック  
 Visual Basic では、`Yield`内のステートメントで、`Try`のブロック、[しようとしています.キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。 A`Try`がブロック、`Yield`ステートメントにはできます`Catch`ブロック、およびことができますが、`Finally`ブロックします。  
  
 次の例が含まれます`Try`、 `Catch`、および`Finally`では、反復子関数をブロックします。 `Finally` Iterator 関数内のブロックを実行する前に、`For Each`イテレーションが完了するとします。  
  
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
  
 A`Yield`ステートメント内で使用できない、`Catch`ブロックまたは`Finally`ブロックします。  
  
 場合、`For Each`本体 (iterator メソッド) ではなく、例外がスロー、 `Catch` iterator 関数内のブロックは実行されませんが、`Finally`反復子関数でのブロックを実行します。 A`Catch`反復子関数の内側のブロックは、反復子関数内で発生する例外だけをキャッチします。  
  
##  <a name="BKMK_AnonymousMethods"></a>匿名メソッド  
 Visual basic では、iterator 関数が匿名関数にできます。 次に例を示します。  
  
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
  
 次の例では、引数を検証する非反復子メソッドがあります。 このメソッドは、匿名、コレクションの要素を示す反復子の結果を返します。  
  
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
  
 最初のイテレーションの開始まで、検証を実行できない検証が代わりに反復子関数の内部である場合は、`For Each`本文。  
  
##  <a name="BKMK_GenericList"></a>ジェネリック リストと共に反復子の使用  
 次の例では、`Stack(Of T)`ジェネリック クラスが実装する、<xref:System.Collections.Generic.IEnumerable%601>ジェネリック インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。 `Push`メソッドでは、型の配列に値を割り当てます`T`します。 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>メソッドを使用して配列の値を返す、`Yield`ステートメント</xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>。  
  
 ジェネリックだけでなく<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>メソッドは、非ジェネリック<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドを実装することがもする必要があります</xref:System.Collections.IEnumerable.GetEnumerator%2A></xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>。 これは、ため<xref:System.Collections.Generic.IEnumerable%601><xref:System.Collections.IEnumerable>.</xref:System.Collections.IEnumerable>から継承</xref:System.Collections.Generic.IEnumerable%601> 非ジェネリックの実装は、ジェネリックな実装に従います。  
  
 例では、さまざまなデータの同じコレクションを反復処理する方法をサポートするために名前付きの反復子を使用します。 これらの反復子を名前付き、`TopToBottom`と`BottomToTop`プロパティ、および`TopN`メソッドです。  
  
 `BottomToTop`プロパティ宣言が含まれる、`Iterator`キーワードです。  
  
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
  
##  <a name="BKMK_SyntaxInformation"></a>構文情報  
 メソッドとして発生することが、反復子または`get`アクセサー。 反復子は、イベント、コンス トラクター、静的コンス トラクターまたは静的のデストラクターで発生することはできません。  
  
 式の型から暗黙的な変換が存在する必要があります、`Yield`ステートメント、反復子の戻り値の型。  
  
 Visual Basic では、iterator メソッドは指定できません`ByRef`パラメーター。  
  
 Visual basic で「メリットをもたらす」予約語ではない、特別な意味で使用されている場合にのみ、`Iterator`メソッドまたは`get`アクセサー。  
  
##  <a name="BKMK_Technical"></a>技術的な実装  
 メソッドとして、反復子を記述しても、コンパイラが il 変換を入れ子になったクラスには、実際には、ステート マシンです。 このクラスには、時間と反復子の位置の追跡`For Each...Next`クライアント コードでのループが継続されます。  
  
 コンパイラが何を表示するには、iterator メソッドに対して生成される Microsoft 中間言語コードを表示するのに、Ildasm.exe ツールを使用することができます。  
  
 反復子を作成する場合、[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)、全体を実装する必要はありません<xref:System.Collections.IEnumerator>インターフェイス</xref:System.Collections.IEnumerator>。 自動的に生成されますコンパイラでは、反復子を検出すると、 `Current`、 `MoveNext`、および`Dispose`のメソッド、<xref:System.Collections.IEnumerator>または<xref:System.Collections.Generic.IEnumerator%601>インターフェイス</xref:System.Collections.Generic.IEnumerator%601></xref:System.Collections.IEnumerator>。  
  
 一連の各イテレーションで、`For Each…Next`ループ (または直接の呼び出し`IEnumerator.MoveNext`)、次の反復子コード本体が、前の後に再開`Yield`ステートメントです。 次に続きます`Yield`ステートメント、反復子本体の末尾に到達するまでになるか、`Exit Function`または`Return`ステートメントが見つかりました。  
  
 反復子をサポートしていない、<xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName>メソッド</xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName>。 最初から再反復処理するには、新しい反復子を取得する必要があります。  
  
 詳細については、次を参照してください。、 [Visual Basic 言語仕様](../../../visual-basic/reference/language-specification.md)します。  
  
##  <a name="BKMK_UseOfIterators"></a>反復子の使用  
 反復子を使用するの簡潔さを維持するために、`For Each`リストの順番を設定する複雑なコードを使用する必要がある場合をループします。 次の操作を実行するときに便利になります。  
  
-   1 つ目後のリストの順番の変更`For Each`イテレーションをループします。  
  
-   最初のイテレーションの前に大きなリストが完全に読み込まれないように、`For Each`ループします。 例では、テーブル行のバッチをロードするページのフェッチを示します。 別の例は、<xref:System.IO.DirectoryInfo.EnumerateFiles%2A>メソッドで、.NET Framework 内での反復子を実装します</xref:System.IO.DirectoryInfo.EnumerateFiles%2A>。  
  
-   反復子のリストの作成をカプセル化します。 Iterator メソッドのリストを作成し、ループ内では、各結果を生成できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic></xref:System.Collections.Generic>   
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 [各.次のステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Yield ステートメント](../../../visual-basic/language-reference/statements/yield-statement.md)   
 [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
