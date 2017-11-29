---
title: "方法 : ファイル、文字列、またはストリームから XML を読み込む (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 572e34b1cd4813fad35e6afaf2ec3d0d9dac470a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="400c7-102">方法 : ファイル、文字列、またはストリームから XML を読み込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="400c7-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="400c7-103">作成することができます[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)し、ファイル、文字列またはストリームなど、外部ソースの内容といくつかのメソッドを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="400c7-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="400c7-104">これらのメソッドは、次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="400c7-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="400c7-105">ファイルから XML を読み込む</span><span class="sxs-lookup"><span data-stu-id="400c7-105">To load XML from a file</span></span>  
  
-   <span data-ttu-id="400c7-106">XML リテラルなどの設定に、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクトを使用して、ファイルから、`Load`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="400c7-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="400c7-107">このメソッドは、入力として、ファイル パス、テキスト ストリームまたは XML ストリームを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="400c7-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="400c7-108">次のコード例の使用を示しています、<xref:System.Xml.Linq.XDocument.Load%28System.String%29>に挿入する方法、<xref:System.Xml.Linq.XDocument>テキスト ファイルから XML を持つオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="400c7-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="400c7-109">文字列から XML を読み込む</span><span class="sxs-lookup"><span data-stu-id="400c7-109">To load XML from a string</span></span>  
  
-   <span data-ttu-id="400c7-110">XML リテラルなどの設定に、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト、文字列から使用する、`Parse`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="400c7-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="400c7-111">次のコード例の使用を示しています、<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>に挿入する方法、<xref:System.Xml.Linq.XDocument>文字列から xml オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="400c7-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="400c7-112">ストリームから XML を読み込む</span><span class="sxs-lookup"><span data-stu-id="400c7-112">To load XML from a stream</span></span>  
  
-   <span data-ttu-id="400c7-113">XML リテラルなどの設定に、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>ストリームからオブジェクトを使用することができます、`Load`メソッドまたは<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="400c7-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="400c7-114">次のコード例の使用を示しています、<xref:System.Xml.Linq.XNode.ReadFrom%2A>に挿入する方法、 <xref:System.Xml.Linq.XDocument> XML ストリームから XML を持つオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="400c7-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="400c7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="400c7-115">See Also</span></span>  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="400c7-116">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="400c7-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="400c7-117">XML</span><span class="sxs-lookup"><span data-stu-id="400c7-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="400c7-118">Visual Basic での XML の操作</span><span class="sxs-lookup"><span data-stu-id="400c7-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
