---
title: XML CDATA リテラル (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 999531d8146748fe491255663f0d2d17d056bcd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603835"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XCData>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>指定項目  
 `<![CDATA[`  
 必須。 XML CDATA セクションの開始を示します。  
  
 `content`  
 必須。 XML CDATA セクションに表示されるテキストの内容。  
  
 `]]>`  
 必須。 セクションの終了を示します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XCData> オブジェクト。  
  
## <a name="remarks"></a>コメント  
 XML CDATA セクションを含む未加工のテキストが含まれている場合は、それを含む XML を解析できません。 XML CDATA セクションには、任意のテキストを含めることができます。 これには、予約済み XML 文字が含まれます。 XML CDATA セクションは、シーケンスで終わる"] >"です。 これは、次の点を意味します。  
  
-   埋め込み式の区切り記号が有効な XML の CDATA コンテンツであるので、XML CDATA リテラルの埋め込み式を使うことはできません。  
  
-   XML CDATA セクションでは入れ子にできないため`content`値を含めることはできません"] >"です。  
  
 リテラル XML CDATA を変数を割り当てたり、XML 要素リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルでは、複数行にまたがることができますが、行継続文字を使用しません。 これにより、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。  
  
 Visual Basic コンパイラでは、XML CDATA リテラルを変換への呼び出しに、<xref:System.Xml.Linq.XCData.%23ctor%2A>コンス トラクターです。  
  
## <a name="example"></a>例  
 次の例では、テキストを含む CDATA セクション"リテラルに含めることができる\<XML > タグ"です。  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XCData>  
 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
