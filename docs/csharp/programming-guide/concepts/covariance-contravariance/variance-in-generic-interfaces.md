---
title: "ジェネリック インターフェイスの分散 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4c4f3ab00b4de2a6f38858dd5f332db3d47eb85b
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-generic-interfaces-c"></a>ジェネリック インターフェイスの分散 (C#)
.NET Framework 4 では、既存のいくつかのジェネリック インターフェイスに対して、分散のサポートが導入されています。 分散のサポートにより、これらのインターフェイスを実装するクラスの暗黙的な変換が可能になりました。 次のインターフェイスは、新たにバリアントになりました。  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T は共変)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T は共変)  
  
-   <xref:System.Linq.IQueryable%601> (T は共変)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` と `TElement` は共変)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T は反変)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T は反変)  
  
-   <xref:System.IComparable%601> (T は反変)  
  
 共変性により、メソッドの戻り値の型の派生を、インターフェイスのジェネリック型パラメーターで定義されている型よりも強くすることができます。 ここでは、共変性機能について説明するために、`IEnumerable<Object>` および `IEnumerable<String>` というジェネリック インターフェイスについて考えます。 `IEnumerable<String>` インターフェイスは、`IEnumerable<Object>` インターフェイスを継承しません。 ただし、`String` 型は `Object` 型を継承します。場合によっては、これらのインターフェイスのオブジェクトを、相互に割り当てる必要が生じることもあるでしょう。 これを次のコード例に示します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 以前のバージョンの .NET Framework では、`Option Strict On` を使用した C# でこのコードを実行すると、コンパイル エラーが発生しましたが、 今後は、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスが共変になったので、上記の例のように、`objects` の代わりに `strings` を使用できるようになりました。  
  
 反変性により、メソッドの引数の型の派生を、インターフェイスのジェネリック パラメーターで指定されている型よりも弱くすることができます。 ここでは、反変性について説明するために、`BaseClass` クラスのインスタンスを比較するための `BaseComparer` クラスを作成した場合について考えます。 `BaseComparer` クラスは、`IEqualityComparer<BaseClass>` インターフェイスを実装します。 <xref:System.Collections.Generic.IEqualityComparer%601> インターフェイスが反変になったので、`BaseComparer` を使用して、`BaseClass` クラスを継承するクラスのインスタンスを比較することができます。 これを次のコード例に示します。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 詳しくは、「[ジェネリック コレクションに対するインターフェイスでの分散の使用 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)」をご覧ください。  
  
 ジェネリック インターフェイスでの分散がサポートされるのは参照型だけです。 値型は変性をサポートしていません。 たとえば、整数は値型によって表されるため、`IEnumerable<int>` を暗黙的に `IEnumerable<object>` に変換することはできません。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 また、バリアント インターフェイスを実装するクラスは、現在でもインバリアントであることを忘れないようにしてください。 たとえば、<xref:System.Collections.Generic.List%601> は共変のインターフェイス <xref:System.Collections.Generic.IEnumerable%601> を実装しますが、`List<Object>` を暗黙的に `List<String>` に変換することはできません。 これを次のコード例に示します。  
  
```cs  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a>関連項目  
 [ジェネリック コレクションに対するインターフェイスでの分散の使用 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)   
 [バリアント ジェネリック インターフェイスの作成 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)   
 [ジェネリック インターフェイス](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf)   
 [デリゲートの分散 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
