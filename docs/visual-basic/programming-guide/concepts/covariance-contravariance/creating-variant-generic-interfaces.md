---
title: "バリアント ジェネリック インターフェイス (Visual Basic) を作成する |Microsoft ドキュメント"
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
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 324e2a906e84950aa9019bbf68a524458492646e
ms.lasthandoff: 03/13/2017

---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>バリアント ジェネリック インターフェイス (Visual Basic) の作成
共変性のインターフェイスのジェネリック型パラメーターを宣言するまたは反変です。 *ジェネリックの共変性*インターフェイス メソッドのジェネリック型パラメーターで定義されているよりも戻り値の型の派生を許可します。 *反変性*インターフェイス メソッドには、ジェネリック パラメーターで指定されているよりも弱い派生の引数の型を持つことができます。 ジェネリック インターフェイスを持つ共変または反変のジェネリック型パラメーターと呼ばれる*バリアント*します。  
  
> [!NOTE]
>  .NET framework 4 には、いくつかの既存のジェネリック インターフェイスの分散のサポートが導入されました。 .NET Framework のバリアントのインターフェイスの一覧で、次を参照してください。[ジェネリック インターフェイス (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)します。  
  
## <a name="declaring-variant-generic-interfaces"></a>バリアント ジェネリック インターフェイスを宣言します。  
 バリアント ジェネリック インターフェイスを宣言するにを使用して、`in`と`out`ジェネリック型パラメーターのキーワードです。  
  
> [!IMPORTANT]
>  `ByRef`Visual Basic でのパラメーターは、バリアント型にすることはできません。 また、値型では、分散はサポートされません。  
  
 宣言するジェネリック型パラメーター共変性を使用して、`out`キーワードです。 共変の型は、次の条件を満たしている必要があります。  
  
-   型がインターフェイス メソッドの戻り値の型としてのみ使用され、メソッド引数の型として使用できません。 これで、次の例に示すは種類`R`共変で宣言されています。  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     この規則には例外が&1; つあります。 メソッド パラメーターとして反変のジェネリック デリゲートをした場合は、デリゲートのジェネリック型パラメーターとして型を使用できます。 型でその例を示します`R`次の例です。 詳細については、次を参照してください。[デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)と[用 Func および Action 汎用デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)します。  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   種類は、インターフェイス メソッドのジェネリック制約として使用されません。 これは、次のコードに示します。  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 使用してジェネリック型パラメーターの反変性を宣言することができます、`in`キーワードです。 反変の型は、インターフェイス メソッドの戻り値の型としてではなく、メソッド引数の型としてのみ使用できます。 反変の型は、ジェネリック制約にも使用できます。 次のコードでは、反変のインターフェイスを宣言し、そのメソッドのいずれかに汎用的な制約を使用する方法を示します。  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 次のコード例のようには、同じインターフェイスが異なる型のパラメーターの共変性と反変性の両方をサポートすることもです。  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 Visual Basic では、デリゲート型を指定することがなくバリアント インターフェイスのイベントを宣言できません。 また、variant インターフェイスがクラス、列挙、または構造体で入れ子になっている必要しますが、インターフェイスを入れ子にできます。 これは、次のコードに示します。  
  
```vb  
Interface ICovariant(Of Out R)  
    ' The following statement generates a compiler error.  
    ' Event SampleEvent()  
    ' The following statement specifies the delegate type and   
    ' does not generate an error.  
    Event AnotherEvent As EventHandler  
  
    ' The following statements generate compiler errors,  
    ' because a variant interface cannot have  
    ' nested enums, classes, or structures.  
  
    'Enum SampleEnum : test : End Enum  
    'Class SampleClass : End Class  
    'Structure SampleStructure : Dim value As Integer : End Structure  
  
    ' Variant interfaces can have nested interfaces.  
    Interface INested : End Interface  
End Interface  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>バリアント ジェネリック インターフェイスを実装します。  
 クラスのバリアント ジェネリック インターフェイスを実装するには、ロケールに依存しないインターフェイスに使用されるのと同じ構文を使用します。 次のコード例では、ジェネリック クラスに、共変のインターフェイスを実装する方法を示します。  
  
```vb  
Interface ICovariant(Of Out R)  
    Function GetSomething() As R  
End Interface  
  
Class SampleImplementation(Of R)  
    Implements ICovariant(Of R)  
    Public Function GetSomething() As R _  
    Implements ICovariant(Of R).GetSomething  
        ' Some code.  
    End Function  
End Class  
```  
  
 バリアント型のインターフェイスを実装するクラスは変化しません。 次に例を示します。  
  
```vb  
 The interface is covariant.  
Dim ibutton As ICovariant(Of Button) =  
    New SampleImplementation(Of Button)  
Dim iobj As ICovariant(Of Object) = ibutton  
  
' The class is invariant.  
Dim button As SampleImplementation(Of Button) =  
    New SampleImplementation(Of Button)  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim obj As SampleImplementation(Of Object) = button  
```  
  
## <a name="extending-variant-generic-interfaces"></a>バリアント ジェネリック インターフェイスの拡張  
 使用する必要があるバリアント ジェネリック インターフェイスを拡張するときに、`in`と`out`派生インターフェイスで変性をサポートするかどうかを明示的に指定するキーワードです。 コンパイラは、拡張されているインターフェイスからの差異を推論できません。 たとえば、次のインターフェイスがあるとします。  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T)  
End Interface  
  
Interface IExtCovariant(Of Out T)  
    Inherits ICovariant(Of T)  
End Interface  
```  
  
 `Invariant(Of T)`インターフェイス、ジェネリック型パラメーター`T`バリアントで`IExtCovariant (Of Out T)`型パラメーターが共変で両方のインターフェイスは、同じインターフェイスを拡張します。 同じ規則には、反変のジェネリック型パラメーターに適用されます。  
  
 ジェネリック型パラメーターで、インターフェイスを拡張するインターフェイスを作成する`T`が共変とインターフェイスのジェネリック型パラメーターの場合の反変、拡張の場合は、インターフェイス`T`バリアント型ではありません。 これは、次のコード例に示します。  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 ただし、ジェネリック型パラメーター`T`は&1; つのインターフェイスの宣言と共変は宣言できません反変拡張するインターフェイスまたはその逆です。 これは、次のコード例に示します。  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>あいまいさを回避します。  
 バリアント ジェネリック インターフェイスを実装するときに分散できる場合もありますわかりにくくなる場合します。 このような状況は回避する必要があります。  
  
 たとえば、1 つのクラスで明示的に別のジェネリック型パラメーターを持つ同じバリアント ジェネリック インターフェイスを実装する場合のあいまいさを作成できます。 コンパイラ エラーは発生しませんが、ここでは、するインターフェイスの実装は、実行時に選択が指定されていません。 これにより、コードで軽度のバグです。 次のコード例を検討してください。  
  
> [!NOTE]
>  `Option Strict Off`、Visual Basic では、あいまいなインターフェイスの実装がある場合に、コンパイラの警告が生成されます。 `Option Strict On`、Visual Basic コンパイラ エラーが生成されます。  
  
```vb  
' Simple class hierarchy.  
Class Animal  
End Class  
  
Class Cat  
    Inherits Animal  
End Class  
  
Class Dog  
    Inherits Animal  
End Class  
  
' This class introduces ambiguity  
' because IEnumerable(Of Out T) is covariant.  
Class Pets  
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)  
  
    Public Function GetEnumerator() As IEnumerator(Of Cat) _  
        Implements IEnumerable(Of Cat).GetEnumerator  
        Console.WriteLine("Cat")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator(Of Dog) _  
        Implements IEnumerable(Of Dog).GetEnumerator  
        Console.WriteLine("Dog")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator2() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
        ' Some code.  
    End Function  
End Class  
  
Sub Main()  
    Dim pets As IEnumerable(Of Animal) = New Pets()  
    pets.GetEnumerator()  
End Sub  
```  
  
 この例では指定されていないか、`pets.GetEnumerator`メソッドによって選択される`Cat`と`Dog`です。 これにより、コードで問題が発生する可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [ジェネリック インターフェイス (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)   
 [Func および Action 汎用デリゲート (Visual Basic) に対する分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
