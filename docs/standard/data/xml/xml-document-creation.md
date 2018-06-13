---
title: XML ドキュメントの作成
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ab7632966cd2a0087a8bdc1d452d02543edbec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572789"
---
# <a name="xml-document-creation"></a><span data-ttu-id="2d30d-102">XML ドキュメントの作成</span><span class="sxs-lookup"><span data-stu-id="2d30d-102">XML Document Creation</span></span>
<span data-ttu-id="2d30d-103">XML ドキュメントは、2 とおりの方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="2d30d-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="2d30d-104">1 つは、パラメーターを使用せずに **XmlDocument** を作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="2d30d-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="2d30d-105">もう 1 つは、**XmlDocument** の作成時に XmlNameTable をパラメーターとして渡す方法です。</span><span class="sxs-lookup"><span data-stu-id="2d30d-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="2d30d-106">パラメーターを使用せず、新しい空の **XmlDocument** を作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="2d30d-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="2d30d-107">ドキュメントを作成すると、**Load** メソッドを使用することにより、文字列、ストリーム、URL、テキスト リーダー、または **XmlReader** から派生したクラスのデータを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="2d30d-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="2d30d-108">文字列から XML を読み込む **LoadXML** メソッドという読み込みメソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="2d30d-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="2d30d-109">各種の **Load** メソッドの詳細については、「[XML ドキュメントの DOM への読み込み](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d30d-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="2d30d-110">**XmlNameTable** というクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="2d30d-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="2d30d-111">このクラスは、分解された文字列オブジェクトのテーブルです。</span><span class="sxs-lookup"><span data-stu-id="2d30d-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="2d30d-112">このテーブルを使用すると、パーサーは XML ドキュメント内で繰り返されているすべての要素名と属性名に同じ文字列オブジェクトを使用でき、効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="2d30d-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="2d30d-113">**XmlNameTable** は、前述のようにドキュメントの作成時に自動的に作成され、ドキュメントの読み込み時に属性名および要素名と共に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="2d30d-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="2d30d-114">名前テーブルのあるドキュメントが既に存在し、それらの名前が別のドキュメントで役に立つ場合は、**XmlNameTable** をパラメーターとしてとる **Load** メソッドを使用して新しいドキュメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2d30d-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="2d30d-115">このメソッドによるドキュメントの作成時には、別のドキュメントからの既存の **XmlNameTable** と、既に読み込まれているすべての属性および要素が使われます。</span><span class="sxs-lookup"><span data-stu-id="2d30d-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="2d30d-116">XmlNameTable を使用すると、要素名と属性名を効率的に比較できます。</span><span class="sxs-lookup"><span data-stu-id="2d30d-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="2d30d-117">**XmlNameTable** の詳細については、「[XmlNameTable によるオブジェクトの比較](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d30d-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="2d30d-118"><xref:System.Xml.XmlNameTable>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d30d-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d30d-119">参照</span><span class="sxs-lookup"><span data-stu-id="2d30d-119">See Also</span></span>  
 [<span data-ttu-id="2d30d-120">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="2d30d-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
