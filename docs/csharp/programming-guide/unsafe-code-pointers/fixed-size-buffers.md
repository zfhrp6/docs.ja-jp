---
title: "固定サイズ バッファー (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6c5cacb588dc263e5b72e4b3cd93ad10b4b681f2
ms.lasthandoff: 03/13/2017

---
# <a name="fixed-size-buffers-c-programming-guide"></a>固定サイズ バッファー (C# プログラミング ガイド)
C# では、[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) ステートメントを使って、データの構造体に固定サイズの配列を持ったバッファーを作成することができます。 これは既存のコード (他の言語で記述されたコード、既存の DLL、COM プロジェクトなど) を扱う場面で役立ちます。 この固定配列には、標準的な構造体メンバーで許容されている属性または修飾子であれば、何でも適用することができます。 ただし配列の型は `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float`、`double` のいずれかに該当する必要があり、それが唯一の制限となります。  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a>コメント  
 以前のバージョンの C# では、C++ スタイルの固定サイズ構造体を宣言することが困難でした。配列を含んだ C# の構造体には、配列の要素は格納されないためです。 この場合、構造体には、配列の要素ではなく、その参照が格納されます。  
  
 C# 2.0 では、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) のコード ブロックで使われている [struct](../../../csharp/language-reference/keywords/struct.md) に、固定サイズの配列を埋め込むことができるようになりました。  
  
 たとえば C# 2.0 未満では、以下の `struct` のサイズは 8 バイトとなります。 `pathName` 配列は、ヒープに割り当てられた配列の参照です。  
  
 [!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 C# 2.0 以降では、`struct` が埋め込み配列を保持できるようになりました。 以下の例の `fixedBuffer` 配列は固定サイズです。 配列の要素にアクセスするには、`fixed` ステートメントを使用して先頭要素へのポインターを確立します。 `fixed` ステートメントによって、`fixedBuffer` のインスタンスがメモリ内の特定の位置に固定されます。  
  
 [!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 要素数 128 の `char` 配列のサイズは 256 バイトです。 固定サイズの [char](../../../csharp/language-reference/keywords/char.md) 型バッファーは、エンコーディングに関係なく常に、1 文字あたり 2 バイトを消費します。 これは、char 型のバッファーが、`CharSet = CharSet.Auto` または `CharSet = CharSet.Ansi` で API メソッドや構造体にマーシャリングされたときにも当てはまります。 詳細については、<xref:System.Runtime.InteropServices.CharSet> を参照してください。  
  
 一般的な固定サイズの配列としては、他にも [bool](../../../csharp/language-reference/keywords/bool.md) 配列があります。 `bool` 配列内の要素のサイズは常に 1 バイトです。 `bool` 配列は、ビット配列やバッファーの作成には適していません。  
  
> [!NOTE]
>  C# コンパイラおよび共通言語ランタイム (CLR) は、[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) を使って作成されたメモリを除き、バッファー オーバーランのセキュリティ チェックを実行しません。 その他のアンセーフ コードと同様、十分な注意が必要です。  
  
 アンセーフ バッファーは、次の点で通常の配列とは異なります。  
  
-   アンセーフ バッファーの使用は、unsafe コンテキストに限られます。  
  
-   アンセーフ バッファーは常にベクタ (1 次元配列) です。  
  
-   配列の宣言には要素数を指定する必要があります (例: `char id[8]`)。 `char id[]` のようにすることはできません。  
  
-   アンセーフ バッファーは、unsafe コンテキストで構造体のインスタンス フィールドとしてのみ使用できます。  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [相互運用性](../../../csharp/programming-guide/interop/index.md)
