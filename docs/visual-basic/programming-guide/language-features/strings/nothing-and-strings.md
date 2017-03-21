---
title: "Visual Basic の nothing と文字列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 56fc47ba2523825224aae3264e965d462cf4c3b6
ms.lasthandoff: 03/13/2017

---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic の Nothing と文字列
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ランタイムと[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]評価`Nothing`が異なるとなる文字列。  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic ランタイムおよび .NET Framework  
 次に例を示します。  
  
 [!code-vb[VbVbalrStrings #&47;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]共通言語ランタイムは通常評価`Nothing`として空の文字列 ("") です。 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]ただし、していないと、文字列操作を実行する試みが行われるたびに、例外をスロー`Nothing`します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
