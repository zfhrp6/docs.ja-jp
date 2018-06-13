---
title: シリアル化時の空白の維持3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 48e654c2b7992544cdc2c67dfc5a5136d6a9bb33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329882"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="3be63-102">シリアル化時の空白の維持</span><span class="sxs-lookup"><span data-stu-id="3be63-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="3be63-103">このトピックでは、XML ツリーをシリアル化するときに空白を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3be63-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="3be63-104">一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。</span><span class="sxs-lookup"><span data-stu-id="3be63-104">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="3be63-105">書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。</span><span class="sxs-lookup"><span data-stu-id="3be63-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="3be63-106">これが [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="3be63-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="3be63-107">もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="3be63-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="3be63-108">場合によっては、このインデントを一切変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3be63-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="3be63-109">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。</span><span class="sxs-lookup"><span data-stu-id="3be63-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="3be63-110">XML ツリーをシリアル化するメソッドの空白に関する動作</span><span class="sxs-lookup"><span data-stu-id="3be63-110">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="3be63-111"><xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq.XDocument> クラスにある次のメソッドは、XML ツリーをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="3be63-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="3be63-112">XML ツリーは、ファイル、<xref:System.IO.TextReader>、または <xref:System.Xml.XmlReader> にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="3be63-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="3be63-113">`ToString` メソッドは、文字列にシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="3be63-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="3be63-114">メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取らない場合は、シリアル化された XML が書式設定 (インデント) されます。</span><span class="sxs-lookup"><span data-stu-id="3be63-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="3be63-115">この場合、XML ツリー内の意味のない空白はすべて破棄されます。</span><span class="sxs-lookup"><span data-stu-id="3be63-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="3be63-116">メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取る場合は、シリアル化された XML が書式設定 (インデント) されないことを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3be63-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="3be63-117">この場合、XML ツリー内の空白はすべて維持されます。</span><span class="sxs-lookup"><span data-stu-id="3be63-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be63-118">参照</span><span class="sxs-lookup"><span data-stu-id="3be63-118">See Also</span></span>  
 [<span data-ttu-id="3be63-119">XML ツリーのシリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="3be63-119">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
