---
title: "方法: 2 つのリストの差集合を見つける (LINQ) (C#) | Microsoft Docs"
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
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
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
ms.openlocfilehash: 5ce6d6192ca2bf0f2dc98f52d825aa265e94f2a0
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a>方法: 2 つのリストの差集合を見つける (LINQ) (C#)
この例では、LINQ を使用して、2 つの文字列リストを比較し、names2.txt ではなく names1.txt でそれらの行を出力する方法を示します。  
  
### <a name="to-create-the-data-files"></a>データ ファイルを作成するには  
  
1.  「[方法: 文字列コレクションを結合および比較する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)」に示されているように、ソリューション フォルダーに names1.txt と names2.txt をコピーします。  
  
## <a name="example"></a>例  
  
```csharp  
class CompareLists  
{          
    static void Main()  
    {  
        // Create the IEnumerable data sources.  
        string[] names1 = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] names2 = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Create the query. Note that method syntax must be used here.  
        IEnumerable<string> differenceQuery =  
          names1.Except(names2);  
  
        // Execute the query.  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt");  
        foreach (string s in differenceQuery)  
            Console.WriteLine(s);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
     The following lines are in names1.txt but not names2.txt  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
     */  
```  
  
 <xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A>、<xref:System.Linq.Enumerable.Concat%2A> など、C# のいくつかの種類のクエリ操作は、メソッド ベースの構文でのみ表すことができます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll を参照設定し、System.Linq 名前空間と System.IO 名前空間を `using` ディレクティブで指定してください。  
  
## <a name="see-also"></a>関連項目  
 [LINQ と文字列 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
