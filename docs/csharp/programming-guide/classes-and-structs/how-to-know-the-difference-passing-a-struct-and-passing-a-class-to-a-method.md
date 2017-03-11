---
title: "方法 : メソッドに構造体を渡すこととクラス参照を渡すことの違いを理解する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "メソッド [C#], 渡す (クラスと構造体を)"
  - "渡す (パラメーターを) [C#], 構造体とクラス"
  - "構造体 [C#], 渡す (メソッド パラメーターとして)"
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
caps.latest.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 25
---
# 方法 : メソッドに構造体を渡すこととクラス参照を渡すことの違いを理解する (C# プログラミング ガイド)
メソッドに [構造体](../../../csharp/language-reference/keywords/struct.md) を渡すことがメソッドに [クラス](../../../csharp/language-reference/keywords/class.md) のインスタンスを渡す場合の違いを次の例に示します。  例では、引数の両方で、値との両方のメソッド （構造体とクラス インスタンス）変更する引数の 1 つがのフィールドの値渡しされます。  ただし、 2 回のメソッドは、クラスのインスタンスを渡すと、渡されたを渡すと、渡された場合に構造体が異なるため同じではありません。  
  
 構造体が [値型](../../../csharp/language-reference/keywords/value-types.md)であるため、メソッドへの [値を構造体を渡します。](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) 構造体、メソッドの引数のコピーを受信し、操作するとき。  したがって、メソッドに呼び出し元のメソッドに、元の構造体へのアクセスがなく、何かの要素を変更できません。  メソッドは一つしか変更できます。  
  
 クラス インスタンスは [参照型](../../../csharp/language-reference/keywords/reference-types.md)値型ではありません。  メソッドへの [参照型は値渡しされます](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) メソッドが、クラス インスタンスへの参照のコピーを受信したとき。  つまり、メソッドはインスタンス インスタンスのコピーではなく、のアドレスのコピーを受信します。  呼び出し元のメソッドのクラス インスタンスにアドレスがありますが、呼び出されたメソッドのパラメーターにアドレスのコピーがあり、アドレスは両方とも、同じオブジェクトを示します。  パラメーターがアドレスのコピーであるため、呼び出されたメソッドは、呼び出し元のメソッド インスタンスのアドレスを変更できません。  ただし、呼び出されたメソッドは元のアドレスとコピーの両方が参照するクラス メンバーにアクセスするには、アドレスを使用できます。  呼び出されたメソッドがクラス メンバーを変更して、呼び出し元のメソッドの元のクラス インスタンスも変更されます。  
  
 次の例の出力は違いを示しています。  クラス インスタンスの `willIChange` フィールドの値は、メソッド `ClassTaker` に呼び出しによってクラス インスタンスの指定したフィールドを検索するには、メソッドがパラメーターのアドレスを使用するので変更されます。  呼び出し元のメソッドの構造体の `willIChange` フィールドは、メソッド `StructTaker` 、アドレスのコピーを呼び出し、引数の値が構造体自体のコピーであるため変更されません。  `StructTaker` は コピーを変更し、 `StructTaker` への呼び出しが完了すると、コピーは失われます。  
  
## 使用例  
 [!code-cs[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-know-the-differen_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラス](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)