---
title: Visual Basic における文字列操作メソッドの種類
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 11903e067c064f129ecd2df80244edb6741c73be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648695"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Visual Basic における文字列操作メソッドの種類
いくつかの方法を分析し、文字列の操作があります。 Visual Basic 言語の一部である一部のメソッドと他の人は気にせずに、`String`クラスです。  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic 言語と .NET Framework  
 Visual Basic のメソッドは、言語固有の関数として使用されます。 これらは、コードで修飾しないで使用できる可能性があります。 次の例は、Visual Basic の文字列操作コマンドの一般的な使用を示しています。  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 この例では、`Mid`関数を直接操作を実行する`aString`に値を代入し、`bString`です。  
  
 Visual Basic の文字列操作メソッドの一覧は、次を参照してください。[文字列操作の概要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)です。  
  
### <a name="shared-methods-and-instance-methods"></a>共有メソッドとインスタンス メソッド  
 メソッドを使って文字列を操作することも、`String`クラスです。 内のメソッドの 2 種類があります`String`:*共有*メソッドおよび*インスタンス*メソッドです。  
  
#### <a name="shared-methods"></a>共有メソッド  
 共有メソッドに由来するメソッド、`String`クラス自体および操作するには、そのクラスのインスタンスは必要ありません。 これらのメソッドは、クラスの名前で修飾することができます (`String`) のインスタンスではなく、`String`クラスです。 例えば:  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 前の例で、<xref:System.String.Copy%2A?displayProperty=nameWithType>メソッドは、静的メソッドを式に対して機能することが指定され、結果の値を割り当てます`bString`です。  
  
#### <a name="instance-methods"></a>インスタンス メソッド  
 インスタンス メソッド、これに対し、によって生じる特定のインスタンスの`String`インスタンス名で修飾する必要があります。 例えば:  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 この例では、<xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドは、メソッドのインスタンスの`String`(つまり、 `aString`)。 操作を実行`aString`し、その値を割り当てます`bString`です。  
  
 詳細については、ドキュメントを参照して、<xref:System.String>クラスです。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
