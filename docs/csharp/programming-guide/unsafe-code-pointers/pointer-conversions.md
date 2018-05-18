---
title: ポインター変換 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: e0c3a409d76468a6e214a96e8bb326a9d906fe18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="pointer-conversions-c-programming-guide"></a>ポインター変換 (C# プログラミング ガイド)
定義済みの暗黙的なポインター変換を次の表に示します。 暗黙的な変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。  
  
## <a name="implicit-pointer-conversions"></a>暗黙的なポインター変換  
  
|From|終了|  
|----------|--------|  
|任意のポインター型|void*|  
|null|任意のポインター型|  
  
 明示的なポインター変換は、暗黙的な変換がない場合に、キャスト式を使用して、変換を実行するために使用します。 次の表はこの変換についてまとめたものです。  
  
## <a name="explicit-pointer-conversions"></a>明示的なポインター変換  
  
|From|終了|  
|----------|--------|  
|任意のポインター型|その他のポインター型|  
|sbyte、byte、short、ushort、int、uint、long または ulong|任意のポインター型|  
|任意のポインター型|sbyte、byte、short、ushort、int、uint、long または ulong|  
  
## <a name="example"></a>例  
 次の例では、`int` へのポインターは `byte` へのポインターに変換されます。 ポインターは、変数の最下位バイト アドレスを指すことに注意してください。 `int` のサイズ (4 バイト) まで結果を連続してインクリメントする場合、変数の残りのバイトを表示することができます。  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [型](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
