---
title: "XML コメント リテラル (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralComment
dev_langs:
- VB
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: 19
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
ms.openlocfilehash: 88cfb984be42345ae1e5c998cf82aa1415d2455e
ms.lasthandoff: 03/13/2017

---
# <a name="xml-comment-literal-visual-basic"></a>XML コメント リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XComment>オブジェクト</xref:System.Xml.Linq.XComment>。  
  
## <a name="syntax"></a>構文  
  
```  
<!-- content -->  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`<!--`|必須です。 XML コメントの開始を示します。|  
|`content`|必須です。 XML コメントに表示されるテキストです。 一連の&2; つのハイフン (-) または終了タグの横にあるハイフンを使用して end を含めることはできません。|  
|`-->`|必須です。 XML コメントの終了を示します。|  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XComment>オブジェクト</xref:System.Xml.Linq.XComment>。  
  
## <a name="remarks"></a>コメント  
 ドキュメントの内容を含まない XML コメント リテラルドキュメントに関する情報が含まれます。 XML コメントのセクションでは、「-->」シーケンスで終了します。 これは、次の点を意味します。  
  
-   組み込み式の区切り記号が有効な XML コメントの内容であるので、XML コメント リテラルで、組み込み式を使用できません。  
  
-   XML コメントのセクションでは入れ子にできないため`content`「-->」の値を含めることはできません。  
  
 XML コメント リテラルは、変数に割り当てることができますか、XML 要素リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルは、行継続文字を使用せず複数の行にまたがることができます。 この機能を使用すると、XML ドキュメントからコンテンツをコピーして貼り付けに直接、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムです。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、XML コメント リテラルを変換への呼び出しに、<xref:System.Xml.Linq.XComment.%23ctor%2A>コンス トラクター</xref:System.Xml.Linq.XComment.%23ctor%2A> 。  
  
## <a name="example"></a>例  
 次の例では、"This is コメント"テキストを表す XML コメントを作成します。  
  
 [!code-vb[VbXMLSamples&#9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>   
 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
