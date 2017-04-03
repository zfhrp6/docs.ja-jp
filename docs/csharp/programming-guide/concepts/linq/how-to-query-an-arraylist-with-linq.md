---
title: "方法: LINQ を使用して ArrayList をクエリする (C#) | Microsoft Docs"
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
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
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
ms.openlocfilehash: 09489e2dabd34da0446a623e91cd85de35c3c70b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>方法: LINQ を使用して ArrayList をクエリする (C#)
LINQ を使用して <xref:System.Collections.ArrayList> などの非ジェネリックの <xref:System.Collections.IEnumerable> コレクションをクエリする場合、範囲変数の型を明示的に宣言して、オブジェクトの特定の型をコレクションに反映させる必要があります。 たとえば、`Student` オブジェクトの <xref:System.Collections.ArrayList> がある場合、[from 句](../../../../csharp/language-reference/keywords/from-clause.md)は次のようになります。  
  
```  
  
var query = from Student s in arrList  
...  
  
```  
  
 範囲変数の型を指定することで、<xref:System.Collections.ArrayList> 内の各項目を `Student` にキャストします。  
  
 明示的に型指定された範囲変数をクエリ式で使用すると、<xref:System.Linq.Enumerable.Cast%2A> メソッドを呼び出した場合と同じ結果を得ることができます。 指定されたキャストを実行できない場合、<xref:System.Linq.Enumerable.Cast%2A> は例外をスローします。 <xref:System.Linq.Enumerable.Cast%2A> と <xref:System.Linq.Enumerable.OfType%2A> は、非ジェネリックの <xref:System.Collections.IEnumerable> 型で実行できる標準クエリ演算子メソッドです。 詳細については、「[LINQ クエリ操作での型の関係](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」を参照してください。  
  
## <a name="example"></a>例  
 <xref:System.Collections.ArrayList> に対する単純なクエリの例を次に示します。 この例では、コードが <xref:System.Collections.ArrayList.Add%2A> メソッドを呼び出すときにオブジェクト初期化子を使用していますが、これは必須ではありません。  
  
```csharp  
using System;  
using System.Collections;  
using System.Linq;  
  
namespace NonGenericLINQ  
{  
    public class Student  
    {  
        public string FirstName { get; set; }  
        public string LastName { get; set; }  
        public int[] Scores { get; set; }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ArrayList arrList = new ArrayList();  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Svetlana", LastName = "Omelchenko", Scores = new int[] { 98, 92, 81, 60 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Claire", LastName = "O’Donnell", Scores = new int[] { 75, 84, 91, 39 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Sven", LastName = "Mortensen", Scores = new int[] { 88, 94, 65, 91 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Cesar", LastName = "Garcia", Scores = new int[] { 97, 89, 85, 82 }  
                    });  
  
            var query = from Student student in arrList  
                        where student.Scores[0] > 95  
                        select student;  
  
            foreach (Student s in query)  
                Console.WriteLine(s.LastName + ": " + s.Scores[0]);  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
}  
/* Output:   
    Omelchenko: 98  
    Garcia: 97  
*/  
```  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
