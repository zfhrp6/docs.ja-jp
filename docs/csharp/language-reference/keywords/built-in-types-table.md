---
title: "組み込み型の一覧表 (C# リファレンス) | Microsoft Docs"
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
  - "C# の組み込み型"
  - "型 [C#], 組み込み"
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 組み込み型の一覧表 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# の組み込み型のキーワードは、次のとおりです。これらは、<xref:System> 名前空間で定義されている型のエイリアスです。  
  
|C\# 型|.NET Framework 型|  
|-----------|----------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[object](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[string](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## 解説  
 表内の `object` と `string` を除くすべての型は、単純型と呼ばれます。  
  
 C\# 型のキーワードとエイリアスは、相互に交換できます。  たとえば、整数の変数を宣言する場合は、次のいずれかの宣言を使用できます。  
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 C\# 型の実際の型を表示するには、`GetType()` システム メソッドを使用します。  たとえば、`myVariable` の型を表すシステム エイリアスを表示するには、次のステートメントを使用します。  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 また、[typeof](../../../csharp/language-reference/keywords/typeof.md) 演算子も使用できます。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [値型](../../../csharp/language-reference/keywords/value-types.md)   
 [既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)   
 [数値結果テーブルの書式設定](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)   
 [動的](../../../csharp/language-reference/keywords/dynamic.md)   
 [型のリファレンス表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)