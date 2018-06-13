---
title: '&lt;proceduresignature1&gt;はオーバー ロードするため、CLS に準拠していない&lt;proceduresignature2&gt;が異なる配列パラメーター型の配列または配列パラメーター型のランクのみ'
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0d150dad8d32b4bfa2b9e549e068ef24382d0eba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594729"
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>&lt;proceduresignature1&gt;はオーバー ロードするため、CLS に準拠していない&lt;proceduresignature2&gt;が異なる配列パラメーター型の配列または配列パラメーター型のランクのみ
プロシージャやプロパティとしてマーク`<CLSCompliant(True)>`と別のプロシージャまたはプロパティをオーバーライドし、パラメーター リストの唯一の違いは、ジャグ配列の入れ子レベルまたは配列のランク。  
  
 次の宣言では、2 番目と 3 番目の宣言は、このエラーを生成します。  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 2 番目の宣言元の 1 次元のパラメーターを変更する`arrayParam`配列の配列にします。 3 番目の宣言の変更`arrayParam`2 次元配列 (ランク 2) にします。 Visual Basic では、これらの変更のいずれかによってのみ異なるオーバー ロードでできます、このようなオーバー ロードが準拠するいないと、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS)。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40035  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   CLS 準拠を必要とする場合は、それぞれ異なる手段がこのヘルプ ページに示されている変更のみにする、オーバー ロードを定義します。  
  
-   このヘルプに示した変更点のみによってページのオーバー ロードが異なることが必要な場合で、削除、<xref:System.CLSCompliantAttribute>定義からとしてマークまたは`<CLSCompliant(False)>`です。  
  
## <a name="see-also"></a>関連項目  
   
 [プロシージャのオーバーロード](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [オーバーロード](../../../visual-basic/language-reference/modifiers/overloads.md)
