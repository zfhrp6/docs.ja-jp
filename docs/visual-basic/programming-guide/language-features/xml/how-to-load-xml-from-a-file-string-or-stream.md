---
title: '方法 : ファイル、文字列、またはストリームから XML を読み込む (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 241f6552e46d7689b42a409ba44bc747984773ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>方法 : ファイル、文字列、またはストリームから XML を読み込む (Visual Basic)
作成することができます[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)し、ファイル、文字列またはストリームなど、外部ソースの内容といくつかのメソッドを使用して設定します。 これらのメソッドは、次の例に示します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>ファイルから XML を読み込む  
  
-   XML リテラルなどの設定に、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクトを使用して、ファイルから、`Load`メソッドです。 このメソッドは、入力として、ファイル パス、テキスト ストリームまたは XML ストリームを受け取ることができます。  
  
     次のコード例の使用を示しています、<xref:System.Xml.Linq.XDocument.Load%28System.String%29>に挿入する方法、<xref:System.Xml.Linq.XDocument>テキスト ファイルから XML を持つオブジェクト。  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a>文字列から XML を読み込む  
  
-   XML リテラルなどの設定に、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト、文字列から使用する、`Parse`メソッドです。  
  
     次のコード例の使用を示しています、<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>に挿入する方法、<xref:System.Xml.Linq.XDocument>文字列から xml オブジェクトです。  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a>ストリームから XML を読み込む  
  
-   XML リテラルなどの設定に、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>ストリームからオブジェクトを使用することができます、`Load`メソッドまたは<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>メソッドです。  
  
 次のコード例の使用を示しています、<xref:System.Xml.Linq.XNode.ReadFrom%2A>に挿入する方法、 <xref:System.Xml.Linq.XDocument> XML ストリームから XML を持つオブジェクト。  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
