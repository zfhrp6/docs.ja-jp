---
title: "コレクション (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b3c8de3e22075d576f86bcd4eb599946740ebe16
ms.lasthandoff: 03/13/2017

---
# <a name="collections-visual-basic"></a>コレクション (Visual Basic)
多くのアプリケーションで、関連するオブジェクトのグループの作成および管理が必要になります。 オブジェクトをグループ化するには、オブジェクトの配列を作成する方法と、オブジェクトのコレクションを作成する方法があります。  
  
 配列は、数が固定されている厳密に型指定されたオブジェクトの作成および処理に最も適しています。 配列の概要については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
 コレクションは、オブジェクトのグループをより柔軟に処理できます。 配列の場合とは違って、コレクションで扱うオブジェクトのグループは、アプリケーションの変更に伴う必要に応じて動的に拡大および縮小できます。 コレクションによっては、コレクションに含まれるオブジェクトのキーを割り当てると、そのキーを使用してオブジェクトを迅速に取り出すことができます。  
  
 コレクションはクラスであるため、そのコレクションに要素を追加するには、事前にそのクラスのインスタンスを宣言する必要があります。  
  
 コレクションに&1; つのデータ型の要素が含まれている場合は、クラスでは、いずれかを使用、<xref:System.Collections.Generic?displayProperty=fullName>名前空間</xref:System.Collections.Generic?displayProperty=fullName>。 ジェネリック コレクションでは、タイプ セーフが強制されるため、他のデータ型を追加することはできません。 ジェネリック コレクションから要素を取得する場合は、データ型を判断したり、変換したりする必要はありません。  
  
