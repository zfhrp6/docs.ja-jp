---
title: "方法: ファイル、文字列、または (Visual Basic) のストリームから XML を読み込む |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 242c8b79cbe1329b6f53e9fd4e5495d4a157e08c
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>方法 : ファイル、文字列、またはストリームから XML を読み込む (Visual Basic)
作成する[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)し、いくつかのメソッドを使用して、ファイル、文字列、ストリームなどの外部ソースからコンテンツを読み込みます。 次の例では、これらのメソッドが表示されます。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>ファイルから XML を読み込む  
  
-   XML リテラルなどを設定する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクトを使用して、ファイルから、`Load`メソッド</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。 このメソッドは、入力として、ファイル パス、テキスト ストリームまたは XML ストリームを受け取ることができます。  
  
     次のコード例の使用を示しています、<xref:System.Xml.Linq.XDocument.Load%28System.String%29>に挿入する方法、<xref:System.Xml.Linq.XDocument>テキスト ファイルから XML を持つオブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument.Load%28System.String%29>。  
  
     [!code-vb[VbXMLSamples #&43;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a>文字列から XML を読み込む  
  
-   XML リテラルなどを設定する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>、文字列からオブジェクトを使用することができます、`Parse`メソッド</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。  
  
     次のコード例の使用を示しています、<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName>に挿入する方法、<xref:System.Xml.Linq.XDocument>文字列から XML を持つオブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName>。  
  
     [!code-vb[VbXMLSamples #&47;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a>ストリームから XML を読み込む  
  
-   XML リテラルなどを設定する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>ストリームからオブジェクトを使用することができます、`Load`メソッドまたは<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName>メソッド</xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。  
  
 次のコード例の使用を示しています、<xref:System.Xml.Linq.XNode.ReadFrom%2A>に挿入する方法、 <xref:System.Xml.Linq.XDocument>XML ストリームから XML を持つオブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XNode.ReadFrom%2A>。  
  
 [!code-vb[VbXMLSamples&#46;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName>   
 [XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Visual Basic で XML を操作します。](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)

