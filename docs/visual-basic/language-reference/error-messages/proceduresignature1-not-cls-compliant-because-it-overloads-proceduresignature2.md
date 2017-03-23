---
title: "&lt;proceduresignature1&gt;はオーバー ロードするため、CLS に準拠していない&lt;proceduresignature2&gt;が異なるか配列パラメーター型の配列または配列パラメーター型のランクのみ |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
dev_langs:
- VB
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: 11
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
ms.openlocfilehash: 984c04a107444036b980439b231d27a8a81656c1
ms.lasthandoff: 03/13/2017

---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>&lt;proceduresignature1&gt;はオーバー ロードするため、CLS に準拠していない&lt;proceduresignature2&gt;が異なるか配列パラメーター型の配列または配列パラメーター型のランク
プロシージャやプロパティとしてマーク`<CLSCompliant(True)>`と別のプロシージャまたはプロパティを上書きされ、パラメーター リストの唯一の違いは、ジャグ配列の入れ子レベルまたは配列のランク。  
  
 次の宣言では、2 番目と&3; 番目の宣言は、このエラーを生成します。  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 2 番目の宣言元の&1; 次元のパラメーターを変更する`arrayParam`配列の配列にします。 3 番目の宣言の変更`arrayParam`2 次元配列 (rank 2) にします。 Visual Basic でこれらの変更の&1; つだけが異なるためのオーバー ロードは、中にこのようなオーバー ロードが準拠していない、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS に) します。  
  
 適用すると、<xref:System.CLSCompliantAttribute>プログラミング要素に属性を設定する`isCompliant`するか、パラメーター`True`または`False`を対応または非対応を示します</xref:System.CLSCompliantAttribute>。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 適用しない場合、<xref:System.CLSCompliantAttribute>要素に準拠するいないと見なされます</xref:System.CLSCompliantAttribute>。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40035  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   CLS 準拠を必要とする場合は、このページで示されている変更のみよりも多くの方法で互いに異なる、オーバー ロードを定義します。  
  
-   このヘルプに示した変更点だけがページで、削除、オーバー ロードが異なることが必要な場合、<xref:System.CLSCompliantAttribute>定義からとしてマーク`<CLSCompliant(False)>`</xref:System.CLSCompliantAttribute>。  
  
## <a name="see-also"></a>関連項目  
 [\<経由で PAVE > CLS 準拠のコードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [プロシージャのオーバー ロード](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [オーバーロード](../../../visual-basic/language-reference/modifiers/overloads.md)
