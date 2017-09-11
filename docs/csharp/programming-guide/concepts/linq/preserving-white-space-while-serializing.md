---
title: "シリアル化時の空白の維持3"
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
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
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
ms.openlocfilehash: eed3f2a2627fb5901692d67095efbdd5c874b54c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="540fe-102">シリアル化時の空白の維持</span><span class="sxs-lookup"><span data-stu-id="540fe-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="540fe-103">このトピックでは、XML ツリーをシリアル化するときに空白を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="540fe-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="540fe-104">一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。</span><span class="sxs-lookup"><span data-stu-id="540fe-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="540fe-105">書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。</span><span class="sxs-lookup"><span data-stu-id="540fe-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="540fe-106">これが [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="540fe-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="540fe-107">もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="540fe-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="540fe-108">場合によっては、このインデントを一切変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="540fe-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="540fe-109">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。</span><span class="sxs-lookup"><span data-stu-id="540fe-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="540fe-110">XML ツリーをシリアル化するメソッドの空白に関する動作</span><span class="sxs-lookup"><span data-stu-id="540fe-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="540fe-111"><xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq.XDocument> クラスにある次のメソッドは、XML ツリーをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="540fe-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="540fe-112">XML ツリーは、ファイル、<xref:System.IO.TextReader>、または <xref:System.Xml.XmlReader> にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="540fe-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="540fe-113">`ToString` メソッドは、文字列にシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="540fe-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName>  
  
 <span data-ttu-id="540fe-114">メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取らない場合は、シリアル化された XML が書式設定 (インデント) されます。</span><span class="sxs-lookup"><span data-stu-id="540fe-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="540fe-115">この場合、XML ツリー内の意味のない空白はすべて破棄されます。</span><span class="sxs-lookup"><span data-stu-id="540fe-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="540fe-116">メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取る場合は、シリアル化された XML が書式設定 (インデント) されないことを指定できます。</span><span class="sxs-lookup"><span data-stu-id="540fe-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="540fe-117">この場合、XML ツリー内の空白はすべて維持されます。</span><span class="sxs-lookup"><span data-stu-id="540fe-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="540fe-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="540fe-118">See Also</span></span>  
 [<span data-ttu-id="540fe-119">XML ツリーのシリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="540fe-119">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)

