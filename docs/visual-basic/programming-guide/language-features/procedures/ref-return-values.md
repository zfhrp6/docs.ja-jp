---
title: Ref 戻り値 (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2979359f0ffafe46a62696485bbb87b211c1704
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651242"
---
# <a name="support-for-reference-return-values-visual-basic"></a>参照戻り値 (Visual Basic) のサポート

C# 言語のサポートされている c# 7.0 から始めて、*戻り値を参照*です。 戻り値の参照を理解する方法の 1 つは、メソッドへの参照によって渡される引数の逆であることです。 参照によって渡された引数が変更されると、変更が、呼び出し元に対して、変数の値に反映されます。 提供する場合、メソッドの参照の戻り値を呼び出し元に、呼び出し元の参照の戻り値に加えた変更が、呼び出されたメソッドのデータに反映されます。

Visual Basic では、参照を持つメソッドを作成すると、戻り値が、参照戻り値を使用することは許可されません。 つまり、参照戻り値を持つメソッドを呼び出すし、その戻り値を変更し、参照の戻り値の変更は、呼び出されたメソッドのデータに反映されます。

## <a name="modifying-the-ref-return-value-directly"></a>Ref の戻り値を直接変更します。

常に成功して、されていないメソッドは`ByRef`パラメーター参照の戻り値を直接変更することができます。 これを行う参照戻り値を返す式を割り当てると、新しい値。 

次の c# の例では定義、`NumericValue.IncrementValue`を内部値をインクリメントし、参照として返すメソッドの戻り値。 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

参照は、値は、Visual Basic の例を次に、呼び出し元によって変更を返します。 なおでは、行、`NumericValue.IncrementValue`メソッドの呼び出しが、メソッドに値を割り当てられません。 代わりに、メソッドによって返される参照の戻り値に値を割り当てます。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>ヘルパー メソッドを使用してください。

その他の場合、メソッド呼び出しの参照の戻り値を直接変更できない可能性があります常にことをお勧めします。 たとえば、文字列を返す検索メソッド可能性があります常に一致が見つかりません。 その場合は、検索が成功した場合にのみ、参照の戻り値を変更します。

次の c# の例では、このシナリオを示します。 定義する、 `Sentence` c# で記述されたクラスが含まれています、`FindNext`メソッドを指定した部分文字列で始まる文章内の次の単語を検索します。 文字列は参照戻り値として返され、参照によりメソッドに渡される `Boolean` 変数は検索が成功したかどうかを示します。 参照の戻り値読み取りことを示します、呼び出し元できましていないのみ返される値です。そのユーザーも変更できますとで内部に含まれるデータにその変更が反映されます、`Sentence`クラスです。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

参照を直接変更する値ここではなく、信頼性の高いためを一致するものを検索し、センテンス内の最初の単語を返すメソッドの呼び出しが失敗するを返します。 その場合は、呼び出し元は誤って文の最初の単語を変更します。 返す、呼び出し元で、これを防止でした、 `null` (または`Nothing`Visual Basic で)。 その場合は、値がある文字列を変更しようとしていますが、`Nothing`スロー、<xref:System.NullReferenceException>です。 返す、呼び出し元によっても禁止することが場合<xref:System.String.Empty?displayProperty=nameWithType>、呼び出し元は、値が文字列変数を定義することが必要ですが、<xref:System.String.Empty?displayProperty=nameWithType>です。 呼び出し元は、その文字列を変更できます、自体を変更の目的なし、変更後の文字列によって格納される、センテンス内の単語にリレーションシップがあるないので、`Sentence`クラスです。

このシナリオを処理する最善の方法では、ヘルパー メソッドへの参照によって参照戻り値を渡すです。 ヘルパー メソッドには、メソッド呼び出しが成功したし、変わった場合は、変更、参照値を返すかどうかを判断するロジックが含まれています。 次の例では、可能な実装を提供します。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>関連項目

[引数値渡しと参照渡し](passing-arguments-by-value-and-by-reference.md)   
[Visual Basic におけるプロシージャ](index.md)   


