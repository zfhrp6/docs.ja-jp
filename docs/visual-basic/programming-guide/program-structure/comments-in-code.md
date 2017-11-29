---
title: "コード内のコメント (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cf1aa755c479c73c64951f80ab0b76985507da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="comments-in-code-visual-basic"></a>コード内のコメント (Visual Basic)
コード例にはコメント記号 (`'`) がしばしば見られます。 このシンボルに指示、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラをそれに続くテキストを無視するか、*コメント*です。 コメントは、コードを読むユーザーに役立つように追加される簡単な説明です。  
  
 プロシージャの先頭に、そのプロシージャの機能の特性 (何を実行するか) について説明する簡単なコメントを常に配置するのは、推奨されるプログラミング方法です。 コードを作成した本人にとっても、コードを調べる他人にとっても、この説明は役に立ちます。 実装の詳細 (プロシージャの実行手順) は、機能の特性を説明するコメントとは別に記述する必要があります。 実装の詳細を記述に入れる場合は、関数を更新するときにその説明も更新してください。  
  
 同じ行のステートメントの後にコメントを入れたり、1 行全体をコメントにしたりできます。 両方の例を次のコードに示します。  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 コメントを複数行に記述する必要がある場合は、以下に例を示すとおりに、各行にコメント記号を記述します。  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## <a name="commenting-guidelines"></a>コメントのガイドライン  
 次の表は、どの種類のコメントをコードのセクションの前に配置できるかに関する一般的なガイドラインを示しています。 これらは推奨であり、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ではコメントの追加に規則はありません。 コードの作成者自身およびコードを読む他のユーザーに最適な内容を記述してください。  
  
|||  
|---|---|  
|コメント タイプ|コメントの説明|  
|目的|プロシージャが行う内容 (手順ではありません) を説明します。|  
|外部からの影響|各外部変数、コントロール、開いているファイル、またはプロシージャからアクセスされるその他の要素の一覧を示します。|  
|効果|影響を受ける外部変数、コントロール、またはファイル、およびその効果 (明白でない場合のみ) の一覧を示します。|  
|受け取る値|引数の目的を指定します。|  
|戻り値|プロシージャから返される値について説明します。|  
  
 次のことに留意してください。  
  
-   重要な変数を宣言する場合は、宣言した変数の用途を説明するためのインライン コメントを必ず前に配置します。  
  
-   コメントには複雑な実装の詳細だけを記述して済むように、変数、コントロール、およびプロシージャにはわかりやすい名前を付けます。  
  
-   同じ行の行連結シーケンスの後にコメントを付けることはできません。  
  
 追加するか、コードのブロックのコメント記号を削除するには、1 つまたは複数の行のコードを選択し、選択、**コメント**(![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) および**コメント解除**(![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) ボタンを**編集**ツールバー。  
  
> [!NOTE]
>  テキストの前に `REM` キーワードを付けて、コードにコメントを追加することもできます。 ただし、`'`シンボルと**コメント**/**コメント解除**ボタンは簡単に使用し、小さい領域とメモリを必要とします。  
  
## <a name="see-also"></a>関連項目  
 [XML コメントに、コードの説明](http://msdn.microsoft.com/magazine/dd722812.aspx)  
 [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [REM ステートメント](../../../visual-basic/language-reference/statements/rem-statement.md)
