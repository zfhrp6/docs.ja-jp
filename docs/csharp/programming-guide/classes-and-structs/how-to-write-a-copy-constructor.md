---
title: "方法 : コピー コンストラクターを記述する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, コピー コンストラクター"
  - "コピー コンストラクター [C#]"
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# 方法 : コピー コンストラクターを記述する (C# プログラミング ガイド)
C\# では、オブジェクトのコピー コンストラクターが提供されていませんが、独自に作成することができます。  
  
## 使用例  
 次の例で、`Person` [クラス](../../../csharp/language-reference/keywords/class.md)は、`Person` のインスタンスを引数として受け取るコピー コンストラクターを定義しています。  引数のプロパティの値は、`Person`の新しいインスタンスのプロパティに割り当てられています。  このコードには、コピーするインスタンスの `Name` プロパティと `Age` プロパティをクラスのインスタンス コンストラクターに渡す代替のコピー コンストラクターが含まれています。  
  
 [!code-cs[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-write-a-copy-cons_1.cs)]  
  
## 参照  
 <xref:System.ICloneable>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [デストラクター](../../../csharp/programming-guide/classes-and-structs/destructors.md)