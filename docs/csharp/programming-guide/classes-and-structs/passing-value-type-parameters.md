---
title: "値型のパラメーターの引き渡し (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "メソッド パラメーター [C#], 値型"
  - "パラメーター [C#], value"
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# 値型のパラメーターの引き渡し (C# プログラミング ガイド)
[参照型](../../../csharp/language-reference/keywords/reference-types.md)の変数はデータへの参照を持つのに対し、[値型](../../../csharp/language-reference/keywords/value-types.md)の変数はデータを直接格納します。  値をメソッドに値型の変数を渡すとメソッドに変数のコピーを渡すことを意味します。  引数の変数でメソッド内に存在しない格納されている元のデータには影響しませんパラメーターに変更します。  呼び出されたメソッドのパラメーターの値を変更する場合 [ref](../../../csharp/language-reference/keywords/ref.md) または [アウト](../../../csharp/language-reference/keywords/out.md) のキーワードを使用してパラメーターを参照で渡す必要があります。  説明を簡単にするために、次の例では `ref` だけを使用しています。  
  
## 値による値型の引き渡し  
 値によって値型を渡す方法を次の例で示します。  変数 `n` は、`SquareIt` メソッドに値で渡されます。  メソッド内で変更があっても、元の変数値には影響しません。  
  
 [!code-cs[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]  
  
 可変 `n` は値型です。  これはデータ `5` 値が含まれます。  `SquareIt` が呼び出されると、`n` の内容がパラメーター `x` にコピーされ、値はメソッド内で 2 乗されます。  ただし`Main` では `n` の値は前に `SquareIt` のメソッドを呼び出すと同じです。  メソッド内での変更はローカル変数 `x` にのみ影響します。  
  
## 参照による値型の引き渡し  
 次の例は前の例と同じですが引数は `ref` のパラメーターとして渡されます。  基になる `n`引数の値は`x` がメソッドで変更されても変更されます。  
  
 [!code-cs[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]  
  
 この例では、`n` の値ではなく、`n` への参照が渡されています。  パラメーター `x` は [int](../../../csharp/language-reference/keywords/int.md) ではなく、`int` への参照 \(例では、`n` への参照\) です。  したがって`x` がメソッド内で 2 乗の場合何が 2 乗されます `n` は `x` に示されています。  
  
## 値型の交換  
 引数の値を変更する一般的な例はメソッドを 2 回変数を渡すメソッドはコンテンツを交換しますのメソッドです。  参照をスワップのメソッドに引数を渡す必要があります。  はメソッド内のパラメーターのローカル コピーを入れ替え変更は呼び出し元のメソッドに発生しません。  次の例では整数値を交換します。  
  
 [!code-cs[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]  
  
 `SwapByRef` のメソッドを呼び出すと次の例に示すように呼び出しで `ref` のキーワードを使用します。  
  
 [!code-cs[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [参照型のパラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)