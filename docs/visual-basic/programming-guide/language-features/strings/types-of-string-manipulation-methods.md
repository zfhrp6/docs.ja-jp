---
title: "Visual Basic で文字列操作メソッドの種類 |Microsoft ドキュメント"
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
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
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
ms.openlocfilehash: 349cfdb3e31225f6aeba90ac29aa1c66e37c7e11
ms.lasthandoff: 03/13/2017

---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic における文字列操作メソッドの種類
分析し、文字列の操作をいくつかの方法があります。 一部である一部のメソッド、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]言語、およびその他のユーザーに内在する、`String`クラスです。  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic 言語と .NET Framework  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]メソッドは、言語固有の関数として使用されます。 これらは、コードで修飾しないで使用できる場合があります。 次の例の一般的な使用方法を示しています、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列操作コマンド。  
  
 [!code-vb[VbVbalrStrings #&44;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 この例では、`Mid`関数に対して直接操作を実行する`aString`に値を代入し、`bString`します。  
  
 Visual Basic の文字列操作メソッドの一覧は、次を参照してください。[文字列操作の概要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)します。  
  
### <a name="shared-methods-and-instance-methods"></a>共有メソッドとインスタンス メソッド  
 メソッドを使って文字列を操作することも、`String`クラスです。 におけるメソッドの&2; つの種類がある`String`:*共有*メソッドと*インスタンス*メソッドです。  
  
#### <a name="shared-methods"></a>共有メソッド  
 共有メソッドに由来するメソッド、`String`クラス自身と動作するには、そのクラスのインスタンスは必要ありません。 これらのメソッドは、クラスの名前で修飾することができます (`String`) のインスタンスではなく、`String`クラスです。 例:  
  
 [!code-vb[VbVbalrStrings #&45;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 上記の例では、<xref:System.String.Copy%2A?displayProperty=fullName>メソッドが静的メソッドで、式に対して機能することが指定されに結果として得られる値を代入`bString`</xref:System.String.Copy%2A?displayProperty=fullName>。  
  
#### <a name="instance-methods"></a>インスタンス メソッド  
 特定のインスタンスのインスタンス メソッドがこれに対し、原因`String`インスタンス名で修飾する必要があります。 例:  
  
 [!code-vb[VbVbalrStrings&#46;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 この例では、<xref:System.String.Substring%2A?displayProperty=fullName>メソッドは、メソッドのインスタンスの`String`(つまり、 `aString`).</xref:System.String.Substring%2A?displayProperty=fullName> 操作を実行`aString`にその値を代入し、`bString`します。  
  
 詳細については、<xref:System.String>クラス</xref:System.String>のドキュメントを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
