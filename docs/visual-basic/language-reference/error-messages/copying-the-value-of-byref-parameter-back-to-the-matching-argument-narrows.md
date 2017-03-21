---
title: "&quot;ByRef&quot; パラメーターの値をコピー &quot;&lt;parametername&gt;&quot;に一致する引数の型から限定&quot;&lt;&quot; typename1 &quot;&gt;&quot; type&quot; に&lt;typename2&gt;&quot; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
dev_langs:
- VB
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 84574006b2e2ccc669fdd83ebfb6eec06b00f041
ms.lasthandoff: 03/13/2017

---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>'ByRef' パラメーターの値をコピー '&lt;parametername&gt;'に一致する引数の型から限定'&lt;' typename1 '&gt;' type' に&lt;typename2&gt;'
拡大変換後の対応するパラメーターの型引数を持つプロシージャが呼び出され、パラメーターから引数への変換を縮小します。  
  
 クラスまたは構造体を定義するときは、そのクラスまたは構造体の型を他の型に変換する&1; つまたは複数の変換演算子を定義できます。 その他の型をクラスまたは構造体の型に変換する逆の変換演算子を定義することもできます。 プロシージャ呼び出しで、クラスまたは構造体の型を使用すると[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の引数の型を対応するパラメーターの型に変換するこれらの変換演算子を使用することができます。  
  
 引数を渡した場合[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の参照を渡す代わりに、手順でローカル変数に引数の値をコピーすることがあります。 このような場合は、プロシージャから制御が戻るとき[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]呼び出し元のコードで引数にローカル変数の値をコピーする必要があります。  
  
 `ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。 種類が異なる場合が[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]双方向で変換する必要があります。 型のいずれかが型の場合、クラスまたは構造体、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]両方と、他の型から変換する必要があります。 これらの変換のいずれかを拡大すると場合、は、逆の変換が縮小可能性があります。  
  
 **エラー ID:** BC32053  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   したがってプロシージャのパラメーターとして、同じ型の呼び出し元の引数を使用可能であれば、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]変換する必要はありません。  
  
-   引数を使ってプロシージャを呼び出す必要がある場合に、パラメーターの型の異なる型が、呼び出し元の引数に値を返す、パラメーターを定義する必要はありません[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)の代わりに`ByRef`します。  
  
-   呼び出し元の引数に値を返す必要がある場合は、逆変換演算子を定義[拡大変換](../../../visual-basic/language-reference/modifiers/widening.md)可能であれば、します。  
  
## <a name="see-also"></a>関連項目  
 [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [プロシージャのパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [値渡しと参照による引数渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [方法: 演算子を定義](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [方法: 変換演算子を定義します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
