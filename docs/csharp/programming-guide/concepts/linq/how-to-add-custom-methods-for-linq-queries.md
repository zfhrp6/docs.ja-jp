---
title: "方法: LINQ クエリのカスタム メソッドを追加する (C#) | Microsoft Docs"
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
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
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
ms.openlocfilehash: 7843620518dd7965724f0108a8fa008c95bd4793
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>方法: LINQ クエリのカスタム メソッドを追加する (C#)
LINQ クエリに使用できる一連のメソッドは、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスに拡張メソッドを追加することで拡張できます。 たとえば一連の値から単一の値を求めるために、平均値や最大値を求める標準的な演算に加えて、独自の集計メソッドを作成することができます。 また、一連の値を受け取って別の一連の値を返す特定のデータ変換やカスタム フィルターの働きを持ったメソッドを作成することもできます。 そのようなメソッドの例としては、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A>、<xref:System.Linq.Enumerable.Reverse%2A> があります。  
  
 <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを拡張すると、列挙可能なコレクションにカスタム メソッドを適用することができます。 詳細については、「[拡張メソッド](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。  
  
## <a name="adding-an-aggregate-method"></a>集計メソッドの追加  
 集計メソッドは、一連の値から単一の値を計算するメソッドです。 LINQ には、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Max%2A> など、いくつかの集計メソッドが用意されています。 <xref:System.Collections.Generic.IEnumerable%601> インターフェイスに拡張メソッドを追加することで、独自の集計メソッドを作成できます。  
  
 次のコード例は、`double` 型の一連の数値から中央値を求める `Median` という拡張メソッドの作成方法を示しています。  
  
```cs  
public static class LINQExtension  
{  
    public static double Median(this IEnumerable<double> source)  
    {  
        if (source.Count() == 0)  
        {  
            throw new InvalidOperationException("Cannot compute median for an empty set.");  
        }  
  
        var sortedList = from number in source  
                         orderby number  
                         select number;  
  
        int itemIndex = (int)sortedList.Count() / 2;  
  
        if (sortedList.Count() % 2 == 0)  
        {  
            // Even number of items.  
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;  
        }  
        else  
        {  
            // Odd number of items.  
            return sortedList.ElementAt(itemIndex);  
        }  
    }  
}  
```  
  
 この拡張メソッドは、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスにある他の集計メソッドを呼び出すときと同じように、列挙可能な任意のコレクションに対して呼び出すことができます。  
  
 `double` 型の配列に対して `Median` メソッドを使用する方法を次のコード例に示します。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>さまざまな型を受け取るために集計メソッドをオーバーロードする  
 集計メソッドでさまざまな型を受け取るように、集計メソッドをオーバーロードすることができます。 その標準的な方法として、型ごとにオーバーロードを作成します。 または、ジェネリック型を受け取り、デリゲートを使って特定の型に変換するオーバーロードを作成する方法もあります。 その両方の方法を組み合わせることもできます。  
  
#### <a name="to-create-an-overload-for-each-type"></a>型ごとにオーバーロードを作成するには  
 サポート予定の型ごとに固有のオーバーロードを作成できます。 次のコード例では、`integer` 型の `Median` メソッドのオーバーロードを示します。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 これで、次のコードに示すように、`integer` 型と `double` 型の両方に対して、`Median` のオーバーロードを呼び出すことができるようになりました。  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
#### <a name="to-create-a-generic-overload"></a>ジェネリック オーバーロードを作成するには  
 一連のジェネリック オブジェクトを受け取るオーバーロードを作成することもできます。 このオーバーロードは、デリゲートをパラメーターとして受け取り、ジェネリック型の一連のオブジェクトを特定の型に変換します。  
  
 次のコードは、<xref:System.Func%602> デリゲートをパラメーターとして受け取る `Median` メソッドのオーバーロードを示しています。 このデリゲートは、ジェネリック型 T のオブジェクトを受け取り、`double` 型のオブジェクトを返します。  
  
```cs  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 これで、任意の型の一連のオブジェクトに対して `Median` メソッドを呼び出すことができます。 型に固有のメソッド オーバーロードがない場合は、デリゲート パラメーターを渡す必要があります。 この目的で、C# ではラムダ式を使用できます。 また、Visual Basic に限り、メソッド呼び出しの代わりに `Aggregate` 句または `Group By` 句を使用した場合、その句のスコープにある任意の値または式を渡すことができます。  
  
 次のコード例では、整数の配列と文字列の配列に対して `Median` メソッドを呼び出す方法を示します。 文字列の場合は、配列に格納されている文字列の長さの中央値が計算されます。 この例は、それぞれのケースについて、`Median` メソッドに <xref:System.Func%602> デリゲート パラメーターを渡す方法を示しています。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
## <a name="adding-a-method-that-returns-a-collection"></a>コレクションを返すメソッドを追加する  
 <xref:System.Collections.Generic.IEnumerable%601> インターフェイスは、一連の値を返すカスタム クエリ メソッドを追加することで拡張できます。 この場合、メソッドから <xref:System.Collections.Generic.IEnumerable%601> 型のコレクションを返す必要があります。 このようなメソッドを使用すると、一連の値にフィルターまたはデータ変換を適用することができます。  
  
 次の例では、コレクション内の最初の要素から 1 つおきに要素を返す `AlternateElements` という名前の拡張メソッドを作成する方法を示しています。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 この拡張メソッドは、次のコードに示すとおり、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスにある他のメソッドを呼び出すときと同じように、列挙可能な任意のコレクションに対して呼び出すことができます。  
  
```cs  
string[] strings = { "a", "b", "c", "d", "e" };  
  
var query = strings.AlternateElements();  
  
foreach (var element in query)  
{  
    Console.WriteLine(element);  
}  
/*  
 This code produces the following output:  
  
 a  
 c  
 e  
*/  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic.IEnumerable%601>   
 [拡張メソッド](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
