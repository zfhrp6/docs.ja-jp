---
title: "ジェネリック インターフェイス (Visual Basic) の分散 |Microsoft ドキュメント"
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
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
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
ms.openlocfilehash: c53c27bdb085213046553fc4b08f11336880a7c2
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-generic-interfaces-visual-basic"></a>ジェネリック インターフェイス (Visual Basic) の分散
.NET framework 4 には、いくつかの既存のジェネリック インターフェイスの分散のサポートが導入されました。 分散のサポートにより、これらのインターフェイスを実装するクラスの暗黙的な変換です。 次のインターフェイスは、バリアントになりました。  
  
-   <xref:System.Collections.Generic.IEnumerable%601>(T は共変)</xref:System.Collections.Generic.IEnumerable%601>  
  
-   <xref:System.Collections.Generic.IEnumerator%601>(T は共変)</xref:System.Collections.Generic.IEnumerator%601>  
  
-   <xref:System.Linq.IQueryable%601>(T は共変)</xref:System.Linq.IQueryable%601>  
  
-   <xref:System.Linq.IGrouping%602>(`TKey`と`TElement`は共変のみ)</xref:System.Linq.IGrouping%602>  
  
-   <xref:System.Collections.Generic.IComparer%601>(T は反変)</xref:System.Collections.Generic.IComparer%601>  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601>(T は反変)</xref:System.Collections.Generic.IEqualityComparer%601>  
  
-   <xref:System.IComparable%601>(T は反変)</xref:System.IComparable%601>  
  
 ジェネリックの共変性は、メソッドの戻り値のより強い派生型、インターフェイスのジェネリック型パラメーターによって定義されているよりもを許可します。 ジェネリックの共変性機能を示すためには、次の汎用インターフェイスを検討してください:`IEnumerable(Of Object)`と`IEnumerable(Of String)`です。 `IEnumerable(Of String)`インターフェイスを継承しない、`IEnumerable(Of Object)`インターフェイスです。 ただし、`String`型が継承、`Object`の種類と場合によっては相互にこれらのインターフェイスのオブジェクトを代入することもできます。 これにより、次のコード例を示します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 以前のバージョンの .NET Framework では、このコードによりと Visual Basic でコンパイル エラーが発生`Option Strict On`します。 使用するようになりましたが、`strings`の代わりに`objects`ために、前の例で示すように、<xref:System.Collections.Generic.IEnumerable%601>インターフェイスは、共変</xref:System.Collections.Generic.IEnumerable%601>。  
  
 反変性により、メソッドの引数の型がインターフェイスのジェネリック パラメーターで指定されているよりも弱い派生します。 反変性を示すためには、作成した前提としています、`BaseComparer`クラスのインスタンスを比較する、`BaseClass`クラスです。 `BaseComparer` クラスは、`IEqualityComparer(Of BaseClass)` インターフェイスを実装します。 <xref:System.Collections.Generic.IEqualityComparer%601>インターフェイスは、反変では現在使用すると、`BaseComparer`継承したクラスのインスタンスを比較する、`BaseClass`クラス</xref:System.Collections.Generic.IEqualityComparer%601> これにより、次のコード例を示します。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 例については、次を参照してください。 [(Visual Basic) のジェネリック コレクションに対するインターフェイスを使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)します。  
  
 ジェネリック インターフェイスの分散は参照型のみサポートされます。 値型は、分散をサポートしていません。 たとえば、`IEnumerable(Of Integer)`に暗黙的に変換できない`IEnumerable(Of Object)`整数が値型によって表されるため、します。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 バリアント インターフェイスを実装するクラスは引き続き不変を覚えておいてもできます。 たとえばが<xref:System.Collections.Generic.List%601>共変のインターフェイスを実装する<xref:System.Collections.Generic.IEnumerable%601>、暗黙的に変換することはできません`List(Of Object)`に`List(Of String)`</xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.List%601>。 これは、次のコード例に示します。  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a>関連項目  
 [(Visual Basic) のジェネリック コレクションに対するインターフェイスの分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)   
 [バリアント ジェネリック インターフェイス (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)   
 [ジェネリック インターフェイス](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf)   
 [デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
