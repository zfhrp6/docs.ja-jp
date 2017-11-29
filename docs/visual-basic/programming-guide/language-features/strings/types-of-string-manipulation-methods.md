---
title: "Visual Basic における文字列操作メソッドの種類"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b437be4a6f4a0cc9d5a4d21291a80c9cb8fffcd3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic における文字列操作メソッドの種類
いくつかの方法を分析し、文字列の操作があります。 一部であるメソッドの一部、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]言語、およびその他の人は気にせずに、`String`クラスです。  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic 言語と .NET Framework  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]メソッドは、言語固有の関数として使用されます。 これらは、コードで修飾しないで使用できる可能性があります。 次の例では、一般的な使用、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]文字列操作コマンド。  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 この例では、`Mid`関数を直接操作を実行する`aString`に値を代入し、`bString`です。  
  
 Visual Basic の文字列操作メソッドの一覧は、次を参照してください。[文字列操作の概要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)です。  
  
### <a name="shared-methods-and-instance-methods"></a>共有メソッドとインスタンス メソッド  
 メソッドを使って文字列を操作することも、`String`クラスです。 内のメソッドの 2 種類があります`String`:*共有*メソッドおよび*インスタンス*メソッドです。  
  
#### <a name="shared-methods"></a>共有メソッド  
 共有メソッドに由来するメソッド、`String`クラス自体および操作するには、そのクラスのインスタンスは必要ありません。 これらのメソッドは、クラスの名前で修飾することができます (`String`) のインスタンスではなく、`String`クラスです。 例:  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 前の例で、<xref:System.String.Copy%2A?displayProperty=nameWithType>メソッドは、静的メソッドを式に対して機能することが指定され、結果の値を割り当てます`bString`です。  
  
#### <a name="instance-methods"></a>インスタンス メソッド  
 インスタンス メソッド、これに対し、によって生じる特定のインスタンスの`String`インスタンス名で修飾する必要があります。 例:  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 この例では、<xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドは、メソッドのインスタンスの`String`(つまり、 `aString`)。 操作を実行`aString`し、その値を割り当てます`bString`です。  
  
 詳細については、ドキュメントを参照して、<xref:System.String>クラスです。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
