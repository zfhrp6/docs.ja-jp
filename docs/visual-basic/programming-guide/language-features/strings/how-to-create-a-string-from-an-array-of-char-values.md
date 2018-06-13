---
title: '方法: Char 値の配列から文字列を作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 104b329011d69e10a2926f31ce5d296759a3cce8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647181"
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
