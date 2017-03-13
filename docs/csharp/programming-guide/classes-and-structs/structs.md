---
title: "構造体 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, 構造体"
  - "構造体 [C#]"
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# 構造体 (C# プログラミング ガイド)
構造体は、次のように [struct](../../../csharp/language-reference/keywords/struct.md) キーワードで定義します。  
  
 [!code-cs[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 構造体は、構文上ではクラスとほとんど変わりませんが、次のようにクラスよりも制限されます。  
  
-   構造体宣言内では、const または static と宣言されているフィールド以外は初期化できません。  
  
-   構造体では、既定のコンストラクター \(パラメーターなしのコンストラクター\) やデストラクターを宣言できません。  
  
-   構造体は、代入時にコピーされます。  構造体を新しい変数に代入すると、すべてのデータがコピーされ、新しいコピーを変更しても、元のコピーのデータは変更されません。  この点は、Dictionary\<string, myStruct\> などの値の型のコレクションを使用する際に重要です。  
  
-   構造体は値型ですが、クラスは参照型です。  
  
-   クラスとは異なり、構造体は `new` 演算子を使用せずにインスタンス化できます。  
  
-   構造体は、パラメーターのあるコンストラクターを宣言できます。  
  
-   構造体は、他の構造体やクラスから継承できず、基本クラスになれません。  すべての構造体が `System.ValueType` を直接継承し、System.ValueType は `System.Object` を継承します。  
  
-   構造体では、インターフェイスを実装できます。  
  
-   構造体は null 許容型として使用でき、null 値を割り当てることができます。  
  
## 関連項目  
 詳細情報  
  
-   [構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [方法 : メソッドに構造体を渡すこととクラス参照を渡すことの違いを理解する](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [方法 : 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [More About Variables](http://go.microsoft.com/fwlink/?LinkId=221230) 入力 [Beginning Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [クラス](../../../csharp/programming-guide/classes-and-structs/classes.md)