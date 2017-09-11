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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 6361ef29b88b4a05b774cf67ca0f3832a8e214fa
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="08066-102">方法 : ファイル、文字列、またはストリームから XML を読み込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08066-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="08066-103">作成する[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)し、いくつかのメソッドを使用して、ファイル、文字列、ストリームなどの外部ソースからコンテンツを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="08066-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="08066-104">次の例では、これらのメソッドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08066-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="08066-105">ファイルから XML を読み込む</span><span class="sxs-lookup"><span data-stu-id="08066-105">To load XML from a file</span></span>  
  
-   <span data-ttu-id="08066-106">XML リテラルなどを設定する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクトを使用して、ファイルから、`Load`メソッド</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="08066-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="08066-107">このメソッドは、入力として、ファイル パス、テキスト ストリームまたは XML ストリームを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="08066-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="08066-108">次のコード例の使用を示しています、<xref:System.Xml.Linq.XDocument.Load%28System.String%29>に挿入する方法、<xref:System.Xml.Linq.XDocument>テキスト ファイルから XML を持つオブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument.Load%28System.String%29>。</span><span class="sxs-lookup"><span data-stu-id="08066-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     <span data-ttu-id="08066-109">[!code-vb[VbXMLSamples #&43;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="08066-109">[!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]</span></span>  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="08066-110">文字列から XML を読み込む</span><span class="sxs-lookup"><span data-stu-id="08066-110">To load XML from a string</span></span>  
  
-   <span data-ttu-id="08066-111">XML リテラルなどを設定する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>、文字列からオブジェクトを使用することができます、`Parse`メソッド</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="08066-111">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="08066-112">次のコード例の使用を示しています、<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName>に挿入する方法、<xref:System.Xml.Linq.XDocument>文字列から XML を持つオブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="08066-112">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     <span data-ttu-id="08066-113">[!code-vb[VbXMLSamples #&47;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="08066-113">[!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]</span></span>  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="08066-114">ストリームから XML を読み込む</span><span class="sxs-lookup"><span data-stu-id="08066-114">To load XML from a stream</span></span>  
  
-   <span data-ttu-id="08066-115">XML リテラルなどを設定する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>ストリームからオブジェクトを使用することができます、`Load`メソッドまたは<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName>メソッド</xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="08066-115">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="08066-116">次のコード例の使用を示しています、<xref:System.Xml.Linq.XNode.ReadFrom%2A>に挿入する方法、 <xref:System.Xml.Linq.XDocument>XML ストリームから XML を持つオブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XNode.ReadFrom%2A>。</span><span class="sxs-lookup"><span data-stu-id="08066-116">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 <span data-ttu-id="08066-117">[!code-vb[VbXMLSamples&#46;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="08066-117">[!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08066-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="08066-118">See Also</span></span>  
 <span data-ttu-id="08066-119"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="08066-119"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="08066-120"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="08066-120"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="08066-121"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="08066-121"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="08066-122"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="08066-122"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="08066-123"><xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="08066-123"><xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="08066-124"> [XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="08066-124"> [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="08066-125"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="08066-125"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="08066-126"> [Visual Basic で XML を操作します。](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="08066-126"> [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)</span></span>

