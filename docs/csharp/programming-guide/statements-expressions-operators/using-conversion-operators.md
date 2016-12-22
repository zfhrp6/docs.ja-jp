---
title: "変換演算子の使用 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "変換演算子 [C#]"
  - "変換 [C#], 演算子"
  - "明示的な変換演算子 [C#]"
  - "暗黙的な変換演算子 [C#]"
  - "演算子 [C#], 変換"
  - "ユーザー定義変換 [C#]"
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 変換演算子の使用 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

より使いやすい `implicit` 変換演算子を使用することもできますし、型を変換していることをコードを読むすべての人に明確に示すために `explicit` 変換演算子を使用することもできます。  このトピックでは、両方の型変換演算子を示します。  
  
> [!NOTE]
>  単純な型変換については、「[方法: 文字列を数値に変換する](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)」、「[方法: バイト配列を int に変換する](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)」、「[方法: 16 進文字列と数値型の間で変換する](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)」、または「<xref:System.Convert>」を参照してください。  
  
## 使用例  
 ここでは、明示的な変換演算子の例を示します。  この演算子は、<xref:System.Byte> 型を `Digit` という値型に変換します。  すべての byte 型を Digit 型に変換できるとは限らないため、変換は明示的に行うように指定されています。つまり、`Main` メソッドに示すように、キャストを使用する必要があります。  
  
 [!code-cs[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## 使用例  
 この例は、上の例で行った処理を元に戻す変換演算子を定義することにより、暗黙の変換演算子を示しています。この例では、`Digit` という値クラスを整数 <xref:System.Byte> 型に変換します。  すべての Digit 型を <xref:System.Byte> に変換できるため、変換をユーザーに明示する必要はありません。  
  
 [!code-cs[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [変換演算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [is](../../../csharp/language-reference/keywords/is.md)