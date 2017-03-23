---
title: "XML ドキュメント リテラル (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
dev_langs:
- VB
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
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
ms.openlocfilehash: 5d64faddad66eba4029969654388ba7df17e5854
ms.lasthandoff: 03/13/2017

---
# <a name="xml-document-literal-visual-basic"></a>XML ドキュメント リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument>。  
  
## <a name="syntax"></a>構文  
  
```  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`encoding`|省略可能です。 リテラル テキストをエンコード ドキュメントの宣言を使用します。|  
|`standalone`|省略可能です。 リテラル テキスト。 "Yes"にする必要がありますまたは"no"です。|  
|`piCommentList`|省略可能です。 XML 処理命令と XML コメントの一覧です。 次の形式を取ります。<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> 各`piComment`次のいずれかになります。<br /><br /> -   [XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)します。<br />-   [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)します。|  
|`rootElement`|必須です。 ドキュメントのルート要素です。 形式は、次のいずれかを示します。<br /><br /> <ul><li>[XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。</li><li>形式の式を埋め込む`<%=` `elementExp` `%>`します。 `elementExp`次のいずれかを返します。<br /><br /> <ul><li><xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</li><li>1 つ含まれているコレクション<xref:System.Xml.Linq.XElement>オブジェクトと任意の数の<xref:System.Xml.Linq.XProcessingInstruction>と<xref:System.Xml.Linq.XComment>オブジェクト</xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XElement>。</li></ul></li></ul><br /> 詳細については、次を参照してください。 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)します。|  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument>。  
  
## <a name="remarks"></a>コメント  
 XML ドキュメント リテラルは、リテラルの先頭に XML 宣言によって識別されます。 各 XML ドキュメント リテラルにはただ&1; つの XML ルート要素を設定する必要がありますが、任意の数の XML 処理命令と XML のコメントがあることができます。  
  
 XML ドキュメント リテラルは、XML 要素にはできません。  
  
> [!NOTE]
>  XML リテラルは、行継続文字を使用せず複数の行にまたがることができます。 これにより、XML ドキュメントからコンテンツをコピーして貼り付けに直接、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムです。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、リテラル XML ドキュメントを変換への呼び出しに、<xref:System.Xml.Linq.XDocument.%23ctor%2A>と<xref:System.Xml.Linq.XDeclaration.%23ctor%2A>コンス トラクター</xref:System.Xml.Linq.XDeclaration.%23ctor%2A> </xref:System.Xml.Linq.XDocument.%23ctor%2A> 。  
  
## <a name="example"></a>例  
 次の例では、XML 宣言、処理命令、コメント、および別の要素を含む要素には、XML ドキュメントを作成します。  
  
 [!code-vb[VbXMLSamples #&30;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>   
 <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>   
 <xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument>   
 [XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)   
 [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
