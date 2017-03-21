---
title: "方法: 分割およびコード (Visual Basic) 内のステートメントを連結する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb._
dev_langs:
- VB
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores, in code
- statements [Visual Basic], line continuation in
- line breaks, in code
- line-continuation character
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 840036a91f430f72e0258b8be466770f2855a58f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>方法: コード内でステートメントを分割および連結する (Visual Basic)
コードを記述する場合は、コード エディターでを水平方向にスクロールを必要とするステートメントが長くなりも作成できます。 方法は、これには影響しませんが、コードを実行、困難の作成者やその他のユーザーをモニターされているとおり、コードを読み取る。 このような場合は、単一の長いステートメントを複数の行に分割を検討してください。  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>複数の行に単一のステートメントを分割するには  
  
-   アンダー スコアは、行連結文字を使用 (`_`)、行を分割する時点。 アンダースコアは、スペースの直後、および行終端記号 (キャリッジ リターン) の直前に指定する必要があります。  
  
    > [!NOTE]
    >  場合によっては、行連結文字を省略した場合、Visual Basic コンパイラに暗黙的には引き続きステートメント次のコード行にします。 行連結文字を省略できます構文要素については、「暗黙的な行継続」を参照してください[ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)します。  
  
     次の例では、ステートメントは末尾行連結文字の&4; つの行が最後の行に分割されます。  
  
     [!code-vb[VbVbcnConventions&#20;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     このシーケンスを使用して、コード読みやすく、オンラインとタイミングを印刷します。  
  
     行連結文字は、行の最後の文字である必要があります。 アイテムと同じ行に、それをフォローできません。  
  
     行連結文字を使用するに関していくつかの制限があります。たとえば、引数の名前の途中では使用できません。 行連結文字で、引数リストを分割することができますが、個々 の引数の名前が残す必要があります。  
  
     行連結文字を使用して、コメントを続行できません。 コンパイラは、特別な意味のコメント内の文字を調べるしません。 複数行にコメントを記述する場合は、コメント記号を繰り返します (`'`)&1; 行にします。  
  
 推奨される方法は、別々 の行に各ステートメントを配置することが[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]同じ行に複数のステートメントを配置することもできます。  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>同じ行に複数のステートメントを配置するには  
  
-   ステートメントをコロンで区切ります (`:`)、次の例のようにします。  
  
     [!code-vb[VbVbcnConventions&#10;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
