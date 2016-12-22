---
title: "ushort (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ushort"
  - "ushort_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ushort キーワード [C#]"
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ushort (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`ushort` キーワードは、次の表に示されたサイズと範囲に従って値を格納する整数データ型を表します。  
  
|種類|範囲|サイズ|.NET Framework 型|  
|--------|--------|---------|----------------------|  
|`ushort`|0 ～ 65,535。|符号なし 16 ビット整数|<xref:System.UInt16?displayProperty=fullName>|  
  
## リテラル  
 `ushort` 変数の宣言と初期化の例を次に示します。  
  
```  
  
ushort myShort = 65535;  
```  
  
 上のように宣言すると、整数リテラル `65535` は暗黙的に [int](../../../csharp/language-reference/keywords/int.md) から `ushort` に変換されます。  整数リテラルが `ushort` の範囲を超えると、コンパイル エラーになります。  
  
 オーバーロードされたメソッドを呼び出すときは、キャストを使用する必要があります。  たとえば、`ushort` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用したオーバーロードされたメソッドがあるとします。  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
  
 `ushort` キャストを使用すると、正しい型が呼び出されます。次に例を示します。  
  
```  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## 変換  
 `ushort` から [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。  
  
 [byte](../../../csharp/language-reference/keywords/byte.md) または [char](../../../csharp/language-reference/keywords/char.md) から `ushort` への暗黙の型変換が組み込まれています。  その他の型の場合は、キャストを使用して明示的な変換を実行する必要があります。  たとえば、2 つの `ushort` 変数 `x` と `y` があるとします。  
  
```  
  
ushort x = 5, y = 12;  
```  
  
 次の代入ステートメントは、代入演算子の右側にある算術式が既定で `int` に評価されるため、コンパイル エラーになります。  
  
```  
  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 このエラーを修正するには、キャストを使用します。  
  
```  
  
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 ただし、次のステートメントは使用できます。このステートメントでは、変換先の変数の記憶サイズは元のサイズ以上になります。  
  
```  
int m = x + y;  
long n = x + y;  
```  
  
 また、浮動小数点型から `ushort` への暗黙の型変換が行われないことに注意してください。  たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイラ エラーになります。  
  
```  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float \(C\# リファレンス\)](../../../csharp/language-reference/keywords/float.md)」と「[double \(C\# リファレンス\)](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
 暗黙の数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 <xref:System.UInt16>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)