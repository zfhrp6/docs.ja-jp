---
title: "デリゲート (Visual Basic) の分散 |Microsoft ドキュメント"
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
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
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
ms.openlocfilehash: cbab7da8c97ca202f8a4d0a1a65b8fa240cca32d
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-delegates-visual-basic"></a>デリゲート (Visual Basic) の分散
.NET framework 3.5 には、c# および Visual Basic でのすべてのデリゲートでのデリゲート型でメソッドのシグネチャに一致する、変性のサポートが導入されました。 割り当てることができるこの手段は、一致するシグネチャがあるメソッドだけでなくよりも強い派生型 (共変性) またはデリゲート型で指定されているよりも弱い派生型 (反変性) のパラメーターを受け取るを返すメソッドも代行させます。 これには、ジェネリックと非ジェネリック デリゲートが含まれます。  
  
 たとえば、次のコードは、2 つのクラスと&2; つのデリゲート: ジェネリックと非ジェネリックです。  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 デリゲートを作成するときに、`SampleDelegate`または`SampleDelegate(Of A, R)`型、それらのデリゲートを次のいずれかに割り当てることができます。  
  
```vb  
' Matching signature.  
Public Shared Function ASecondRFirst(  
    ByVal second As Second) As First  
    Return New First()  
End Function  
  
' The return type is more derived.  
Public Shared Function ASecondRSecond(  
    ByVal second As Second) As Second  
    Return New Second()  
End Function  
  
' The argument type is less derived.  
Public Shared Function AFirstRFirst(  
    ByVal first As First) As First  
    Return New First()  
End Function  
  
' The return type is more derived   
' and the argument type is less derived.  
Public Shared Function AFirstRSecond(  
    ByVal first As First) As Second  
    Return New Second()  
End Function  
```  
  
 次のコード例は、メソッド シグネチャとデリゲート型の間の暗黙的な変換を示しています。  
  
```vb  
' Assigning a method with a matching signature   
' to a non-generic delegate. No conversion is necessary.  
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a non-generic delegate.  
' The implicit conversion is used.  
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond  
  
' Assigning a method with a matching signature to a generic delegate.  
' No conversion is necessary.  
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a generic delegate.  
' The implicit conversion is used.  
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond  
```  
  
 例については、次を参照してください。[デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)と[用 Func および Action 汎用デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)します。  
  
## <a name="variance-in-generic-type-parameters"></a>ジェネリック型パラメーターの分散  
 .NET Framework 4 およびそれ以降は、分散に必要な個々 の型が継承されている場合、相互にジェネリック型パラメーターで指定された別の型を持つ汎用デリゲートを割り当てることができるように、デリゲートの間の暗黙的な変換を有効にできます。  
  
 暗黙的な変換を有効にするのには、共変としてのデリゲートのジェネリック パラメーター明示的に宣言する必要がありますと反変性を使用して、`in`または`out`キーワードです。  
  
 次のコード例では、共変のジェネリック型パラメーターを持つデリゲートを作成する方法を示します。  
  
```vb  
' Type T is declared covariant by using the out keyword.  
Public Delegate Function SampleGenericDelegate(Of Out T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
    ' You can assign delegates to each other,  
    ' because the type T is declared covariant.  
    Dim dObject As SampleGenericDelegate(Of Object) = dString  
End Sub  
```  
  
 一致するようにのみ、変性のサポートを使用する場合、メソッドのシグネチャはデリゲート型し、使用しないでください、`in`と`out`キーワード、同一のラムダ式またはメソッドを持つデリゲートをインスタンス化することもありますが、別に&1; つのデリゲートを割り当てることはできませんを見つけることがあります。  
  
 次のコード例では`SampleGenericDelegate(Of String)`に明示的に変換できない`SampleGenericDelegate(Of Object)`いますが、`String`継承`Object`します。 この問題を解決するには、ジェネリック パラメーターをマークすることによって`T`で、`out`キーワードです。  
  
