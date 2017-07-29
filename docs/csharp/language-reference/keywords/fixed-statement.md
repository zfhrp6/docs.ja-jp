---
title: "fixed ステートメント (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
dev_langs:
- CSharp
helpviewer_keywords:
- fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 24
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4e1f810f6e6cfaef3a65c7391f074b414ef18b5a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="fixed-statement-c-reference"></a>fixed ステートメント (C# リファレンス)
`fixed` ステートメントは、移動可能な変数がガベージ コレクターにより再配置されることを防ぎます。 `fixed` ステートメントは、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストでのみ許可されます。 `Fixed` は、[固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)の作成にも使うことができます。  
  
 `fixed` ステートメントは、マネージ変数へのポインターを設定し、ステートメントの実行中にその変数を "固定" します。 `fixed` を指定しないと、ガベージ コレクションが変数を予期せず再配置するため、移動可能なマネージ変数へのポインターはほとんど役に立ちません。 C# コンパイラでは、`fixed` ステートメントでマネージ変数へのポインターを割り当てることだけができます。  
  
 [!code-cs[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 配列、文字列、固定サイズ バッファー、または変数のアドレスを使って、ポインターを初期化できます。 次の例では、変数のアドレス、配列、および文字列の使い方を示します。 固定サイズ バッファーについて詳しくは、「[固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)」をご覧ください。  
  
 [!code-cs[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 すべてが同じ型であれば、複数のポインターをまとめて初期化できます。  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 異なる型のポインターを初期化するには、次の例で示すように、`fixed` ステートメントを入れ子にします。  
  
 [!code-cs[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 ステートメント内のコードの実行が済むと、固定された変数は固定を解除されて、ガベージ コレクションの対象になります。 そのため、`fixed` ステートメントの外側ではこれらの変数を参照しないでください。  
  
> [!NOTE]
>  fixed ステートメントで初期化されたポインターは変更できません。  
  
 unsafe モードでは、スタック上のメモリを割り当てることができ、スタックはガベージ コレクションの対象にならないので、固定する必要はありません。 詳しくは、「[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)」をご覧ください。  
  
## <a name="example"></a>例  
 [!code-cs[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

