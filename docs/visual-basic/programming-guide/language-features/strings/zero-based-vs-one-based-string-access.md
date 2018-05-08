---
title: 0 から始まる vs です。Visual Basic で文字列の 1 つに基づいたアクセス
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a0a42f72d94adf1c10865374017fa61e833df40f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>0 から始まる vs です。Visual Basic で文字列の 1 つに基づいたアクセス
このトピックでどの Visual Basic を比較し、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]文字列の文字へのアクセスを提供します。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]常に、文字列の文字に 0 から始まるアクセスを提供し、Visual Basic は、関数によって、0 から始まると 1 つベースのアクセスを提供します。  
  
## <a name="one-based"></a>1 から始まる  
 1 から始まる Visual Basic の関数の例は、次を検討してください。、`Mid`関数。 位置 1 から始まる、部分文字列を開始する文字位置を示す引数を受け取る。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドは、文字のインデックスを開始するには、部分文字列を文字列 0 の位置から開始します。 したがって、文字列"ABCDE"がある場合、個々 の文字の番号と 1,2,3,4,5 で使用するため、`Mid`関数が 0,1,2,3,4 で使用するため、<xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドです。  
  
## <a name="zero-based"></a>0 から始まる  
 0 から始まる Visual Basic の関数の例は、次を検討してください。、`Split`関数。 文字列を分割し、各部分文字列を含む配列を返します。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType>もメソッドは文字列を分割し、部分文字列を含む配列を返します。 `Split`関数と<xref:System.String.Split%2A>メソッドの戻り値[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]配列、する必要がある 0 から始まる。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
