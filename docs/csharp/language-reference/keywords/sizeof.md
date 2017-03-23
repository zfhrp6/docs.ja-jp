---
title: "sizeof (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "sizeof_CSharpKeyword"
  - "sizeof"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "sizeof キーワード [C#]"
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# sizeof (C# リファレンス)
アンマネージ型のサイズ \(バイト単位\) を取得します。  アンマネージ型には、後の表に示す組み込み型と、次の型とが含まれます。  
  
-   列挙型  
  
-   ポインター型  
  
-   参照型のフィールドやプロパティを含まないユーザー定義の構造体  
  
 `int` のサイズを取得する方法を次の例に示します。  
  
```c#  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## 解説  
 C\# バージョン 2.0 以降、組み込み型に `sizeof` を適用する場合に、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) モードを使用する必要はありません。  
  
 `sizeof` 演算子はオーバーロードできません。  `sizeof` 演算子により返される値の型は `int` です。  次の表に、特定の組み込み型をオペランドとする `sizeof` 式と、代用される定数値を示します。  
  
|式|定数値|  
|-------|---------|  
|`sizeof(sbyte)`|1|  
|`sizeof(byte)`|1|  
|`sizeof(short)`|2|  
|`sizeof(ushort)`|2|  
|`sizeof(int)`|4|  
|`sizeof(uint)`|4|  
|`sizeof(long)`|8|  
|`sizeof(ulong)`|8|  
|`sizeof(char)`|2 \(Unicode\)|  
|`sizeof(float)`|4|  
|`sizeof(double)`|8|  
|`sizeof(decimal)`|16|  
|`sizeof(bool)`|1|  
  
 struct などその他のすべての型については、`sizeof` 演算子はアンセーフ コード ブロックでのみ使用できます。  <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> メソッドは使用できますが、このメソッドの戻り値が `sizeof` の戻り値と等しいとは限りません。  <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> は値のマーシャリング後にサイズを返します。一方、`sizeof` は、共通言語ランタイムによる割り当ての後に埋め込みを含めたサイズを返します。  
  
## 使用例  
 [!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [enum](../../../csharp/language-reference/keywords/enum.md)   
 [unsafe コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [定数](../../../csharp/programming-guide/classes-and-structs/constants.md)