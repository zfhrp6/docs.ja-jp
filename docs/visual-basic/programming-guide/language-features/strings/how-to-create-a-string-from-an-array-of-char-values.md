---
title: "方法: Char 値の配列から文字列を作成する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06e5c6923c26f3cb84b38475d6680523853d727d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>方法: Char 値の配列から文字列を作成する (Visual Basic)
この例では、個別の文字から文字列"abcd"を作成します。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このメソッドには、特別な要件はありません。  
  
 構文`"a"c`, が、1 つ、`c`引用符で囲まれた 1 文字に依存して、文字リテラルを作成するために使用します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 Null 文字 (に相当`Chr(0)`) 文字列が発生する予期しない結果文字列を使用する場合。 Null 文字は、文字列に含まれますが、null 文字以降には、一部の状況では表示されません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.String>  
 [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
