---
title: "XML CDATA リテラル (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
dev_langs:
- VB
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
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
ms.openlocfilehash: 24e52bf203ff3df57e26137da24abcc2cb7e8e20
ms.lasthandoff: 03/13/2017

---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XCData>オブジェクト</xref:System.Xml.Linq.XCData>。  
  
## <a name="syntax"></a>構文  
  
```  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>指定項目  
 `<![CDATA[`  
 必須です。 XML CDATA セクションの開始を示します。  
  
 `content`  
 必須です。 XML CDATA セクションに表示されるテキストの内容。  
  
 `]]>`  
 必須です。 セクションの終了を示します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XCData>オブジェクト</xref:System.Xml.Linq.XCData>。  
  
## <a name="remarks"></a>コメント  
 XML CDATA セクションには、未加工のテキストが含まれているは解析されずに、それを含んでいる xml が含まれます。 XML CDATA セクションには、任意のテキストを含めることができます。 これには、予約済み XML 文字が含まれます。 XML CDATA セクションは、シーケンスで終わる"] >"です。 これは、次の点を意味します。  
  
-   組み込み式の区切り記号が有効な XML CDATA コンテンツであるので、リテラル XML CDATA で埋め込み式を使用できません。  
  
-   XML CDATA セクションは入れ子にできないため`content`値を含めることはできません"] >"です。  
  
 リテラル XML CDATA を変数を割り当てたり、XML 要素リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルでは、複数行にまたがることができますが、行継続文字を使用しません。 これにより、XML ドキュメントからコンテンツをコピーして貼り付けに直接、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムです。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、XML CDATA リテラルを変換への呼び出しに、<xref:System.Xml.Linq.XCData.%23ctor%2A>コンス トラクター</xref:System.Xml.Linq.XCData.%23ctor%2A> 。  
  
## <a name="example"></a>例  
 次の例では、CDATA セクションのテキストを含む"リテラルに含めることができる\<XML > タグ"です。  
  
 [!code-vb[VbXMLSamples 第&23;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XCData></xref:System.Xml.Linq.XCData>   
 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