```vb  
Public Delegate Function SampleGenericDelegate(Of T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
  
    ' You can assign the dObject delegate  
    ' to the same lambda expression as dString delegate  
    ' because of the variance support for   
    ' matching method signatures with delegate types.  
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "  
  
    ' The following statement generates a compiler error  
    ' because the generic type T is not marked as covariant.  
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString  
  
End Sub  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET framework の型パラメーターをバリアントを持つ汎用デリゲート  
 .NET framework 4 には、いくつかの既存の汎用デリゲートのジェネリック型パラメーターの分散のサポートが導入されています。  
  
-   `Action`デリゲート、<xref:System>名前空間、たとえば、<xref:System.Action%601>と<xref:System.Action%602></xref:System.Action%602></xref:System.Action%601></xref:System>  
  
-   `Func`デリゲート、<xref:System>名前空間、たとえば、<xref:System.Func%601>と<xref:System.Func%602></xref:System.Func%602></xref:System.Func%601></xref:System>  
  
-   <xref:System.Predicate%601>委任します。</xref:System.Predicate%601>  
  
-   <xref:System.Comparison%601>委任します。</xref:System.Comparison%601>  
  
-   <xref:System.Converter%602>委任します。</xref:System.Converter%602>  
  
 詳細と例については、次を参照してください。[用 Func および Action 汎用デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)します。  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>汎用デリゲートのバリアント型パラメーターを宣言します。  
 汎用デリゲートは共変または反変のジェネリック型パラメーター、そのことができますとして参照される場合、*バリアント汎用デリゲート*します。  
  
 宣言するジェネリック型パラメーター汎用デリゲートの共変性を使用して、`out`キーワードです。 共変の型は、メソッド引数の型ではなく、メソッドの戻り値の型としてのみ使用できます。 次のコード例では、共変のジェネリック デリゲートを宣言する方法を示します。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 汎用デリゲートのジェネリック型パラメーターの反変性を宣言するにを使用して、`in`キーワードです。 反変の型は、メソッドの戻り値の型としてではなく、メソッド引数の型としてのみ使用できます。 次のコード例では、反変のジェネリック デリゲートを宣言する方法を示します。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  `ByRef`Visual Basic でのパラメーターは、バリアント型としてマークすることはできません。  
  
 異なる型のパラメーターが、同じデリゲート内での分散とジェネリックの共変性の両方をサポートすることもできます。 これを次の例に示します。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>インスタンス化とバリアント汎用デリゲートの呼び出し  
 インスタンス化し、インスタンス化し、ロケールに依存しないデリゲートの呼び出しと同様、バリアント型のデリゲートを呼び出すことができます。 次の例では、ラムダ式によって、デリゲートがインスタンス化されます。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
### <a name="combining-variant-generic-delegates"></a>バリアント汎用デリゲートを組み合わせる  
 バリアント型のデリゲートを結合する必要があります。 <xref:System.Delegate.Combine%2A>メソッド variant デリゲート変換はサポートされないため、まったく同じ型であるデリゲートが必要です</xref:System.Delegate.Combine%2A>。 これにより、実行時に例外を使用してデリゲートを結合するときに、<xref:System.Delegate.Combine%2A>メソッド (c# および Visual Basic) またはを使用して、 `+` (C# の場合)、次のコード例に示す演算子</xref:System.Delegate.Combine%2A>。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>値と参照型のジェネリック型パラメーターの分散  
 ジェネリック型パラメーターの分散は参照型のみサポートされます。 たとえば、`DVariant(Of Int)`に暗黙的に変換できない`DVariant(Of Object)`または`DVariant(Of Long)`整数が値型であるためです。  
  
 次の例では、その差異でジェネリック型パラメーターはサポートされていません値型です。  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Visual Basic での厳密でないデリゲート変換  
 厳密でないデリゲート変換によりより柔軟にデリゲート型でメソッド署名を照合できます。 たとえば、パラメーターの指定を省略してメソッドをデリゲートに割り当てるときに、関数の戻り値を省略できます。 詳細については、次を参照してください。[厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ジェネリック](https://msdn.microsoft.com/library/ms172192)   
 [Func および Action 汎用デリゲート (Visual Basic) に対する分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
