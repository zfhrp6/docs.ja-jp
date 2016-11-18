---
title: "コレクション内での比較と並べ替え"
description: "コレクション内での比較と並べ替え"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c7b7c005-628d-427a-91ad-af0c3958c00e
translationtype: Human Translation
ms.sourcegitcommit: e07788926a995b41571be276379ad9285747951d
ms.openlocfilehash: bad7fd4e9cda1976a31f287d7c95d81d113a30fa

---

# <a name="comparisons-and-sorts-within-collections"></a>コレクション内での比較と並べ替え

[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) クラスは、削除する要素を検索するか、キーと値のペアの値を返すかに関係なく、コレクションの管理に関連するほぼすべての処理において比較を実行します。

通常、コレクションは等値比較子か順序比較子、またはその両方を使用します。 比較には 2 つのコンストラクターが使用されます。 

## <a name="checking-for-equality"></a>等価性のチェック

`Contains`、`IndexOf`、`LastIndexOf`、`Remove` などのメソッドは、コレクション要素に対して等値比較子を使用します。 コレクションがジェネリックの場合、次のガイドラインに従ってアイテムの等価性が比較されます。

*   T 型で [IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1) ジェネリック インターフェイスが実装されている場合、等値比較子はそのインターフェイスの `Equals` メソッドです。

*   T 型で `IEquatable<T>` が実装されていない場合、`Object.Equals` が使用されます。

また、ディクショナリ コレクションの一部のコンストラクター オーバーロードでは、[IEqualityComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEqualityComparer-1) 実装が受け取られ、これを使用してキーの等価性が比較されます。

## <a name="determining-sort-order"></a>並べ替え順序の決定

`BinarySearch`、`Sort` などのメソッドは、コレクション要素に対して順序比較子を使用します。 コレクションの要素間または要素と指定された値との間で比較を実行できます。 オブジェクトの比較には、既定の比較子と明示的な比較子の概念が適用されます。 

既定の比較子は、比較される 1 つ以上のオブジェクトに依存して `IComparable` インターフェイスを実装します。 リスト コレクションの値として使用されるか、またはディクショナリ コレクションのキーとして使用されるすべてのクラスで、`IComparable` を実装することをお勧めします。 ジェネリック コレクションの場合、等価比較は次の基準に従って決定されます。

*   T 型で [System.IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1) ジェネリック インターフェイスが実装されている場合、既定の比較子はそのインターフェイスの `CompareTo(T)` メソッドです。

*   T 型で非ジェネリックの [System.IComparable](https://docs.microsoft.com/dotnet/core/api/System.IComparable) インターフェイスが実装されている場合、既定の比較子はそのインターフェイスの `CompareTo`(Object) メソッドです。

*   T 型でいずれのインターフェイスも実装されていない場合、既定の比較子は存在せず、比較子または比較デリゲートを明示的に指定する必要があります。

明示的な比較を指定するために、一部のメソッドではパラメーターとして `IComparer` 実装を受け取ります。 たとえば、`List<T>.Sort` メソッドは [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) 実装を受け取ります。 

## <a name="equality-and-sort-example"></a>等価性と並べ替えの例

次のコードは、単純なビジネス オブジェクトでの [IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1) と [IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1) の実装を示しています。 また、オブジェクトがリストに格納され、並べ替えられている場合、`Sort()` メソッドを呼び出すと、結果的に 'Part' 型の既定の比較子と、匿名メソッドを使用して実装された `Sort(Comparison<T>)` メソッドを使用することになります。

C#

```csharp
using System;
using System.Collections.Generic;
// Simple business object. A PartId is used to identify the type of part 
// but the part name can change. 
public class Part : IEquatable<Part> , IComparable<Part>
{
    public string PartName { get; set; }

    public int PartId { get; set; }

    public override string ToString()
    {
        return "ID: " + PartId + "   Name: " + PartName;
    }
    public override bool Equals(object obj)
    {
        if (obj == null) return false;
        Part objAsPart = obj as Part;
        if (objAsPart == null) return false;
        else return Equals(objAsPart);
    }
    public int SortByNameAscending(string name1, string name2)
    {

        return name1.CompareTo(name2);
    }

    // Default comparer for Part type.
    public int CompareTo(Part comparePart)
    {
          // A null value means that this object is greater.
        if (comparePart == null)
            return 1;

        else
            return this.PartId.CompareTo(comparePart.PartId);
    }
    public override int GetHashCode()
    {
        return PartId;
    }
    public bool Equals(Part other)
    {
        if (other == null) return false;
        return (this.PartId.Equals(other.PartId));
    }
    // Should also override == and != operators.

}
public class Example
{
    public static void Main()
    {
        // Create a list of parts.
        List<Part> parts = new List<Part>();

        // Add parts to the list.
        parts.Add(new Part() { PartName = "regular seat", PartId = 1434 });
        parts.Add(new Part() { PartName= "crank arm", PartId = 1234 });
        parts.Add(new Part() { PartName = "shift lever", PartId = 1634 }); ;
        // Name intentionally left null.
        parts.Add(new Part() {  PartId = 1334 });
        parts.Add(new Part() { PartName = "banana seat", PartId = 1444 });
        parts.Add(new Part() { PartName = "cassette", PartId = 1534 });


        // Write out the parts in the list. This will call the overridden 
        // ToString method in the Part class.
        Console.WriteLine("\nBefore sort:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }


        // Call Sort on the list. This will use the 
        // default comparer, which is the Compare method 
        // implemented on Part.
        parts.Sort();


        Console.WriteLine("\nAfter sort by part number:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }

        // This shows calling the Sort(Comparison(T) overload using 
        // an anonymous method for the Comparison delegate. 
        // This method treats null as the lesser of two values.
        parts.Sort(delegate(Part x, Part y)
        {
            if (x.PartName == null && y.PartName == null) return 0;
            else if (x.PartName == null) return -1;
            else if (y.PartName == null) return 1;
            else return x.PartName.CompareTo(y.PartName);
        });

        Console.WriteLine("\nAfter sort by name:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }

        /*

            Before sort:
        ID: 1434   Name: regular seat
        ID: 1234   Name: crank arm
        ID: 1634   Name: shift lever
        ID: 1334   Name:
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette

        After sort by part number:
        ID: 1234   Name: crank arm
        ID: 1334   Name:
        ID: 1434   Name: regular seat
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette
        ID: 1634   Name: shift lever

        After sort by name:
        ID: 1334   Name:
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette
        ID: 1234   Name: crank arm
        ID: 1434   Name: regular seat
        ID: 1634   Name: shift lever

         */

    }
}
```

## <a name="see-also"></a>関連項目

[IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer)

[IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1)

[IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1)

[IComparable](https://docs.microsoft.com/dotnet/core/api/System.IComparable)

[IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1)



<!--HONumber=Nov16_HO3-->


