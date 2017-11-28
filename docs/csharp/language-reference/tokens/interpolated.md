---
title: "$ (C# リファレンス)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
ms.assetid: 7d9e21b5-eac3-4878-9530-50e4da578acd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d245bab063721abdb930aae113aab2094553b9bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-c-reference"></a>$ (C# リファレンス)

リテラル文字列を[挿入文字列](../keywords/interpolated-strings.md)として識別します。 挿入文字列はテンプレートのような文字列で、"*挿入式*" とリテラル テキストを含みます。 挿入文字列が解決されると、たとえば代入ステートメントまたはメソッド呼び出し内で、結果文字列の文字列表現によって挿入式が置き換えられます。 挿入文字列は、.NET Framework でサポートされている[複合書式指定文字列](../../../standard/base-types/composite-format.md)の代わりになるものです。

次の例では、`$` 文字を使用して、挿入文字列を定義します。

[!code-csharp[interpolated-string-symbol](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]

挿入文字列の詳細については、トピック「[挿入文字列](../keywords/interpolated-strings.md)」を参照してください。

## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 特殊文字](../../../csharp/language-reference/tokens/index.md)
