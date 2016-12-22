---
title: "固定サイズ バッファー (C# プログラミング ガイド) | Microsoft Docs"
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
  - "固定サイズ バッファー [C#]"
  - "アンセーフ バッファー [C#]"
  - "アンセーフ コード [C#], 固定サイズのバッファー"
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 固定サイズ バッファー (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# では、[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) ステートメントを使用して、データ構造内に固定サイズのバッファーを作成できます。  この機能は、別の言語で作成されたコード、既存の DLL プロジェクト、既存の COM プロジェクトなど、各種既存コードを操作するときに便利です。  固定配列は、標準の構造体メンバーのあらゆる属性または修飾子を使用できます。  唯一の制限として、配列型を `bool`、`byte`、 `char`、 `short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float`、または `double` にする必要があります。  
  
```  
private fixed char name[30];  
```  
  
## 解説  
 以前のバージョンの C\# では、C\+\+ スタイルの固定サイズの構造体を宣言するのが困難でした。これは、配列を格納する C\# 構造体に配列要素が含まれないためです。  代わりに、この構造体には配列要素への参照が含まれます。  
  
 C\# 2.0 では、[安全でない](../../../csharp/language-reference/keywords/unsafe.md)コード ブロックでの使用時に固定サイズの配列を[構造体](../../../csharp/language-reference/keywords/struct.md)に埋め込む機能が追加されています。  
  
 たとえば、C\# 2.0 より前のバージョンでは、次の `struct` のサイズは 8 バイトです。  `pathName` 配列は、ヒープに割り当てられた配列への参照です。  
  
 [!CODE [csProgGuidePointers#19](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#19)]  
  
 C\# 2.0 以降では、`struct` に埋め込まれた配列を保持できるようになりました。  次の例では、`fixedBuffer` 配列のサイズは固定です。  配列の要素にアクセスするには、`fixed` ステートメントを使用して、最初の要素へのポインターを取得します。  `fixed` ステートメントは、`fixedBuffer` のインスタンスをメモリ内の特定の場所に固定します。  
  
 [!CODE [csProgGuidePointers#20](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#20)]  
  
 128 要素の `char` 配列のサイズは 256 バイトです。  固定サイズの [char](../../../csharp/language-reference/keywords/char.md) バッファーは、エンコーディングとは無関係に、常に 1 文字につき 2 バイトを使用します。  これは、`CharSet = CharSet.Auto` や `CharSet = CharSet.Ansi` によって char バッファーが API メソッドや構造体にマーシャリングされる場合でも同じです。  詳細については、「<xref:System.Runtime.InteropServices.CharSet>」を参照してください。  
  
 一般的な固定サイズの配列には、この他に [bool](../../../csharp/language-reference/keywords/bool.md) 配列があります。  `bool` 配列の要素のサイズは常に 1 バイトです。  `bool` 配列はビット配列やバッファーの作成には適していません。  
  
> [!NOTE]
>  [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) を使用して作成されたメモリを除き、C\# コンパイラおよび共通言語ランタイム \(CLR: Common Language Runtime\) は、バッファー オーバーランのセキュリティ チェックを実行しません。  固定サイズの配列には、すべてのアンセーフ コードと同様に注意してください。  
  
 アンセーフ バッファーは、通常の配列と次の点で異なります。  
  
-   アンセーフ バッファーは、unsafe コンテキストでのみ使用できます。  
  
-   アンセーフ バッファーは常にベクター \(1 次元配列\) です。  
  
-   配列の宣言には、`char id[8]` のように要素数を記述する必要があります。  代わりに `char id[]` を使用することはできません。  
  
-   アンセーフ バッファーは、unsafe コンテキストの構造体のインスタンス フィールドのみに限られます。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [unsafe コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [相互運用性](../../../csharp/programming-guide/interop/interoperability.md)