---
title: "標準クエリ演算子の連結 (C#) | Microsoft Docs"
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
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8e9da047fcc224176d028f8caef8b57bc134dc21
ms.lasthandoff: 03/13/2017


---
# <a name="chaining-standard-query-operators-together-c"></a>標準クエリ演算子の連結 (C#)
これは「[チュートリアル: クエリの連結 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)」チュートリアルの最後のトピックです。  
  
 標準クエリ演算子も連結することができます。 たとえば、<xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> 演算子を挿入することができます。また、この演算子はレイジー方式でも機能します。 この演算子によって中間結果が具体化されることはありません。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Linq.Enumerable.Where%2A> メソッドは `ConvertCollectionToUpperCase` を呼び出す前に呼び出されます。 <xref:System.Linq.Enumerable.Where%2A> メソッドは、このチュートリアルの前の例で使用したレイジー メソッド (`ConvertCollectionToUpperCase` と `AppendString`) とほぼ同様に動作しますが、この例では異なる点もあります。  
  
 異なる点とは、この場合の <xref:System.Linq.Enumerable.Where%2A> メソッドではソース コレクションを反復処理し、最初の項目を述語に渡さないことを決定してから、述語に渡す次の項目を取得します。 その後、2 番目の項目を生成します。  
  
 ただし、基本的な考え方は同じです。つまり、中間コレクションは、必要がない限り具体化されません。  
  
 クエリ式が使用されている場合、そのクエリ式は標準クエリ演算子への呼び出しに変換され、同じ原則が適用されます。  
  
 Office Open XML ドキュメントに対してクエリを実行するこのセクションの例はすべて、同じ原則を使用します。 遅延実行およびレイジー評価は、LINQ (および LINQ to XML) を効果的に使用するために理解しておく必要がある基本的概念です。  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            where s.CompareTo("D") >= 0  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: クエリの連結 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
