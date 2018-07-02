---
title: break ステートメント (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 987ee1ca5601b3dd105412bf0fa18361c57a95fd
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315239"
---
# <a name="break-c-reference"></a>break (C# リファレンス)

`break` ステートメントは、これを囲むループまたは [switch](../../../csharp/language-reference/keywords/switch.md) ステートメントのうち、最も内側のものを終了させます。 終了したステートメントの次にステートメントがある場合は、そこに制御が移動します。

## <a name="example"></a>例

次の例では、条件付きステートメントに 1 から 100 までをカウントするカウンターがあります。ただし、`break` ステートメントによって、ループは 4 回で終了します。

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>例

この例では、`break` ステートメントを使用して、入れ子になった内側のループから抜け出し、外側のループに制御を戻します。

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>例

次に示すのは、[switch](../../../csharp/language-reference/keywords/switch.md) ステートメントで `break` を使用する例です。

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

`4` を入力すると、出力は次のようになります。

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>参照

[C# リファレンス](../../../csharp/language-reference/index.md)  
[C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
[C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
[switch](../../../csharp/language-reference/keywords/switch.md)  
[ジャンプ ステートメント](../../../csharp/language-reference/keywords/jump-statements.md)  
[繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)
