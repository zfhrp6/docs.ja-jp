---
title: "参照型のパラメーターの引き渡し (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "メソッド パラメーター [C#], 参照型"
  - "パラメーター [C#], リファレンス"
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 参照型のパラメーターの引き渡し (C# プログラミング ガイド)
[参照型](../../../csharp/language-reference/keywords/reference-types.md)の変数には、データが直接格納されず、データへの参照が格納されます。  参照型のパラメーターを値で渡すときには、クラス メンバーの値など、参照によって指されるデータを変更できます。  ただし、参照自身の値は変更できません。つまり、同じ参照を使用して、新しいクラスのメモリを割り当て、ブロックの外で永続化させることはできません。  参照自身の値を変更するには、[ref](../../../csharp/language-reference/keywords/ref.md) キーワードまたは [out](../../../csharp/language-reference/keywords/out.md) キーワードを使用してパラメーターを渡します。  説明を簡単にするために、次の例では `ref` だけを使用しています。  
  
## 値による参照型の引き渡し  
 参照型のパラメーター `arr` を値で `Change` メソッドに渡す方法を、次の例で示します。  パラメーターは `arr` への参照であるため、配列要素の値を変更できます。  ただし、他のメモリ位置へのパラメーターの再割り当ては、メソッド内だけで有効です。元の変数 `arr` には影響しません。  
  
 [!code-cs[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 上の例では、参照型の配列 `arr` は、`ref` パラメーターを指定せずにメソッドに渡されています。  このような場合は、`arr` を指す参照のコピーがメソッドに渡されます。  出力は、メソッドが配列要素の内容を \(この場合は `1` から `888` へ\) 変更できることを示しています。  ただし、`Change` メソッド内で [new](../../../csharp/language-reference/keywords/new.md) 演算子を使用して新しいメモリ領域を割り当てると、変数 `pArray` は新しい配列を参照します。  したがって、新しい領域の割り当ての後に変更があっても、`Main` 内で作成されている元の配列 `arr` は影響を受けません。  この例では `Main` メソッド内と `Change` メソッド内で 2 つの配列が作成されています。  
  
## 参照による参照型の引き渡し  
 次の例は前の例と同じですが`ref` のキーワードはメソッドのヘッダーと呼び出しに追加されます。  メソッドの呼び出し元のプログラムに影響元の変数の変更。  
  
 [!code-cs[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 メソッド内でのすべての変更が、`Main` 内の元の配列に影響します。  実際、元の配列は `new` 演算子を使用して再割り当てされています。  つまり、`Change` メソッドの呼び出し後は、`arr` へのすべての参照が、`Change` メソッドで作成された 5 つの要素を持つ配列を指しています。  
  
## 2 つの文字列の交換  
 文字列の交換は、参照によって参照型のパラメーターを渡す方法の良い例です。  次の例では、`str1` と `str2` の 2 つの文字列が `Main` で初期化され、`ref` キーワードを使用してパラメーターとして `SwapStrings` メソッドに渡されています。  2 つの文字列はこのメソッド内で交換され、`Main` 内でもその結果が反映されています。  
  
 [!code-cs[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 この例では、呼び出しプログラムの変数に変更を反映するために、パラメーターを参照で渡す必要があります。  メソッド ヘッダーとメソッド呼び出しの両方から `ref` キーワードを削除すると、呼び出しプログラムには変更が反映されません。  
  
 文字列の詳細については、「[string \(C\# リファレンス\)](../../../csharp/language-reference/keywords/string.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)