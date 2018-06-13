---
title: ファイル、Textwriter、および XmlWriters3 にシリアル化します。
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: ff877e3c800bd1409d796fb68d651175d3602e34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645318"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="34009-102">ファイル、TextWriter、および XmlWriter へのシリアル化</span><span class="sxs-lookup"><span data-stu-id="34009-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="34009-103">XML ツリーは、<xref:System.IO.File>、<xref:System.IO.TextWriter>、または <xref:System.Xml.XmlWriter> にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="34009-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="34009-104"><xref:System.Xml.Linq.XDocument> メソッドを使用すると、<xref:System.Xml.Linq.XElement> や `ToString` など任意の XML コンポーネントを文字列にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="34009-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="34009-105">文字列にシリアル化するときに書式設定されないようにするには、<xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="34009-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="34009-106">ファイルにシリアル化するときの既定の動作では、結果の XML ドキュメントの書式設定 (インデント設定) が行われます。</span><span class="sxs-lookup"><span data-stu-id="34009-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="34009-107">インデントを設定する場合、XML ツリー内の意味のない空白は保持されません。</span><span class="sxs-lookup"><span data-stu-id="34009-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="34009-108">書式を設定してシリアル化するには、<xref:System.Xml.Linq.SaveOptions> を引数として受け取らない次のメソッドのいずれかのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="34009-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="34009-109">インデントを設定せず、XML ツリー内の意味のない空白を保持できるようにするには、<xref:System.Xml.Linq.SaveOptions> を引数として受け取る次のメソッドのいずれかのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="34009-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="34009-110">例については、該当するリファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="34009-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34009-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="34009-111">See Also</span></span>  
 [<span data-ttu-id="34009-112">(Visual Basic) の XML ツリーをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="34009-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
