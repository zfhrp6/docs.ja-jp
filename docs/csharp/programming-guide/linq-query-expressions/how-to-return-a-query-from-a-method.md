---
title: "方法 : メソッドからクエリを返す (C# プログラミング ガイド) | Microsoft Docs"
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
  - "メソッドからクエリを返す [C#]"
  - "クエリ [C# での LINQ], メソッドからクエリを返す"
  - "クエリ式 [C# での LINQ], メソッドからクエリを返す"
ms.assetid: 9d6f20a7-f085-44cf-9df3-71948255ec68
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : メソッドからクエリを返す (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

この例では、メソッドからクエリを戻り値および `out` パラメーターとして返す方法を示します。  
  
 クエリの型は、<xref:System.Collections.IEnumerable> か <xref:System.Collections.Generic.IEnumerable%601>、または <xref:System.Linq.IQueryable%601> のような派生型である必要があります。  したがって、クエリを返すメソッドの戻り値または `out` パラメーターも同じ型である必要があります。  メソッドがクエリを具象型の <xref:System.Collections.Generic.List%601> または <xref:System.Array> に実体化する場合は、クエリ自体ではなくクエリ結果を返すと見なされます。  メソッドから返されたクエリ変数は、引き続き構成または変更できます。  
  
## 使用例  
 次の例では、最初のメソッドはクエリを戻り値として返し、2 番目のメソッドはクエリを `out` パラメーターとして返します。  どちらの場合も返されるのはクエリであり、クエリ結果ではないことに注意してください。  
  
 [!code-cs[csProgGuideLINQ#80](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-a-query-from-a-method_1.cs)]  
  
## コードのコンパイル  
  
-   .NET Framework Version 3.5 以降を対象とする [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] プロジェクトを作成します。  既定では、プロジェクトには、System.Core.dll への参照と、System.Linq 名前空間に対する `using` ディレクティブが含まれます。  
  
-   クラスを例のコードで置き換えます。  
  
-   F5 キーを押して、プログラムをコンパイルおよび実行します。  
  
-   任意のキーを押して、コンソール ウィンドウを終了します。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)