> [!NOTE]
>  このトピックの例に、 [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ステートメントを`System.Collections.Generic`と`System.Linq`名前空間。  
  
 **このトピックの内容**  
  
-   [単純なコレクションを使用します。](#BKMK_SimpleCollection)  
  
-   [コレクションの種類](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic のクラス](#BKMK_Generic)  
  
    -   [System.Collections.Concurrent のクラス](#BKMK_Concurrent)  
  
    -   [System.Collections のクラス](#BKMK_Collections)  
  
    -   [Visual Basic のコレクション クラス](#BKMK_VisualBasic)  
  
-   [キー/値ペアのコレクションを実装します。](#BKMK_KeyValuePairs)  
  
-   [LINQ を使用して、コレクションにアクセスするには](#BKMK_LINQ)  
  
-   [コレクションを並べ替える](#BKMK_Sorting)  
  
-   [カスタム コレクションを定義します。](#BKMK_CustomCollection)  
  
-   [反復子](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>単純なコレクションを使用する  
 このセクションの例では、ジェネリックを使用して<xref:System.Collections.Generic.List%601>クラスで、この厳密に型指定されたオブジェクトの一覧を使用することができます</xref:System.Collections.Generic.List%601>。  
  
 次の例は、文字列のリストを作成しを使用して、文字列を使用して反復処理し、[ごとにしています.次](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメントです。  
  
```vb  
' Create a list of strings.  
Dim salmons As New List(Of String)  
salmons.Add("chinook")  
salmons.Add("coho")  
salmons.Add("pink")  
salmons.Add("sockeye")  
  
' Iterate through the list.  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 使用することができます、コレクションの内容が事前にわかっている場合、*コレクション初期化子*コレクションを初期化します。 詳細については、次を参照してください。[コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)します。  
  
 次の例は、コレクションへの要素の追加にコレクション初期化子を使用する以外、前の例と同じです。  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 使用することができます、[にしています.次](../../../visual-basic/language-reference/statements/for-next-statement.md)ステートメントの代わりに、`For Each`コレクションを反復処理します。 インデックス位置によってコレクションの要素にアクセスすることで、これを実現します。 要素のインデックスは、0 から開始し、要素の数から 1 少ない値で終了します。  
  
 次の例は、`For…Next` の代わりに `For Each` を使用して、コレクションの要素を反復処理します。  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 次の例は、削除するオブジェクトを指定して、コレクションから要素を削除します。  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
' Remove an element in the list by specifying  
' the object.  
salmons.Remove("coho")  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook pink sockeye  
```  
  
 次の例では、ジェネリック リストからすべての要素を削除します。 代わりに、`For Each`ステートメント、[にしています.次](../../../visual-basic/language-reference/statements/for-next-statement.md)降順に反復処理するステートメントを使用します。 これは、<xref:System.Collections.Generic.List%601.RemoveAt%2A>メソッドが低いインデックス値を持つ削除された要素の後に要素をにより</xref:System.Collections.Generic.List%601.RemoveAt%2A>。  
  
```vb  
Dim numbers As New List(Of Integer) From  
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}  
  
' Remove odd numbers.  
For index As Integer = numbers.Count - 1 To 0 Step -1  
    If numbers(index) Mod 2 = 1 Then  
        ' Remove the element by specifying  
        ' the zero-based index in the list.  
        numbers.RemoveAt(index)  
    End If  
Next  
  
' Iterate through the list.  
' A lambda expression is placed in the ForEach method  
' of the List(T) object.  
numbers.ForEach(  
    Sub(number) Console.Write(number & " "))  
' Output: 0 2 4 6 8  
```  
  
 で<xref:System.Collections.Generic.List%601>、独自のクラスを定義することも、</xref:System.Collections.Generic.List%601>要素の型の 次の例で、`Galaxy`クラスによって使用される、 <xref:System.Collections.Generic.List%601>、コードで定義されています</xref:System.Collections.Generic.List%601>。  
  
```vb  
Private Sub IterateThroughList()  
    Dim theGalaxies As New List(Of Galaxy) From  
        {  
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},  
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},  
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},  
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}  
        }  
  
    For Each theGalaxy In theGalaxies  
        With theGalaxy  
            Console.WriteLine(.Name & "  " & .MegaLightYears)  
        End With  
    Next  
  
    ' Output:  
    '  Tadpole  400  
    '  Pinwheel  25  
    '  Milky Way  0  
    '  Andromeda  3  
End Sub  
  
Public Class Galaxy  
    Public Property Name As String  
    Public Property MegaLightYears As Integer  
End Class  
```  
  
<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a>コレクションの種類   
 .NET Framework は、多くの共通のコレクションを提供します。 各コレクションの型は、固有の目的に合わせてデザインされています。  
  
 このセクションでは、次の共通のコレクション クラスをいつくか説明します:  
  
-   @System.Collections.Generic クラス  
  
-   @System.Collections.Concurrent クラス  
  
-   @System.Collections クラス  
  
-   Visual Basic の `Collection` クラス  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>System.Collections.Generic のクラス  

 ジェネリック コレクションを作成するにはクラスでは、いずれかを使用して、<xref:System.Collections.Generic>名前空間</xref:System.Collections.Generic>。 ジェネリック コレクションは、コレクション内のすべての項目が同じデータ型である場合に便利です。 ジェネリック コレクションには該当するデータ型しか追加できないため、厳密な型指定が適用されます。  
  
 次の表の頻繁に使用されるクラスの一覧、<xref:System.Collections.Generic?displayProperty=fullName>名前空間:</xref:System.Collections.Generic?displayProperty=fullName>  
  
|クラス|説明|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602></xref:System.Collections.Generic.Dictionary%602>|キーに基づいて編成された、キーと値のペアのコレクションを表します。|  
|<xref:System.Collections.Generic.List%601></xref:System.Collections.Generic.List%601>|インデックスを使用してアクセスできる、オブジェクトの一覧を表します。 リストの検索、並べ替え、および変更のメソッドを提供します。|  
|<xref:System.Collections.Generic.Queue%601></xref:System.Collections.Generic.Queue%601>|先入れ先出し (FIFO) のオブジェクトのコレクションを表します。|  
|<xref:System.Collections.Generic.SortedList%602></xref:System.Collections.Generic.SortedList%602>|関連付けられたに基づいてキーにより並べ替えられたキー/値ペアのコレクションを表す<xref:System.Collections.Generic.IComparer%601>実装</xref:System.Collections.Generic.IComparer%601>。|  
|<xref:System.Collections.Generic.Stack%601></xref:System.Collections.Generic.Stack%601>|後入れ先出し (LIFO) のオブジェクトのコレクションを表します。|  
  
 詳細については、次を参照してください[よく使用されるコレクション型](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55)、[コレクション クラスの選択](../../../standard/collections/selecting-a-collection-class.md)、 <xref:System.Collections.Generic?displayProperty=fullName>.</xref:System.Collections.Generic?displayProperty=fullName> 。  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>System.Collections.Concurrent のクラス   
 .NET Framework 4 またはそれ以降のコレクションで、<xref:System.Collections.Concurrent>名前空間は、複数のスレッドからコレクション項目にアクセスするための効率的なスレッド セーフな操作を提供します</xref:System.Collections.Concurrent>。  
  
 内のクラス、<xref:System.Collections.Concurrent>名前空間は、対応する型の代わりに使用する必要があります、<xref:System.Collections.Generic?displayProperty=fullName>と<xref:System.Collections?displayProperty=fullName>に、複数のスレッドがコレクションを同時にアクセスするたびに、名前空間</xref:System.Collections?displayProperty=fullName></xref:System.Collections.Generic?displayProperty=fullName></xref:System.Collections.Concurrent>。 詳細については、次を参照してください[スレッド セーフなコレクション](../../../standard/collections/threadsafe/index.md) <xref:System.Collections.Concurrent>.</xref:System.Collections.Concurrent> 。  
  
 含まれるいくつかのクラス、<xref:System.Collections.Concurrent>名前空間は<xref:System.Collections.Concurrent.BlockingCollection%601>、 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>、 <xref:System.Collections.Concurrent.ConcurrentQueue%601>、 <xref:System.Collections.Concurrent.ConcurrentStack%601>.</xref:System.Collections.Concurrent.ConcurrentStack%601> </xref:System.Collections.Concurrent.ConcurrentQueue%601> </xref:System.Collections.Concurrent.ConcurrentDictionary%602> </xref:System.Collections.Concurrent.BlockingCollection%601> </xref:System.Collections.Concurrent>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>System.Collections のクラス    
 内のクラス、<xref:System.Collections?displayProperty=fullName>型のオブジェクトが、具体的には型指定されたオブジェクトと名前空間が要素を格納しないで`Object`</xref:System.Collections?displayProperty=fullName>。  
  
 可能であれば、ジェネリック コレクションを使用する必要があります、<xref:System.Collections.Generic?displayProperty=fullName>名前空間または<xref:System.Collections.Concurrent>従来型の代わりに名前空間、`System.Collections`名前空間</xref:System.Collections.Concurrent></xref:System.Collections.Generic?displayProperty=fullName>。  
  
 次のテーブルは `System.Collections` 名前空間でよく使用されるクラスの一覧です:  
  
|クラス|説明|  
|---|---|  
|<xref:System.Collections.ArrayList></xref:System.Collections.ArrayList>|必要に応じてサイズが動的に拡大されるオブジェクトの配列を表します。|  
|<xref:System.Collections.Hashtable></xref:System.Collections.Hashtable>|キーのハッシュ コードに基づいて編成された、キーと値のペアのコレクションを表します。|  
|<xref:System.Collections.Queue></xref:System.Collections.Queue>|先入れ先出し (FIFO) のオブジェクトのコレクションを表します。|  
|<xref:System.Collections.Stack></xref:System.Collections.Stack>|後入れ先出し (LIFO) のオブジェクトのコレクションを表します。|  
  
 <xref:System.Collections.Specialized>名前空間には、文字列専用のコレクションやリンク リスト、ハイブリッド ディクショナリなどの厳密に型指定された専用のコレクション クラスが用意されています</xref:System.Collections.Specialized>。  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a>Visual Basic のコレクション クラス  
 Visual Basic を使用する<xref:Microsoft.VisualBasic.Collection>クラスや数値インデックスを使用して、項目コレクションのアクセスを`String`キー</xref:Microsoft.VisualBasic.Collection> 。 キーを指定してもしなくても、項目をコレクション オブジェクトに追加できます。 キーを使わずに項目を追加した場合は、その項目にアクセスするときに数値インデックスを使う必要があります。  
  
 Visual Basic の `Collection` クラスは、そのすべての要素を `Object` 型として保存するため、任意のデータ型の項目を追加できます。 不適切なデータ型が追加されないようにする保護機能はありません。  
  
 Visual Basic の `Collection` クラスを使用すると、コレクション内の最初の項目はインデックス 1 となります。 これは、インデックスが 0 から開始される .NET Framework のコレクション クラスとは異なります。  
  
 可能であれば、ジェネリック コレクションを使用する必要があります、<xref:System.Collections.Generic?displayProperty=fullName>名前空間または<xref:System.Collections.Concurrent>Visual Basic ではなく名前空間`Collection`クラス</xref:System.Collections.Concurrent></xref:System.Collections.Generic?displayProperty=fullName>  
  
 詳細については、 <xref:Microsoft.VisualBasic.Collection>。</xref:Microsoft.VisualBasic.Collection>を参照してください。  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>キーと値のペアのコレクションを実装する   
 <xref:System.Collections.Generic.Dictionary%602>ジェネリック コレクションでは、各要素のキーを使用して、コレクション内の要素にアクセスすることができます</xref:System.Collections.Generic.Dictionary%602>。 ディクショナリに追加される各エントリは、値とその値に関連付けられたキーで構成されます。 `Dictionary` クラスはハッシュ テーブルとして実装されているため、キーを使用した値の取得は非常に高速になります。  
  
 次の例では `Dictionary` のコレクションを作成し、`For Each` ステートメントを使用してディクショナリを反復処理します。  
  
```vb  
Private Sub IterateThroughDictionary()  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    For Each kvp As KeyValuePair(Of String, Element) In elements  
        Dim theElement As Element = kvp.Value  
  
        Console.WriteLine("key: " & kvp.Key)  
        With theElement  
            Console.WriteLine("values: " & .Symbol & " " &  
                .Name & " " & .AtomicNumber)  
        End With  
    Next  
End Sub  
  
Private Function BuildDictionary() As Dictionary(Of String, Element)  
    Dim elements As New Dictionary(Of String, Element)  
  
    AddToDictionary(elements, "K", "Potassium", 19)  
    AddToDictionary(elements, "Ca", "Calcium", 20)  
    AddToDictionary(elements, "Sc", "Scandium", 21)  
    AddToDictionary(elements, "Ti", "Titanium", 22)  
  
    Return elements  
End Function  
  
Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),  
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)  
    Dim theElement As New Element  
  
    theElement.Symbol = symbol  
    theElement.Name = name  
    theElement.AtomicNumber = atomicNumber  
  
    elements.Add(Key:=theElement.Symbol, value:=theElement)  
End Sub  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 コレクション初期化子を使用して `Dictionary` コレクションをビルドする代わりに、`BuildDictionary` および `AddToDictionary` メソッドを次のメソッドに置換できます。  
  
```vb  
Private Function BuildDictionary2() As Dictionary(Of String, Element)  
    Return New Dictionary(Of String, Element) From  
        {  
            {"K", New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {"Ca", New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {"Sc", New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {"Ti", New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
```  
  
 次の例では、<xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>メソッドおよび<xref:System.Collections.Generic.Dictionary%602.Item%2A>のプロパティ`Dictionary`キーによって項目をすばやく検索します</xref:System.Collections.Generic.Dictionary%602.Item%2A></xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>。 `Item`プロパティでは、項目にアクセスすることができます、`elements`を使用してコレクション、 `elements(symbol)` Visual basic コードです。  
  
```vb  
Private Sub FindInDictionary(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    If elements.ContainsKey(symbol) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Dim theElement = elements(symbol)  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
 代わりに次の例を使用して、<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>メソッドがキーによって項目をすばやく検索します</xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>。  
  
```vb  
Private Sub FindInDictionary2(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    Dim theElement As Element = Nothing  
    If elements.TryGetValue(symbol, theElement) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
<a name="BKMK_LINQ"></a> 
##  <a name="using-linq-to-access-a-collection"></a>LINQ を使用してコレクションにアクセスする  
 統合言語クエリ (LINQ) を使用してコレクションにアクセスできます。 LINQ クエリは、フィルター処理、並べ替え、およびグループ化の機能を提供します。 詳細については、次を参照してください。 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)します。  
  
 次の例では、ジェネリック `List` に対して LINQ クエリを実行します。 LINQ クエリは、結果が格納されている別のコレクションを戻します。  
  
```vb  
Private Sub ShowLINQ()  
    Dim elements As List(Of Element) = BuildList()  
  
    ' LINQ Query.  
    Dim subset = From theElement In elements  
                  Where theElement.AtomicNumber < 22  
                  Order By theElement.Name  
  
    For Each theElement In subset  
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)  
    Next  
  
    ' Output:  
    '  Calcium 20  
    '  Potassium 19  
    '  Scandium 21  
End Sub  
  
Private Function BuildList() As List(Of Element)  
    Return New List(Of Element) From  
        {  
            {New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <a name="BKMK_Sorting"></a> 
## <a name="sorting-a-collection"></a>コレクションを並べ替える  
 次の例では、コレクションを並べ替えるための手順を示しています。 この例のインスタンスの並べ替え、 `Car` <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601>に格納されているクラス `Car`クラスが実装する、<xref:System.IComparable%601>を必要とするインターフェイス、<xref:System.IComparable%601.CompareTo%2A>メソッドを実装する</xref:System.IComparable%601.CompareTo%2A></xref:System.IComparable%601>。  
  
 呼び出すたび、<xref:System.IComparable%601.CompareTo%2A>メソッドは、並べ替えに使用される単一の比較</xref:System.IComparable%601.CompareTo%2A>。 `CompareTo` メソッドのユーザーが作成したコードは、現在のオブジェクトと別のオブジェクトとの各比較の値を戻します。 現在のオブジェクトが別のオブジェクトよりも小さい場合はゼロ未満の値を、大きい場合はゼロ以上の値を、等しい場合はゼロを戻します。 これによって、より大きい、より小さい、等しい、の条件をコードに定義することができます。  
  
 `ListCars` のメソッドでは、`cars.Sort()` ステートメントがリストを並べ替えます。 この呼び出しを<xref:System.Collections.Generic.List%601.Sort%2A>のメソッド、<xref:System.Collections.Generic.List%601>により、`CompareTo`に対して自動的に呼び出されるメソッド、`Car`内のオブジェクト、 `List`</xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.List%601.Sort%2A> 。  
  
```vb  
Public Sub ListCars()  
  
    ' Create some new cars.  
    Dim cars As New List(Of Car) From  
    {  
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},  
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},  
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},  
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},  
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},  
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},  
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}  
    }  
  
    ' Sort the cars by color alphabetically, and then by speed  
    ' in descending order.  
    cars.Sort()  
  
    ' View all of the cars.  
    For Each thisCar As Car In cars  
        Console.Write(thisCar.Color.PadRight(5) & " ")  
        Console.Write(thisCar.Speed.ToString & " ")  
        Console.Write(thisCar.Name)  
        Console.WriteLine()  
    Next  
  
    ' Output:  
    '  blue  50 car4  
    '  blue  30 car5  
    '  blue  20 car1  
    '  green 50 car7  
    '  green 10 car3  
    '  red   60 car6  
    '  red   50 car2  
End Sub  
  
Public Class Car  
    Implements IComparable(Of Car)  
  
    Public Property Name As String  
    Public Property Speed As Integer  
    Public Property Color As String  
  
    Public Function CompareTo(ByVal other As Car) As Integer _  
        Implements System.IComparable(Of Car).CompareTo  
        ' A call to this method makes a single comparison that is  
        ' used for sorting.  
  
        ' Determine the relative order of the objects being compared.  
        ' Sort by color alphabetically, and then by speed in  
        ' descending order.  
  
        ' Compare the colors.  
        Dim compare As Integer  
        compare = String.Compare(Me.Color, other.Color, True)  
  
        ' If the colors are the same, compare the speeds.  
        If compare = 0 Then  
            compare = Me.Speed.CompareTo(other.Speed)  
  
            ' Use descending order for speed.  
            compare = -compare  
        End If  
  
        Return compare  
    End Function  
End Class  
```  
  
<a name="BKMK_CustomCollection"></a> 
## <a name="defining-a-custom-collection"></a>カスタム コレクションを定義する  
 コレクションを定義するには実装することによって、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Collections.IEnumerable>インターフェイス</xref:System.Collections.IEnumerable></xref:System.Collections.Generic.IEnumerable%601>。 詳細については、次を参照してください。[コレクションを列挙する](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f)です。  
  
 カスタム コレクションを定義するには、通常に説明されている .NET Framework に含まれているコレクションを使用するように[コレクションの種類](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)このトピックの前です。  
  
 次の例は、`AllColors` という名前のカスタム コレクション クラスを定義します。 このクラスは、実装、<xref:System.Collections.IEnumerable>を必要とするインターフェイス、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドを実装する</xref:System.Collections.IEnumerable.GetEnumerator%2A></xref:System.Collections.IEnumerable>。  
  
 `GetEnumerator` メソッドは、`ColorEnumerator` クラスのインスタンスを戻します。 `ColorEnumerator`実装して、<xref:System.Collections.IEnumerator>を必要とするインターフェイス、<xref:System.Collections.IEnumerator.Current%2A>プロパティには、<xref:System.Collections.IEnumerator.MoveNext%2A>メソッド、および<xref:System.Collections.IEnumerator.Reset%2A>メソッドを実装する</xref:System.Collections.IEnumerator.Reset%2A></xref:System.Collections.IEnumerator.MoveNext%2A></xref:System.Collections.IEnumerator.Current%2A></xref:System.Collections.IEnumerator>。  
  
```vb  
Public Sub ListColors()  
    Dim colors As New AllColors()  
  
    For Each theColor As Color In colors  
        Console.Write(theColor.Name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: red blue green  
End Sub  
  
' Collection class.  
Public Class AllColors  
    Implements System.Collections.IEnumerable  
  
    Private _colors() As Color =  
    {  
        New Color With {.Name = "red"},  
        New Color With {.Name = "blue"},  
        New Color With {.Name = "green"}  
    }  
  
    Public Function GetEnumerator() As System.Collections.IEnumerator _  
        Implements System.Collections.IEnumerable.GetEnumerator  
  
        Return New ColorEnumerator(_colors)  
  
        ' Instead of creating a custom enumerator, you could  
        ' use the GetEnumerator of the array.  
        'Return _colors.GetEnumerator  
    End Function  
  
    ' Custom enumerator.  
    Private Class ColorEnumerator  
        Implements System.Collections.IEnumerator  
  
        Private _colors() As Color  
        Private _position As Integer = -1  
  
        Public Sub New(ByVal colors() As Color)  
            _colors = colors  
        End Sub  
  
        Public ReadOnly Property Current() As Object _  
            Implements System.Collections.IEnumerator.Current  
            Get  
                Return _colors(_position)  
            End Get  
        End Property  
  
        Public Function MoveNext() As Boolean _  
            Implements System.Collections.IEnumerator.MoveNext  
            _position += 1  
            Return (_position < _colors.Length)  
        End Function  
  
        Public Sub Reset() Implements System.Collections.IEnumerator.Reset  
            _position = -1  
        End Sub  
    End Class  
End Class  
  
' Element class.  
Public Class Color  
    Public Property Name As String  
End Class  
```  
  
<a name="BKMK_Iterators"></a>
##  <a name="iterators"></a>反復子  
 *反復子*コレクションに対するカスタム イテレーションを実行するために使用します。 反復子は、メソッドまたは `get` アクセサーのいずれかです。 反復子を使用して、 [Yield](../../../visual-basic/language-reference/statements/yield-statement.md)ステートメントを一度に&1; つのコレクションの各要素を返します。  
  
 使用して、反復子を呼び出す、[ごとにしています.次](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメントです。 `For Each` ループの各イテレーションは、反復子を呼び出します。 ときに、`Yield`反復子でステートメントに達すると、式が返され、コードの現在位置が保持されます。 次回、反復子が呼び出されると、この位置から実行が再開されます。  
  
 詳細については、次を参照してください。[反復子 (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md)します。  
  
 次の例は、Iterator メソッドを使用します。 Iterator メソッドには、`Yield`ステートメント内にある、[にしています.次](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。 `ListEvenNumbers`メソッドは、の各反復処理、`For Each`ステートメント本体を次の手順を実行する反復子メソッドの呼び出しを作成`Yield`ステートメントです。  
  
```vb  
Public Sub ListEvenNumbers()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    Console.WriteLine()  
    ' Output: 6 8 10 12 14 16 18  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As IEnumerable(Of Integer)  
  
' Yield even numbers in the range.  
    For number = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
## <a name="see-also"></a>関連項目  
 [コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [プログラミングの概念 (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)   
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [Parallel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)   
 [コレクションとデータ構造体](../../../standard/collections/index.md)   
 [作成して、コレクションの操作](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069)   
 [コレクション クラスの選択](../../../standard/collections/selecting-a-collection-class.md)   
 [比較とコレクション内で並べ替え](../../../standard/collections/comparisons-and-sorts-within-collections.md)   
 [ジェネリック コレクションを使用する状況](../../../standard/collections/when-to-use-generic-collections.md)
