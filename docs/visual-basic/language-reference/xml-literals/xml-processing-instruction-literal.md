---
title: "XML 処理命令リテラル (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
dev_langs:
- VB
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
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
ms.openlocfilehash: 2903297fa22cd8dc10bc4b12abaa754d4f6284f2
ms.lasthandoff: 03/13/2017

---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML 処理命令リテラル (Visual Basic)
リテラルを表す、<xref:System.Xml.Linq.XProcessingInstruction>オブジェクト</xref:System.Xml.Linq.XProcessingInstruction>。  
  
## <a name="syntax"></a>構文  
  
```  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>指定項目  
 `<?`  
 必須です。 XML 処理命令リテラルの開始を示します。  
  
 `piName`  
 必須です。 アプリケーションを示す処理命令のターゲットを名前します。 "Xml"または"XML"で始まることはできません。  
  
 `piData`  
 省略可能です。 アプリケーションの対象とする方法を示す文字列`piName`XML ドキュメントを処理する必要があります。  
  
 `?>`  
 必須です。 処理命令の終了を示します。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XProcessingInstruction>オブジェクト</xref:System.Xml.Linq.XProcessingInstruction>。  
  
## <a name="remarks"></a>コメント  
 XML 処理命令リテラルは、アプリケーションが、XML ドキュメントを処理する方法を示しています。 アプリケーションに XML ドキュメントが読み込まれると、アプリケーションは、ドキュメントを処理する方法を決定する XML 処理命令をチェックできます。 アプリケーションの意味を解釈する`piName`と`piData`です。  
  
 XML ドキュメント リテラルは、XML 処理命令の次のような構文を使用します。 詳細については、次を参照してください。 [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)します。  
  
> [!NOTE]
>  `piName`のため、XML 1.0 仕様これらの id を確保するため、要素が文字列"xml"または"XML"で始まることはできません。  
  
 変数には、XML 処理命令リテラルを代入したり、XML ドキュメント リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルは、行継続文字をしなくても複数行にまたがることができます。 これにより、XML ドキュメントからコンテンツをコピーして貼り付けに直接、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムです。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、XML 処理命令リテラルを変換への呼び出しに、<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>コンス トラクター</xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> 。  
  
## <a name="example"></a>例  
 次の例では、XML ドキュメントのスタイル シートを識別する処理命令を作成します。  
  
 [!code-vb[VbXMLSamples #&28;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>   
 [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
