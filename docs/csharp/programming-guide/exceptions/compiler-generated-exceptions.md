---
title: "コンパイラにより生成された例外 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: 13
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4015551ac983610afc8bf1f08e73a33c1ac338ff
ms.lasthandoff: 03/13/2017

---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>コンパイラにより生成された例外 (C# プログラミング ガイド)
一部の例外は、基本操作が失敗した場合に .NET Framework の共通言語ランタイム (CLR) によって自動的にスローされます。 次の表には、これらの例外とそのエラー条件が一覧で示されています。  
  
|例外|説明|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|算術演算中に発生する例外 (<xref:System.DivideByZeroException> や <xref:System.OverflowException> など) の基底クラス。|  
|<xref:System.ArrayTypeMismatchException>|要素の実際の型が配列の実際の型に適合していないことが原因で、指定された要素を配列に格納できない場合にスローされます。|  
|<xref:System.DivideByZeroException>|整数値のゼロ除算が試行されたときにスローされます。|  
|<xref:System.IndexOutOfRangeException>|インデックスがゼロよりも小さい場合またはインデックスが配列の境界外にある場合に、配列のインデックス作成が試行されたときにスローされます。|  
|<xref:System.InvalidCastException>|基本データ型からインターフェイスまたは派生型への明示的な変換が実行時に失敗したときにスローされます。|  
|<xref:System.NullReferenceException>|値が [null](../../../csharp/language-reference/keywords/null.md) であるオブジェクトを参照しようとした場合にスローされます。|  
|<xref:System.OutOfMemoryException>|[new](../../../csharp/language-reference/keywords/new-operator.md) 演算子を使用したメモリの割り当てに失敗するとスローされます。 これは、共通言語ランタイムで使用できるメモリが足りなくなったことを示します。|  
|<xref:System.OverflowException>|`checked` コンテキストで算術演算がオーバーフローしたときにスローされます。|  
|<xref:System.StackOverflowException>|保留中のメソッド呼び出しが多すぎることが原因で実行スタックが不足したときにスローされます。通常は、非常に深い再帰か無限再帰があることを示します。|  
|<xref:System.TypeInitializationException>|静的コンストラクターが例外をスローし、その例外をキャッチするための対応する `catch` 句がない場合にスローされます。|  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [例外と例外処理](../../../csharp/programming-guide/exceptions/index.md)   
 [例外処理](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
