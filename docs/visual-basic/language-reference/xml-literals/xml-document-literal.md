---
title: XML ドキュメント リテラル (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: bd2ecfb93cfcdb7cf9c115f9a44ac47dd74c4b53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604355"
---
# <a name="xml-document-literal-visual-basic"></a>XML ドキュメント リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XDocument>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`encoding`|任意。 リテラルのテキスト エンコード ドキュメントの宣言を使用します。|  
|`standalone`|任意。 リテラル テキスト。 "Yes"にする必要がありますまたは"no"です。|  
|`piCommentList`|任意。 XML 処理命令や XML コメントの一覧です。 次の形式になります。<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> 各`piComment`次のいずれかになります。<br /><br /> -   [XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)です。<br />-   [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)です。|  
|`rootElement`|必須。 ドキュメントのルート要素です。 形式では、次のいずれかです。<br /><br /> <ul><li>[XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)です。</li><li>形式の式を埋め込む`<%=` `elementExp` `%>`です。 `elementExp`次のいずれかを返します。<br /><br /> <ul><li><xref:System.Xml.Linq.XElement> オブジェクト。</li><li>いずれかを含むコレクション<xref:System.Xml.Linq.XElement>オブジェクトと任意の数の<xref:System.Xml.Linq.XProcessingInstruction>と<xref:System.Xml.Linq.XComment>オブジェクト。</li></ul></li></ul><br /> 詳細については、次を参照してください。 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)です。|  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XDocument> オブジェクト。  
  
## <a name="remarks"></a>コメント  
 XML ドキュメント リテラルは、リテラルの先頭に XML 宣言によって識別されます。 各 XML ドキュメント リテラルには、XML のルート要素の 1 つだけ必要がありますが、任意の数 XML 処理命令や XML コメントの持つことができます。  
  
 XML ドキュメント リテラルは、XML 要素ではできません。  
  
> [!NOTE]
>  XML リテラルは、行継続文字を使用せず複数行にまたがることができます。 これにより、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。  
  
 Visual Basic コンパイラでは、リテラルの XML ドキュメントを変換への呼び出しに、<xref:System.Xml.Linq.XDocument.%23ctor%2A>と<xref:System.Xml.Linq.XDeclaration.%23ctor%2A>コンス トラクターです。  
  
## <a name="example"></a>例  
 次の例では、XML 宣言、処理命令、コメント、および別の要素を格納する要素のある XML ドキュメントを作成します。  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
