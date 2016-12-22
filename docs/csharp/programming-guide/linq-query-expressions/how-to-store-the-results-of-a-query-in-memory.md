---
title: "方法 : クエリの結果をメモリに格納する (C# プログラミング ガイド) | Microsoft Docs"
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
  - "LINQ クエリの結果ストレージ [C# での LINQ]"
  - "クエリ式 [C# での LINQ], 結果の格納"
ms.assetid: 7271597f-3523-4f7b-b088-1eeffe913b2d
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : クエリの結果をメモリに格納する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

基本的に、クエリは、データの取得方法と編成方法を指示するための一連の命令です。  クエリを実行するには、<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドを呼び出す必要があります。  この呼び出しは、`foreach` ループを使用して要素を反復処理する際に行います。  クエリを評価し、`foreach` のループを実行せずに結果を格納するには、クエリ変数で次のメソッドを 1 回を呼び出します:  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 クエリ結果を格納するときは、次の例に示すように、返されたコレクション オブジェクトを新しい変数に代入することをお勧めします。  
  
## 使用例  
 [!code-cs[csProgGuideLINQ#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  
## コードのコンパイル  
  
-   .NET Framework Version 3.5 を対象とする [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] プロジェクトを作成します。  既定では、プロジェクトには、System.Core.dll への参照と、System.Linq 名前空間に対する `using` ディレクティブが含まれます。  
  
-   コードをプロジェクト内にコピーします。  
  
-   F5 キーを押して、プログラムをコンパイルおよび実行します。  
  
-   任意のキーを押して、コンソール ウィンドウを終了します。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)