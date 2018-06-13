---
title: XML コメント リテラル (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 60c354215c627683fd6c69d9ca66fc115c26ccda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603939"
---
# <a name="xml-comment-literal-visual-basic"></a>XML コメント リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XComment>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`<!--`|必須。 XML コメントの開始を示します。|  
|`content`|必須。 XML コメントに表示されるテキストです。 2 つのハイフン (-) または終了タグの横にあるハイフンで end の系列を含めることはできません。|  
|`-->`|必須。 XML コメントの終了を示します。|  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XComment> オブジェクト。  
  
## <a name="remarks"></a>コメント  
 XML コメント リテラルにはドキュメントの内容が含まれていませんドキュメントに関する情報が含まれます。 XML コメントのセクションでは、シーケンス「:」で終了します。 これは、次の点を意味します。  
  
-   埋め込み式の区切り記号が有効な XML コメントのコンテンツであるので、XML コメント リテラルの埋め込み式を使うことはできません。  
  
-   XML コメントのセクションでは入れ子にできないため`content`"-->"の値を含めることはできません。  
  
 XML コメント リテラルは、変数に割り当てることができますか、XML 要素リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルは、行継続文字を使用せず複数行にまたがることができます。 この機能を使用すると、XML ドキュメントの内容をコピーし、Visual Basic プログラムに直接貼り付けることができます。  
  
 Visual Basic コンパイラでは、XML コメント リテラルを変換への呼び出しに、<xref:System.Xml.Linq.XComment.%23ctor%2A>コンス トラクターです。  
  
## <a name="example"></a>例  
 次の例では、「これは、コメント」テキストを含む XML コメントを作成します。  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XComment>  
 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
