---
title: '値 &#39; のコピーByRef &#39;パラメーター &#39;&lt;parametername&gt;&#39; の種類 &#39; から、一致する引数範囲を絞り込みますに戻る&lt;typename1&gt;(& a) を入力します #39 &#39;&lt; 。typename2&gt;&#39;です。'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4bf993639007162e2e17d4b8cb9dfe8d5316acaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>値 &#39; のコピーByRef &#39;パラメーター &#39;&lt;parametername&gt;&#39; の種類 &#39; から、一致する引数範囲を絞り込みますに戻る&lt;typename1&gt;(& a) を入力します #39 &#39;&lt; 。typename2&gt;&#39;です。
プロシージャが、対応するパラメーターの型に拡大変換する引数によって呼び出され、引数には、パラメーターからの変換は縮小します。  
  
 クラスまたは構造体を定義するときは、そのクラスまたは構造体の型を他の型に変換する 1 つまたは複数の変換演算子を定義できます。 その他の型をクラスまたは構造体の型に変換する逆の変換演算子を定義することもできます。 プロシージャ呼び出しでクラスまたは構造体の型を使用すると、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] はこれらの変換演算子を使用して、引数の型を対応するパラメーターの型に変換することができます。  
  
 引数を渡す場合[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]場合がありますの参照を渡す代わりにプロシージャ内のローカル変数に引数の値をコピーします。 このような場合は、プロシージャから返されるときに、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] は呼び出し元のコードの引数にローカル変数の値をコピーする必要があります。  
  
 `ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。 型が異なる場合、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] は双方向で変換する必要があります。 型のいずれかがクラスまたは構造体の型の場合、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] はその型を他の型との間で変換する必要があります。 これらの変換のいずれかを拡大すると場合、逆変換は縮小可能性があります。  
  
 **エラー ID:** BC32053  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   可能な場合は、プロシージャのパラメーターと同じ型の呼び出し元引数を使用して、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] で変換する必要がないようにします。  
  
-   パラメーターの型の異なる型引数を持つプロシージャを呼び出す必要がある場合は、呼び出し元の引数に値を返す、パラメーターを定義する必要はありません[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)の代わりに`ByRef`です。  
  
-   呼び出し元の引数に値を返す必要がある場合、逆変換演算子を定義として[Widening](../../../visual-basic/language-reference/modifiers/widening.md)可能であれば、します。  
  
## <a name="see-also"></a>関連項目  
 [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [プロシージャのパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [引数の値渡しと参照渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [方法 : 演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [方法 : 変換演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Visual Basic での型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
