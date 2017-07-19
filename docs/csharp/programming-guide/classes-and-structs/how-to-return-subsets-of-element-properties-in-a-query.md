---
title: "方法 : クエリで要素のプロパティのサブセットを返す (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 99768c4b486dd6e8a25af22ab187c673c548ece9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/03/2017

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
  
 [!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 名前を指定しない場合、匿名型にはプロパティのソース要素名が使用されます。 匿名型のプロパティに新しい名前を付けるには、次のように `select` ステートメントを記述します。  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 前の例でこの方法を試すには、`Console.WriteLine` ステートメントも次のように変更する必要があります。  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   このコードを実行するには、クラスをコピーし、[!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] で作成した Visual C# コンソール アプリケーション プロジェクトに貼り付けます。 既定で、このプロジェクトは [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] バージョン 3.5 をターゲットにしており、System.Core.dll および System.Linq の `using` ディレクティブの参照が含まれます。 これらの要件のうち 1 つまたは複数を満たしていないプロジェクトの場合は、手動で追加することができます。   
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)
