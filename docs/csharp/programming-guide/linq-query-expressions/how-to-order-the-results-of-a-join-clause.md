---
title: "方法 : join 句の結果の順序を指定する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "join 句 [C#]"
  - "結合 [C#], 順序付け (結果を)"
  - "クエリ [C# での LINQ], 結合"
  - "クエリ式 [C# での LINQ], 結合"
ms.assetid: 83f36f16-2ba3-453f-8b9f-7d02b415610e
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : join 句の結果の順序を指定する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

この例は、結合操作の結果の順序を指定する方法を示しています。  順序付けは結合後に行われます。  結合の前に 1 つ以上のソース シーケンスを指定した `orderby` 句を使用することもできますが、一般にこの方法は推奨されません。  一部の [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] プロバイダーは、結合後にその順序付けを維持しない可能性があります。  
  
## 使用例  
 このクエリは、グループ結合を作成し、次にまだスコープ内にあるカテゴリ要素に基づいて各グループを並べ替えます。  匿名型初期化子の内部では、結果のシーケンス内の一致するすべての要素がサブクエリによって順序付けられます。  
  
 [!code-cs[csProgGuideLINQ#81](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-order-the-results-of-a-join-clause_1.cs)]  
  
## コードのコンパイル  
  
-   .NET Framework Version 3.5 を対象とする [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] プロジェクトを作成します。  既定では、プロジェクトには、System.Core.dll への参照と、System.Linq 名前空間に対する `using` ディレクティブが含まれます。  
  
-   コードをプロジェクト内にコピーします。  
  
-   F5 キーを押して、プログラムをコンパイルおよび実行します。  
  
-   任意のキーを押して、コンソール ウィンドウを終了します。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [orderby 句](../../../csharp/language-reference/keywords/orderby-clause.md)   
 [join 句](../../../csharp/language-reference/keywords/join-clause.md)   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)