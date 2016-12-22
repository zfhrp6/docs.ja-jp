---
title: "コンパイラにより生成された例外 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "例外 [C#], コンパイラにより生成された"
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラにより生成された例外 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

例外には、基本操作が失敗すると、.NET Framework の共通言語ランタイム \(CLR: Common Language Runtime\) により自動的にスローされるものがあります。  次の表は、例外とそのエラー条件の一覧です。  
  
|例外|Description|  
|--------|-----------------|  
|<xref:System.ArithmeticException>|<xref:System.DivideByZeroException> や <xref:System.OverflowException> など、算術演算中に発生する例外の基本クラスです。|  
|<xref:System.ArrayTypeMismatchException>|要素の実際の型が、配列の実際の型と互換性がないために、要素を配列に格納できなかった場合にスローされます。|  
|<xref:System.DivideByZeroException>|整数値を 0 で除算しようとしたときにスローされます。|  
|<xref:System.IndexOutOfRangeException>|0 未満のインデックス、または配列の範囲外のインデックスを使用して、配列のインデックス付けをしようとしたときにスローされます。|  
|<xref:System.InvalidCastException>|基本型からインターフェイスまたは派生型への明示的変換が、実行時に失敗した場合にスローされます。|  
|<xref:System.NullReferenceException>|値が [null](../../../csharp/language-reference/keywords/null.md) のオブジェクトを参照しようとするとスローされます。|  
|<xref:System.OutOfMemoryException>|[new 演算子](../../../visual-basic/language-reference/operators/new-operator.md)を使用してメモリを割り当てようとして失敗した場合にスローされます。  共通言語ランタイムの使用可能なメモリ容量が不足しています。|  
|<xref:System.OverflowException>|`checked` コンテキストで算術演算がオーバーフローしたときにスローされます。|  
|<xref:System.StackOverflowException>|保留状態のメソッド呼び出しが多すぎて、実行スタックに空きがなくなったときにスローされます。一般的には、再帰が深いか、または無限再帰の場合に発生します。|  
|<xref:System.TypeInitializationException>|静的コンストラクターが例外をスローし、その例外をキャッチする、対応する `catch` 句が存在しない場合にスローされます。|  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [例外と例外処理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [例外処理](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)