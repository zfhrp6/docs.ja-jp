---
title: '方法 : クエリで要素のプロパティのサブセットを返す (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: f6ec0067cf993018cf58f397e2ad06939852a952
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>方法 : クエリで要素のプロパティのサブセットを返す (C# プログラミング ガイド)
次の両方の条件に当てはまる場合は、クエリ式に匿名型を使用します。  
  
-   各ソース要素のプロパティの一部のみを返したい。  
  
-   クエリを実行したメソッドのスコープ外のクエリ結果を保存する必要がない。  
  
 各ソース要素の 1 つのプロパティまたはフィールドのみを返す場合は、`select` 句でドット演算子 (.) を使用します。 たとえば、各 `student` の `ID` のみを返すには、次のように `select` 句を記述します。  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>例  
 次に、匿名型を使用して、各ソース要素のプロパティのうち、指定した条件に一致するプロパティのみを返す例を示します。  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 名前を指定しない場合、匿名型にはプロパティのソース要素名が使用されます。 匿名型のプロパティに新しい名前を付けるには、次のように `select` ステートメントを記述します。  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 前の例でこの方法を試すには、`Console.WriteLine` ステートメントも次のように変更する必要があります。  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   このコードを実行するには、クラスをコピーし、Visual Studio で作成した Visual C# コンソール アプリケーション プロジェクトに貼り付けます。 既定で、このプロジェクトは [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] バージョン 3.5 をターゲットにしており、System.Core.dll および System.Linq の `using` ディレクティブの参照が含まれます。 これらの要件のうち 1 つまたは複数を満たしていないプロジェクトの場合は、手動で追加することができます。   
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)
