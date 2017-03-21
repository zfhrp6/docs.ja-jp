---
title: "ジェネリックの共変性と反変性 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
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
ms.openlocfilehash: b785e298c5ba38a8e3d8cc549b2dcf2df1ef6bd8
ms.lasthandoff: 03/13/2017

---
# <a name="covariance-and-contravariance-visual-basic"></a>ジェネリックの共変性と反変性 (Visual Basic)
Visual basic での共変性と反変性には、配列型、デリゲートの型およびジェネリック型引数の暗黙の参照変換が有効にします。 ジェネリックの共変性は代入互換性を保持し、反変性では、それを反転させます。  
  
 次のコードでは、代入互換性、共変性と反変性の違いについて説明します。  
  
```vb  
' Assignment compatibility.   
Dim str As String = "test"  
' An object of a more derived type is assigned to an object of a less derived type.   
Dim obj As Object = str  
  
' Covariance.   
Dim strings As IEnumerable(Of String) = New List(Of String)()  
' An object that is instantiated with a more derived type argument   
' is assigned to an object instantiated with a less derived type argument.   
' Assignment compatibility is preserved.   
Dim objects As IEnumerable(Of Object) = strings  
  
' Contravariance.             
' Assume that there is the following method in the class:   
' Shared Sub SetObject(ByVal o As Object)  
' End Sub  
Dim actObject As Action(Of Object) = AddressOf SetObject  
  
' An object that is instantiated with a less derived type argument   
' is assigned to an object instantiated with a more derived type argument.   
' Assignment compatibility is reversed.   
Dim actString As Action(Of String) = actObject  
```  
  
 配列の共変性より強い派生型の配列の弱い派生型の配列への暗黙的な変換できます。 この操作がタイプ セーフである、次のコード例に示すようにします。  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 メソッドのグループの共変性と反変性のサポートは、デリゲート型でメソッド署名を照合できます。 これにより、一致するシグネチャも強い派生型 (共変性) またはを返すメソッドのあるメソッドだけでなくデリゲートを割り当てることは、デリゲート型で指定されているよりも弱い派生型 (反変性) があるパラメーターを受け入れます。 詳細については、次を参照してください。[デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)と[デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)します。  
  
 次のコード例では、ジェネリックの共変性と反変性は、メソッドのグループのサポートを示します。  
  
```vb  
Shared Function GetObject() As Object  
    Return Nothing  
End Function  
  
Shared Sub SetObject(ByVal obj As Object)  
End Sub  
  
Shared Function GetString() As String  
    Return ""  
End Function  
  
Shared Sub SetString(ByVal str As String)  
  
End Sub  
  
Shared Sub Test()  
    ' Covariance. A delegate specifies a return type as object,  
    ' but you can assign a method that returns a string.  
    Dim del As Func(Of Object) = AddressOf GetString  
  
    ' Contravariance. A delegate specifies a parameter type as string,  
    ' but you can assign a method that takes an object.  
    Dim del2 As Action(Of String) = AddressOf SetObject  
End Sub  
```  
  
 .NET Framework 4 またはそれ以降の Visual Basic では、ジェネリック インターフェイスとデリゲートの共変性と反変性をサポートし、ジェネリック型パラメーターの暗黙の変換では、します。 詳細については、次を参照してください。[ジェネリック インターフェイス (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)と[デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)します。  
  
 次のコード例では、ジェネリック インターフェイスの暗黙の参照変換を示しています。  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 ジェネリック インターフェイスまたはデリゲートを呼び出す*バリアント*そのジェネリック パラメーターが共変で宣言されている場合または反変です。 Visual Basic では、独自のバリアント型のインターフェイスとデリゲートを作成することができます。 詳細については、次を参照してください。[を作成するバリアント ジェネリック インターフェイス (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)と[デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)します。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[ジェネリック インターフェイス (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|ジェネリック インターフェイスでの共変性と反変性について説明し、.NET Framework でのバリアント ジェネリック インターフェイスの一覧を示します。|  
|[バリアント ジェネリック インターフェイス (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|カスタムのバリアント インターフェイスを作成する方法を示します。|  
|[(Visual Basic) のジェネリック コレクションに対するインターフェイスの分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|共変性と反変性をサポートする方法を示しています、<xref:System.Collections.Generic.IEnumerable%601>と<xref:System.IComparable%601>インターフェイスを使用して、コードを再利用できます</xref:System.IComparable%601></xref:System.Collections.Generic.IEnumerable%601>。|  
|[デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|ジェネリックの共変性と反変性と非汎用デリゲートについて説明し、.NET Framework のバリアント汎用デリゲートの一覧を提供します。|  
|[デリゲート (Visual Basic) の分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|デリゲート型でメソッドのシグネチャを一致するように、非汎用デリゲートの共変性と反変性のサポートを使用する方法を示します。|  
|[Func および Action 汎用デリゲート (Visual Basic) に対する分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|共変性と反変性をサポートする方法を示しています、`Func`と`Action`デリゲートを使用して、コードを再利用できます。|
