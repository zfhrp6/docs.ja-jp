---
title: '方法: コード内でステートメントを分割および連結する (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
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
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 6bca3d62cb3e886ee08b9169d63d4c3a38247f3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651019"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>方法: コード内でステートメントを分割および連結する (Visual Basic)
コードを書くときにも必要になるは、水平方向にスクロール コード エディターでステートメントが長くなりを作成する可能性があります。 方法は、これには影響しませんが、コードの実行、困難の作成者やその他のユーザーをモニターに表示されるようにコードを読み取る。 このような場合は、単一の長いステートメントを複数の行に分割することを検討してください。  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>複数の行に単一のステートメントを分割するには  
  
-   行連結文字、つまりアンダー スコアを使用して (`_`)、行を分割する時点。 アンダースコアは、スペースの直後、および行終端記号 (キャリッジ リターン) の直前に指定する必要があります。  
  
    > [!NOTE]
    >  場合によっては、行連結文字を省略した場合、Visual Basic コンパイラは暗黙的に続行ステートメント コードの次の行にします。 行連結文字を省略できる構文要素の一覧を参照してください「暗黙的な行の連結」[ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)です。  
  
     次の例では、ステートメントは行連結文字をすべて終了して 4 つの行が最後の行に分割されます。  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     このシーケンスを使用して、コードを見やすく、オンラインとときに出力されます。  
  
     行連結文字は、行の最後の文字である必要があります。 他の何らかの同じ行にたどってすることはできません。  
  
     行連結文字を使用するに関していくつかの制限があります。たとえば、引数名の途中では使用できません。 行連結文字の引数リストを中断することができますが、個々 の引数の名前はそのまま保持する必要があります。  
  
     行連結文字を使用してコメントを続行することはできません。 コンパイラには、特別な意味のコメント内の文字を確認しません。 複数行にコメントを記述する場合は、コメント記号を繰り返します (`'`) 行ごとにします。  
  
 行ごとに各ステートメントを配置することは推奨される方法が、Visual Basic することもできますが同じ直線上に複数のステートメントを配置します。  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>同じ行に複数のステートメントを配置するには  
  
-   ステートメントをコロンで区切ります (`:`)、次の例のようにします。  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
