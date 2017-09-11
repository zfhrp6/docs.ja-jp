---
title: "ファイル、Textwriter、および XmlWriters3 へのシリアル化 |Microsoft ドキュメント"
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
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f8f8672004b0704b00ff60e5b58256f664bcbd82
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="46617-102">ファイル、TextWriter、および XmlWriter へのシリアル化</span><span class="sxs-lookup"><span data-stu-id="46617-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="46617-103">XML ツリーをシリアル化することができます、 <xref:System.IO.File>、 <xref:System.IO.TextWriter>、または<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="46617-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="46617-104">任意の XML コンポーネントをシリアル化することができますを含む<xref:System.Xml.Linq.XDocument>と<xref:System.Xml.Linq.XElement>を使用して文字列に、`ToString`メソッド</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="46617-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="46617-105">文字列にシリアル化するときに書式設定されないようにする場合は、使用、<xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>メソッド</xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="46617-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="46617-106">ファイルにシリアル化するときの既定動作では、(インデント設定)、結果の XML ドキュメントの書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="46617-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="46617-107">インデントを設定する場合、XML ツリー内の意味のない空白は保持されません。</span><span class="sxs-lookup"><span data-stu-id="46617-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="46617-108">書式設定を含む、シリアル化する受け取らない次のメソッドのオーバー ロードのいずれかの操作を使用して<xref:System.Xml.Linq.SaveOptions>を引数として:</xref:System.Xml.Linq.SaveOptions></span><span class="sxs-lookup"><span data-stu-id="46617-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <span data-ttu-id="46617-109"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="46617-109"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="46617-110"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="46617-110"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="46617-111">インデントを設定せず、XML ツリー内の余分な空白を保存するオプションを設定する場合は、次のメソッドのオーバー ロードのいずれかを使用<xref:System.Xml.Linq.SaveOptions>を引数として:</xref:System.Xml.Linq.SaveOptions></span><span class="sxs-lookup"><span data-stu-id="46617-111">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <span data-ttu-id="46617-112"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="46617-112"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="46617-113"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="46617-113"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="46617-114">例については、該当するリファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="46617-114">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46617-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="46617-115">See Also</span></span>  
 [<span data-ttu-id="46617-116">XML ツリーをシリアル化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46617-116">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
