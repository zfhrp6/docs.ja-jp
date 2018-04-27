---
title: 名前&#39;&lt;名前&gt;&#39;が宣言されていません
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26245952a2dc5341dedba6c497c47773b882b49b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="name-39ltnamegt39-is-not-declared"></a>名前&#39;&lt;名前&gt;&#39;が宣言されていません
ステートメントがプログラミング要素を参照しますが、コンパイラはその正確な名前を持つ要素を見つけることができません。  
  
 **エラー ID:** BC30451  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  参照元のステートメントで名前のスペルを確認します。 Visual Basic では、大文字と小文字が、スペルにその他の違いは、完全に別の名前と見なされます。 アンダースコア (`_`) も名前の一部であり、スペルに含まれます。  
  
2.  メンバー アクセス演算子があることを確認 (`.`) オブジェクトとメンバーの間です。 たとえば、 <xref:System.Windows.Forms.TextBox> という名前の `TextBox1`コントロールがある場合、このコントロールの <xref:System.Windows.Forms.TextBoxBase.Text%2A> プロパティにアクセスするには、「 `TextBox1.Text`」と入力する必要があります。 代わりに「 `TextBox1Text`」と入力した場合、別の名前と見なされます。  
  
3.  スペルが正しい、オブジェクト メンバー アクセスの構文が正しい場合は、要素が宣言されていることを確認します。 詳細については、次を参照してください。[要素の宣言](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)です。  
  
4.  プログラミング要素が宣言されている場合は、スコープ内にあることを確認します。 参照元のステートメントがプログラミング要素が宣言領域の外側にある場合は、要素名を修飾する必要があります。 詳細については、次を参照してください。 [Visual Basic におけるスコープ](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)です。  
  
## <a name="see-also"></a>関連項目  
 [宣言と定数の概要](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
