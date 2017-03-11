---
title: "引数としての配列の受け渡し (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "配列 [C#], 渡す (引数として)"
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 引数としての配列の受け渡し (C# プログラミング ガイド)
配列は引数としてメソッド パラメーターに渡すことができます。  配列は参照型であるため、メソッドで要素の値を変更できます。  
  
## 引数としての 1 次元配列の受け渡し  
 初期化された 1 次元配列をメソッドに渡すことができます。  たとえば、次のステートメントは配列を印刷メソッドに渡します。  
  
 [!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_1.cs)]  
  
 印刷メソッドの部分的な実装を次のコードに示します。  
  
 [!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_2.cs)]  
  
 次の例に示すように、新しい配列の初期化と受け渡しを 1 ステップで行うことができます。  
  
 [!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_3.cs)]  
  
## 例  
  
### Description  
 次の例では、文字列の配列は初期化され、文字列の `PrintArray` メソッドに引数として渡されます。  メソッドは配列の要素を表示します。  次に、配列引数を値渡しで送信しても、配列要素の変更の妨げにはならないことを示すために、`ChangeArray` メソッドと `ChangeArrayElement` メソッドが呼び出されています。  
  
### コード  
 [!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_4.cs)]  
  
## 引数としての多次元配列の受け渡し  
 初期化された多次元配列は、1 次元配列を渡す場合と同じ方法でメソッドに渡します。  
  
 [!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_5.cs)]  
  
 2 次元配列を引数として受け入れる印刷メソッドの部分宣言を次のコードに示します。  
  
 [!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_6.cs)]  
  
 次の例に示すように、新しい配列の初期化と受け渡しを 1 ステップで行うことができます。  
  
 [!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_7.cs)]  
  
## 例  
  
### Description  
 次の例では、整数の 2 次元配列を初期化し、`Print2DArray` メソッドに渡します。  メソッドは配列の要素を表示します。  
  
### コード  
 [!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_8.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)