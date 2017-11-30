---
title: "XML ドキュメントの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a0806e34cfbf7c8e0b5ba995ca4876b8d10405e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-creation"></a><span data-ttu-id="d0fb6-102">XML ドキュメントの作成</span><span class="sxs-lookup"><span data-stu-id="d0fb6-102">XML Document Creation</span></span>
<span data-ttu-id="d0fb6-103">XML ドキュメントは、2 とおりの方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="d0fb6-104">作成する方法の 1 つは、 **XmlDocument**パラメーターなしでします。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="d0fb6-105">その他の方法は、作成する、 **XmlDocument**を XmlNameTable をパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="d0fb6-106">次の例は、新しい、空を作成する方法を示しています。 **XmlDocument**パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="d0fb6-107">ドキュメントを作成した後は、文字列からのデータを読み込むことができますストリーム、URL、テキスト リーダー、または**XmlReader**派生したクラスを使用して、**読み込む**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="d0fb6-108">別のロード メソッドも、 **LoadXML**メソッドで、文字列から XML を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="d0fb6-109">詳細については、さまざまな**ロード**メソッドを参照してください[DOM に XML ドキュメントを読み取る](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)です。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="d0fb6-110">呼ばれるクラスがある、 **XmlNameTable**です。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="d0fb6-111">このクラスは、分解された文字列オブジェクトのテーブルです。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="d0fb6-112">このテーブルを使用すると、パーサーは XML ドキュメント内で繰り返されているすべての要素名と属性名に同じ文字列オブジェクトを使用でき、効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="d0fb6-113">**XmlNameTable**ドキュメントが上記のように作成され、ドキュメントが読み込まれるときに、属性と要素の名前に読み込まれるときに自動的に作成します。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="d0fb6-114">使用して新しいドキュメントを作成するには、ネーム テーブルを持つドキュメントが既にある場合、それらの名前が別のドキュメントで役に立つ、**ロード**を受け取るメソッド、 **XmlNameTable**をパラメーターとして。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="d0fb6-115">既存の機能を使用してこのメソッドを使用して、ドキュメントが作成されると、 **XmlNameTable**のすべての属性と既に読み込まれます。 その他のドキュメントから要素。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="d0fb6-116">XmlNameTable を使用すると、要素名と属性名を効率的に比較できます。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="d0fb6-117">詳細については、 **XmlNameTable**を参照してください[比較 XmlNameTable によるオブジェクトの](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)します。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="d0fb6-118">リファレンスについては、次を参照してください。<xref:System.Xml.XmlNameTable>です。</span><span class="sxs-lookup"><span data-stu-id="d0fb6-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0fb6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0fb6-119">See Also</span></span>  
 [<span data-ttu-id="d0fb6-120">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="d0fb6-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
