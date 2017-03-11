---
title: "Comments in Code (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Uncomment button"
  - "REM statement"
  - "comments, in code"
  - "comments, Visual Basic code"
  - "Comment button"
  - "buttons, Uncomment"
  - "buttons, Comment"
  - "code comments, Visual Basic"
  - "Visual Basic code, comments"
  - "comments"
  - "code comments"
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Comments in Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コード例にはコメント記号 \(`'`\) がしばしば見られます。  この記号は、後続のテキスト \([!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]コメント\) を無視するように  *コンパイラに指示します。* コメントは、コードを読むユーザーに役立つように追加される簡単な説明です。  
  
 プロシージャの先頭に、そのプロシージャの機能の特性 \(何を実行するか\) について説明する簡単なコメントを常に配置するのは、推奨されるプログラミング方法です。  コードを作成した本人にとっても、コードを調べる他人にとっても、この説明は役に立ちます。  実装の詳細 \(プロシージャの実行手順\) は、機能の特性を説明するコメントとは別に記述する必要があります。  実装の詳細を記述に入れる場合は、関数を更新するときにその説明も更新してください。  
  
 同じ行のステートメントの後にコメントを入れたり、1 行全体をコメントにしたりできます。  両方の例を次のコードに示します。  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/comments-in-code_1.vb)]  
  
 コメントを複数行に記述する必要がある場合は、以下に例を示すとおりに、各行にコメント記号を記述します。  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/comments-in-code_2.vb)]  
  
## コメントのガイドライン  
 次の表は、どの種類のコメントをコードのセクションの前に配置できるかに関する一般的なガイドラインを示しています。  これらは推奨であり、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ではコメントの追加に規則はありません。  コードの作成者自身およびコードを読む他のユーザーに最適な内容を記述してください。  
  
|||  
|-|-|  
|コメント タイプ|コメントの説明|  
|目的|プロシージャが行う内容 \(手順ではありません\) を説明します。|  
|外部からの影響|各外部変数、コントロール、開いているファイル、またはプロシージャからアクセスされるその他の要素の一覧を示します。|  
|効果|影響を受ける外部変数、コントロール、またはファイル、およびその効果 \(明白でない場合のみ\) の一覧を示します。|  
|受け取る値|引数の目的を指定します。|  
|戻り値|プロシージャから返される値について説明します。|  
  
 次のことに留意してください。  
  
-   重要な変数を宣言する場合は、宣言した変数の用途を説明するためのインライン コメントを必ず前に配置します。  
  
-   コメントには複雑な実装の詳細だけを記述して済むように、変数、コントロール、およびプロシージャにはわかりやすい名前を付けます。  
  
-   同じ行の行連結シーケンスの後にコメントを付けることはできません。  
  
 コード ブロックのコメント記号を追加または削除するには、1 行以上のコードを選択し、**\[編集\]** ツール バーの **\[選択範囲のコメント\]** ボタン \(![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.png "vaCommentButton")\) または **\[選択範囲のコメント解除\]** ボタン \(![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.png "vaUncommentButton")\) をクリックします。  
  
> [!NOTE]
>  テキストの前に `REM` キーワードを付けて、コードにコメントを追加することもできます。  ただし、`'` 記号および **\[選択範囲のコメント\]** と **\[選択範囲のコメントの解除\]** の各ボタンの方が使いやすく、必要なスペースとメモリが少なくて済みます。  
  
## 参照  
 [XML コメントを使用したコードのドキュメント化](http://msdn.microsoft.com/magazine/dd722812.aspx)   
 [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)   
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)   
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [REM Statement](../../../visual-basic/language-reference/statements/rem-statement.md)