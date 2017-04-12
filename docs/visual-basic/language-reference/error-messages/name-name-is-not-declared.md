---
title: "名前 &quot;&lt;名前&gt;&quot; が宣言されていない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
dev_langs:
- VB
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 81b6862a7f8ceb7998b2ea53336ed3af46b1db5f
ms.lasthandoff: 03/13/2017

---
# <a name="name-39ltnamegt39-is-not-declared"></a>名前 '&lt;名前&gt;' が宣言されていません。
プログラミングの要素をステートメントが、コンパイラはその正確な名前を持つ要素を見つけられないです。  
  
 **エラー ID:** BC30451  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  参照元のステートメントで名前のスペルを確認します。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]小文字を区別しない、その他の違いが完全に別の名前と見なされますが、します。 アンダースコア (`_`) も名前の一部であり、スペルに含まれます。  
  
2.  メンバー アクセス演算子があることを確認 (`.`) オブジェクトとメンバーの間です。 ある場合など、<xref:System.Windows.Forms.TextBox>という名前のコントロール`TextBox1`にアクセスするには、その<xref:System.Windows.Forms.TextBoxBase.Text%2A>プロパティを入力する必要があります`TextBox1.Text`</xref:System.Windows.Forms.TextBoxBase.Text%2A></xref:System.Windows.Forms.TextBox>。 代わりに「 `TextBox1Text`」と入力した場合、別の名前と見なされます。  
  
3.  スペルが正しい、オブジェクト メンバー アクセスの構文が正しい場合は、要素が宣言されていることを確認します。 詳細については、次を参照してください。[宣言された要素](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)します。  
  
4.  プログラミングの要素が宣言された場合は、スコープ内にあることを確認します。 参照元のステートメントがプログラミングの要素が宣言されている領域の外側にある場合は、要素名を修飾する必要があります。 詳細については、次を参照してください。 [Visual Basic におけるスコープ](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)します。  
  
## <a name="see-also"></a>関連項目  
 [宣言と定数の概要](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)   
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [宣言された要素名](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
