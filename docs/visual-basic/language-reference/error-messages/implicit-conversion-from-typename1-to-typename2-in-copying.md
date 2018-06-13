---
title: 暗黙的な変換&#39; &lt;typename1&gt; &#39;に&#39; &lt;typename2&gt; &#39;の値をコピー中&#39;ByRef&#39;パラメーター &#39; &lt;parametername&gt; &#39; 、一致する引数にします。
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: b1f772598b18f8edfe0198f62d78854d30f993ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590001"
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>暗黙的な変換&#39; &lt;typename1&gt; &#39;に&#39; &lt;typename2&gt; &#39;の値をコピー中&#39;ByRef&#39;パラメーター &#39; &lt;parametername&gt; &#39; 、一致する引数にします。
プロシージャが呼び出される、 [ByRef](../../../visual-basic/language-reference/modifiers/byref.md)対応するパラメーターとは異なる型の引数。  
  
 引数を渡す場合`ByRef`、Visual Basic は、参照を渡す代わりにプロシージャ内のローカル変数に引数の値をコピーすることがあります。 このような場合は、プロシージャが戻るとき、Visual Basic 必要がありますにコピーしてローカル変数の値戻す呼び出し元のコードの引数。  
  
 `ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。 型が異なる場合は、Visual Basic が双方向で変換する必要があります。 使用できないため`CType`または暗黙的なプロシージャ引数、またはパラメーター、そのような変換でその他の変換キーワードのいずれかが常にします。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC41999  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   可能であれば、ので Visual Basic は、変換を行う必要はありませんは、プロシージャのパラメーターと同じ型の呼び出し元の引数を使用します。  
  
-   パラメーターの型の異なる型引数を持つプロシージャを呼び出す必要がある場合は、呼び出し元の引数に値を返す、パラメーターを定義する必要はありません[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)の代わりに`ByRef`です。  
  
## <a name="see-also"></a>関連項目  
 [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [プロシージャのパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [引数の値渡しと参照渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
