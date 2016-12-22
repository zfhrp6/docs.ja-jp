---
title: "ジェネリックと配列 (C# プログラミング ガイド) | Microsoft Docs"
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
  - "配列 [C#], ジェネリック"
  - "ジェネリック [C#], 配列"
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ジェネリックと配列 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 2.0 以降では、下限がゼロの 1 次元配列には、<xref:System.Collections.Generic.IList%601> が自動的に実装されます。  これによって、ジェネリック メソッドを作成できるようになり、配列やその他のコレクション型の反復処理を実行するときに同じコードを使用できます。  この技法は、主にコレクションのデータを読み込むときに有効です。  配列で要素の追加または削除を行うときに <xref:System.Collections.Generic.IList%601> インターフェイスは使用できません。  このコンテキストの配列上で <xref:System.Collections.Generic.IList%601.RemoveAt%2A> などの <xref:System.Collections.Generic.IList%601> メソッドを呼び出そうとすると、例外がスローされます。  
  
 次のコード例では、<xref:System.Collections.Generic.IList%601> 入力パラメーターを使用する単一のジェネリック メソッドで、リストと配列 \(この場合は整数の配列\) の両方に対して反復処理を実行する方法を示します。  
  
 [!code-cs[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリック](../../../visual-basic/reference/command-line-compiler/index.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [ジェネリック](../Topic/Generics%20in%20the%20.NET%20Framework.md)