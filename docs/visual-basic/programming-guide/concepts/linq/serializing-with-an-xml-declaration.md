---
title: "XML 宣言 (Visual Basic) でシリアル化 |Microsoft ドキュメント"
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
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
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
ms.openlocfilehash: 50707da956df593f176764bed94adfc6aec3dfa5
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="092fa-102">XML 宣言 (Visual Basic) でシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="092fa-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="092fa-103">このトピックでは、シリアル化を実行する際に XML 宣言を生成するかどうかを制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="092fa-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="092fa-104">XML 宣言の生成</span><span class="sxs-lookup"><span data-stu-id="092fa-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="092fa-105">シリアル化、<xref:System.IO.File>または<xref:System.IO.TextWriter>を使用して、<xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>メソッドまたは<xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>メソッドは、XML 宣言を生成します</xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.IO.TextWriter></xref:System.IO.File>。</span><span class="sxs-lookup"><span data-stu-id="092fa-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> method generates an XML declaration.</span></span> <span data-ttu-id="092fa-106">シリアル化すると、 <xref:System.Xml.XmlWriter>、ライターの設定 (で指定されている、<xref:System.Xml.XmlWriterSettings>オブジェクト)、XML 宣言を生成するかどうかどうかを決定します</xref:System.Xml.XmlWriterSettings></xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="092fa-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="092fa-107">`ToString` メソッドを使用して文字列にシリアル化する場合、生成される XML には XML 宣言は含まれません。</span><span class="sxs-lookup"><span data-stu-id="092fa-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="092fa-108">XML 宣言付きのシリアル化</span><span class="sxs-lookup"><span data-stu-id="092fa-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="092fa-109">次の例を作成し、 <xref:System.Xml.Linq.XElement>、ファイルにドキュメントを保存し、ファイルをコンソールに出力します</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="092fa-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="092fa-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="092fa-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="092fa-111">XML 宣言なしでのシリアル化</span><span class="sxs-lookup"><span data-stu-id="092fa-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="092fa-112">次の例<xref:System.Xml.Linq.XElement><xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter></xref:System.Xml.Linq.XElement>を保存する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="092fa-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="092fa-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="092fa-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="092fa-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="092fa-114">See Also</span></span>  
 [<span data-ttu-id="092fa-115">XML ツリーをシリアル化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="092fa-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
