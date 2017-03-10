---
title: "方法 : ポインターを使用してバイトの配列をコピーする (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "配列 [C#], byte"
  - "バイト配列 [C#]"
  - "ポインター [C#], バイトをコピーするための"
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 方法 : ポインターを使用してバイトの配列をコピーする (C# プログラミング ガイド)
次の例では、ポインターを使用して配列間でバイトをコピーします。  
  
 この例では、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードを使用して、`Copy` メソッド内でポインターを使用できるようにしています。  [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) ステートメントを使用して、コピー元とコピー先の配列へのポインターを宣言します。  これで、ガベージ コレクションによって移動されないように、メモリ内でコピー元とコピー先の位置が*固定*されます。  `fixed` ブロックが完了すると、配列のメモリ ブロックの固定が解除されます。  この例の `Copy` メソッドでは `unsafe` キーワードを使用しているため、**\/unsafe** コンパイラ オプションを指定してコンパイルする必要があります。  Visual Studio でこのオプションを設定するには、プロジェクト名を右クリックし、**\[プロパティ\]** をクリックします。  **\[ビルド\]** タブで、**\[アンセーフ コードの許可\]** を選択します。  
  
## 使用例  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers2.cs#3)]  
  
 [!code-cs[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers.cs#18)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [unsafe コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [\/unsafe \(Enable Unsafe Mode\)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)