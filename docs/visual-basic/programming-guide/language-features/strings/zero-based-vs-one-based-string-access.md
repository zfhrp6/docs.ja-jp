---
title: "0 から始まる vs です。Visual Basic で文字列の 1 つに基づいたアクセス"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>0 から始まる vs です。Visual Basic で文字列の 1 つに基づいたアクセス
このトピックでは比較方法[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]と[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]文字列の文字へのアクセスを提供します。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]常に対し、文字列の文字に 0 から始まるアクセスを提供[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]関数によって、および 0 から始まる 1 ベースのアクセスを提供します。  
  
## <a name="one-based"></a>1 から始まる  
 1 から始まるの例については[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]機能を考慮してください、`Mid`関数。 位置 1 から始まる、部分文字列を開始する文字位置を示す引数を受け取る。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドは、文字のインデックスを開始するには、部分文字列を文字列 0 の位置から開始します。 したがって、文字列"ABCDE"がある場合、個々 の文字の番号と 1,2,3,4,5 で使用するため、`Mid`関数が 0,1,2,3,4 で使用するため、<xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドです。  
  
## <a name="zero-based"></a>0 から始まる  
 0 から始まるの例については[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]機能を考慮してください、`Split`関数。 文字列を分割し、各部分文字列を含む配列を返します。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType>もメソッドは文字列を分割し、部分文字列を含む配列を返します。 `Split`関数と<xref:System.String.Split%2A>メソッドの戻り値[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]配列、する必要がある 0 から始まる。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
