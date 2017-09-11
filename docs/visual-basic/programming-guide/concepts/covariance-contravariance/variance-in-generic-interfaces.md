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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c53c27bdb085213046553fc4b08f11336880a7c2
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="efe4d-102">ジェネリック インターフェイス (Visual Basic) の分散</span><span class="sxs-lookup"><span data-stu-id="efe4d-102">Variance in Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="efe4d-103">.NET framework 4 には、いくつかの既存のジェネリック インターフェイスの分散のサポートが導入されました。</span><span class="sxs-lookup"><span data-stu-id="efe4d-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="efe4d-104">分散のサポートにより、これらのインターフェイスを実装するクラスの暗黙的な変換です。</span><span class="sxs-lookup"><span data-stu-id="efe4d-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="efe4d-105">次のインターフェイスは、バリアントになりました。</span><span class="sxs-lookup"><span data-stu-id="efe4d-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="efe4d-106"><xref:System.Collections.Generic.IEnumerable%601>(T は共変)</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="efe4d-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="efe4d-107"><xref:System.Collections.Generic.IEnumerator%601>(T は共変)</xref:System.Collections.Generic.IEnumerator%601></span><span class="sxs-lookup"><span data-stu-id="efe4d-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="efe4d-108"><xref:System.Linq.IQueryable%601>(T は共変)</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="efe4d-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="efe4d-109"><xref:System.Linq.IGrouping%602>(`TKey`と`TElement`は共変のみ)</xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="efe4d-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="efe4d-110"><xref:System.Collections.Generic.IComparer%601>(T は反変)</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="efe4d-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="efe4d-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T は反変)</xref:System.Collections.Generic.IEqualityComparer%601></span><span class="sxs-lookup"><span data-stu-id="efe4d-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="efe4d-112"><xref:System.IComparable%601>(T は反変)</xref:System.IComparable%601></span><span class="sxs-lookup"><span data-stu-id="efe4d-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="efe4d-113">ジェネリックの共変性は、メソッドの戻り値のより強い派生型、インターフェイスのジェネリック型パラメーターによって定義されているよりもを許可します。</span><span class="sxs-lookup"><span data-stu-id="efe4d-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="efe4d-114">ジェネリックの共変性機能を示すためには、次の汎用インターフェイスを検討してください:`IEnumerable(Of Object)`と`IEnumerable(Of String)`です。</span><span class="sxs-lookup"><span data-stu-id="efe4d-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="efe4d-115">`IEnumerable(Of String)`インターフェイスを継承しない、`IEnumerable(Of Object)`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="efe4d-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="efe4d-116">ただし、`String`型が継承、`Object`の種類と場合によっては相互にこれらのインターフェイスのオブジェクトを代入することもできます。</span><span class="sxs-lookup"><span data-stu-id="efe4d-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="efe4d-117">これにより、次のコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="efe4d-117">This is shown in the following code example.</span></span>  
  
<span data-ttu-id="efe4d-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="efe4d-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="efe4d-119">以前のバージョンの .NET Framework では、このコードによりと Visual Basic でコンパイル エラーが発生`Option Strict On`します。</span><span class="sxs-lookup"><span data-stu-id="efe4d-119">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="efe4d-120">使用するようになりましたが、`strings`の代わりに`objects`ために、前の例で示すように、<xref:System.Collections.Generic.IEnumerable%601>インターフェイスは、共変</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="efe4d-120">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="efe4d-121">反変性により、メソッドの引数の型がインターフェイスのジェネリック パラメーターで指定されているよりも弱い派生します。</span><span class="sxs-lookup"><span data-stu-id="efe4d-121">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="efe4d-122">反変性を示すためには、作成した前提としています、`BaseComparer`クラスのインスタンスを比較する、`BaseClass`クラスです。</span><span class="sxs-lookup"><span data-stu-id="efe4d-122">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="efe4d-123">`BaseComparer` クラスは、`IEqualityComparer(Of BaseClass)` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="efe4d-123">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="efe4d-124"><xref:System.Collections.Generic.IEqualityComparer%601>インターフェイスは、反変では現在使用すると、`BaseComparer`継承したクラスのインスタンスを比較する、`BaseClass`クラス</xref:System.Collections.Generic.IEqualityComparer%601></span><span class="sxs-lookup"><span data-stu-id="efe4d-124">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="efe4d-125">これにより、次のコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="efe4d-125">This is shown in the following code example.</span></span>  
  
<span data-ttu-id="efe4d-126"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="efe4d-126"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="efe4d-127">例については、次を参照してください。 [(Visual Basic) のジェネリック コレクションに対するインターフェイスを使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)します。</span><span class="sxs-lookup"><span data-stu-id="efe4d-127">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="efe4d-128">ジェネリック インターフェイスの分散は参照型のみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="efe4d-128">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="efe4d-129">値型は、分散をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="efe4d-129">Value types do not support variance.</span></span> <span data-ttu-id="efe4d-130">たとえば、`IEnumerable(Of Integer)`に暗黙的に変換できない`IEnumerable(Of Object)`整数が値型によって表されるため、します。</span><span class="sxs-lookup"><span data-stu-id="efe4d-130">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>  
  
<span data-ttu-id="efe4d-131"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="efe4d-131"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="efe4d-132">バリアント インターフェイスを実装するクラスは引き続き不変を覚えておいてもできます。</span><span class="sxs-lookup"><span data-stu-id="efe4d-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="efe4d-133">たとえばが<xref:System.Collections.Generic.List%601>共変のインターフェイスを実装する<xref:System.Collections.Generic.IEnumerable%601>、暗黙的に変換することはできません`List(Of Object)`に`List(Of String)`</xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="efe4d-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="efe4d-134">これは、次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="efe4d-134">This is illustrated in the following code example.</span></span>  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a><span data-ttu-id="efe4d-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="efe4d-135">See Also</span></span>  
 <span data-ttu-id="efe4d-136">[(Visual Basic) のジェネリック コレクションに対するインターフェイスの分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md) </span><span class="sxs-lookup"><span data-stu-id="efe4d-136">[Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md) </span></span>  
<span data-ttu-id="efe4d-137"> [バリアント ジェネリック インターフェイス (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="efe4d-137"> [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) </span></span>  
<span data-ttu-id="efe4d-138"> [ジェネリック インターフェイス](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf) </span><span class="sxs-lookup"><span data-stu-id="efe4d-138"> [Generic Interfaces](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf) </span></span>  
<span data-ttu-id="efe4d-139"> [デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="efe4d-139"> [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)</span></span>
