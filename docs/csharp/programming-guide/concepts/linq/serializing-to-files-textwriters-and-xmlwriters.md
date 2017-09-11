---
title: "ファイル、TextWriter、および XmlWriter へのシリアル化1"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 94a2b3e16703496d2e59b08677395db30d944d56
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="61a7e-102">ファイル、TextWriter、および XmlWriter へのシリアル化</span><span class="sxs-lookup"><span data-stu-id="61a7e-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="61a7e-103">XML ツリーは、<xref:System.IO.File>、<xref:System.IO.TextWriter>、または <xref:System.Xml.XmlWriter> にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="61a7e-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="61a7e-104"><xref:System.Xml.Linq.XDocument> メソッドを使用すると、<xref:System.Xml.Linq.XElement> や `ToString` など任意の XML コンポーネントを文字列にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="61a7e-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="61a7e-105">文字列にシリアル化するときに書式設定されないようにするには、<xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="61a7e-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="61a7e-106">ファイルにシリアル化するときの既定の動作では、結果の XML ドキュメントの書式設定 (インデント設定) が行われます。</span><span class="sxs-lookup"><span data-stu-id="61a7e-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="61a7e-107">インデントを設定する場合、XML ツリー内の意味のない空白は保持されません。</span><span class="sxs-lookup"><span data-stu-id="61a7e-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="61a7e-108">書式を設定してシリアル化するには、<xref:System.Xml.Linq.SaveOptions> を引数として受け取らない次のメソッドのいずれかのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="61a7e-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 <span data-ttu-id="61a7e-109">インデントを設定せず、XML ツリー内の意味のない空白を保持できるようにするには、<xref:System.Xml.Linq.SaveOptions> を引数として受け取る次のメソッドのいずれかのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="61a7e-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 <span data-ttu-id="61a7e-110">例については、該当するリファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="61a7e-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a7e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="61a7e-111">See Also</span></span>  
 [<span data-ttu-id="61a7e-112">XML ツリーのシリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="61a7e-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)

