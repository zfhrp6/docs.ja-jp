---
title: "ジェネリック メソッド (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ジェネリック [C#], メソッド"
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
caps.latest.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 27
---
# ジェネリック メソッド (C# プログラミング ガイド)
ジェネリック メソッドは、型パラメーターと共に次のように宣言されるメソッドです。  
  
 [!code-cs[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-methods_1.cs)]  
  
 次のコード例は、型引数として `int` を使用してメソッドを呼び出す方法を示しています。  
  
 [!code-cs[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-methods_2.cs)]  
  
 型引数は省略することもできます。省略された型引数は、コンパイラが推論します。  次に示す `Swap` の呼び出しは、上の呼び出しと同じです。  
  
 [!code-cs[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-methods_3.cs)]  
  
 静的メソッドにもインスタンス メソッドにも同じ型の推定規則が適用されます。  コンパイラは、渡されたメソッド引数に基づいて型パラメーターを推論できます。制約や戻り値のみから型パラメーターを推論することはできません。  そのため型の推定は、パラメーターを持たないメソッドでは無効です。  型の推定は、コンパイル時にコンパイラが、オーバーロードされたメソッド シグネチャを解決しようとする前に行われます。  コンパイラは、同じ名前を持つすべてのジェネリック メソッドに型の推定ロジックを適用します。  オーバーロード解決ステップで、コンパイラは、型の推定が成功したジェネリック メソッドのみを取り込みます。  
  
 ジェネリック クラス内の非ジェネリック メソッドは、クラスレベルの型パラメーターに次のようにアクセスできます。  
  
 [!code-cs[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-methods_4.cs)]  
  
 格納する側のクラスと同じ型パラメーターを受け取るジェネリック メソッドを定義した場合、コンパイラは警告 CS0693 を生成します。これは、メソッドのスコープ内で、内側の `T` に指定された引数が、外側の `T` に指定された引数を隠すためです。  クラスをインスタンス化したときに指定した以外の型引数を使ってジェネリック クラス メソッドを柔軟に呼び出す必要がある場合は、次の例の `GenericList2<T>` に示されているように、メソッドの型パラメーターに別の識別子を指定することを検討してください。  
  
 [!code-cs[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-methods_5.cs)]  
  
 メソッドの型パラメーターでより特殊な演算を実現するには、制約を使用します。  次に示す `SwapIfGreater<T>` という `Swap<T>` のバージョンは、<xref:System.IComparable%601> を実装する型引数でのみ使用できます。  
  
 [!code-cs[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-methods_6.cs)]  
  
 ジェネリック メソッドは、いくつかの型パラメーターでオーバーロードできます。  たとえば、次のメソッドは、同じクラスにすべて置くことができます。  
  
 [!code-cs[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-methods_7.cs)]  
  
## C\# 言語仕様  
 詳細については、「[C\# 言語仕様](../../../csharp/language-reference/language-specification.md)」を参照してください。  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)