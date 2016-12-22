---
title: "方法 : クエリで要素のプロパティのサブセットを返す (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "匿名型 [C#], 要素のプロパティのサブセット"
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : クエリで要素のプロパティのサブセットを返す (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

次の条件が両方とも該当する場合、クエリ式で匿名型を使用します。  
  
-   各ソース要素のプロパティの一部のみを返す必要がある。  
  
-   クエリが実行されるメソッドのスコープの外側にクエリ結果を保存する必要がない。  
  
 各ソース要素から 1 つのプロパティまたはフィールドのみを返す必要がある場合、`select` 句でドット演算子を使用するだけでこれを行うことができます。  たとえば、各 `student` の `ID` のみを返すには、次のように `select` 句を記述します。  
  
```  
select student.ID;  
```  
  
## 使用例  
 次の例に、匿名型を使用して、指定した条件に一致する各ソース要素のプロパティのサブセットのみを返す方法を示します。  
  
 [!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 名前が指定されていない場合、匿名型では、そのプロパティのソース要素の名前が使用されることに注意してください。  匿名型のプロパティに新しい名前を指定するには、次のように `select` ステートメントを記述します。  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 前の例でこれを行う場合、`Console.WriteLine` ステートメントも変更する必要があります。  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## コードのコンパイル  
  
-   このコードを実行するには、[!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] で作成した Visual C\# コンソール アプリケーション プロジェクトに、クラスをコピーして貼り付けます。  既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] Version 3.5 を対象としており、System.Core.dll への参照と System.Linq の `using` ディレクティブが含まれます。  これらの要件が 1 つ以上プロジェクトから欠落していても、手動で追加できます。  詳細については、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)