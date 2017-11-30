---
title: "方法: ステートメントへのラベル付け (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190ec9fc2392e6e4adae9b2b612edd69d73cedfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-label-statements-visual-basic"></a>方法: ステートメントへのラベル付け (Visual Basic)
ステートメント ブロックは、コロンで区切られたコードの行が構成をされています。 行の識別文字列または整数に続くコードと呼ばれます*というラベルの付いた*です。 ステートメント ラベルはなどを識別に使用するステートメントを使用するコードの行をマークするために使用`On Error Goto`です。  
  
 ラベルとして使用できるは、有効な Visual Basic 識別子 — などのプログラミング要素を識別するもの、または整数リテラル。 ラベルは、ソース コードの行の先頭に置く必要があり、後にするかどうかが続くことは、ステートメントが同じ直線上に関係なく、コロン必要があります。  
  
 コンパイラは、行の先頭が任意に定義済みの識別子と一致するかどうかをチェックして、ラベルを識別します。 そうでない場合、コンパイラはラベルであると想定します。  
  
 ラベルは、独自の宣言領域があるし、その他の識別子に干渉しません。 ラベルのスコープは、メソッドの本体です。 ラベルの宣言は、あいまいな場合でも優先されます。  
  
> [!NOTE]
>  ラベルは、メソッドの中の実行可能なステートメントでのみ使用できます。  
  
### <a name="to-label-a-line-of-code"></a>コードの行にラベル付け  
  
-   その後にソース コードの行の先頭に、コロン、識別子を配置します。  
  
     たとえば、次のコード行は、ラベルが付いた`Jump`と`120`、それぞれします。  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
