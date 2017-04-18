---
title: "0 から始まるとします。Visual Basic における文字列の&1; から始まるアクセス |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6cd2cab888bf336151ed26968119431f4ffc75f4
ms.lasthandoff: 03/13/2017

---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>0 から始まるとします。Visual Basic における文字列の&1; から始まるアクセス
このトピックでは比較方法[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]と[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]文字列内の文字へのアクセスを提供します。 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]が常に、文字列内の文字への&0; から始まるアクセスを提供[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]関数によって、0 から始まり、1 つベースのアクセスを提供します。  
  
## <a name="one-based"></a>1 から始まる  
 たとえば&1; から始まるの[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]機能を検討してください、`Mid`関数です。 部分文字列が開始する、位置 1 から始まる文字位置を示す引数を受け取る。 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Substring%2A?displayProperty=fullName>メソッドは、文字のインデックスで部分文字列を開始するには、文字列の位置の 0 から開始します</xref:System.String.Substring%2A?displayProperty=fullName>。 したがって、文字列"ABCDE"がある場合、個々 の文字の番号と 1,2,3,4,5 で使用するため、`Mid`関数が 0,1,2,3,4 で使用するため、<xref:System.String.Substring%2A?displayProperty=fullName>メソッド</xref:System.String.Substring%2A?displayProperty=fullName>。  
  
## <a name="zero-based"></a>0 から始まる  
 たとえば、0 から始まるの[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]機能を検討してください、`Split`関数です。 文字列を分割し、これらの部分文字列を含む配列を返します。 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Split%2A?displayProperty=fullName>もメソッドは文字列を分割し、部分文字列を含む配列を返します</xref:System.String.Split%2A?displayProperty=fullName>。 `Split`関数と<xref:System.String.Split%2A>メソッドの戻り値[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]配列、必要がある&0; から始まる</xref:System.String.Split%2A>。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:System.String.Substring%2A></xref:System.String.Substring%2A>   
 <xref:System.String.Split%2A></xref:System.String.Split%2A>   
 [Visual Basic における文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
