---
title: "方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "クラス [C#], 演算子のオーバーロード"
  - "複素数 [C#]"
  - "演算子のオーバーロード [C#], 複素数"
  - "演算子のオーバーロード [C#], 使用 (クラスを作成するために)"
  - "演算子 [C#], オーバーロード (複素数クラスを作成するために)"
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド)
この例では、演算子のオーバーロードを使用して、複素数の加算を定義する複素数クラス `Complex` を作成する方法を示します。  プログラムは、`ToString` メソッドのオーバーライドを使用して、数値の虚数部と実数部、および加算結果を表示します。  
  
## 使用例  
 [!code-cs[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)   
 [Why are overloaded operators always static in C\#? \(オーバーロードされた演算子が C\# で常に静的になる理由\)](http://go.microsoft.com/fwlink/?LinkId=112383)