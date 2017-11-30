---
title: "XmlNameTable によるオブジェクトの比較"
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
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd1a3bad69499b4804299adecabad3a43b5eab1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="694b3-102">XmlNameTable によるオブジェクトの比較</span><span class="sxs-lookup"><span data-stu-id="694b3-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="694b3-103">**XmlDocuments**を作成すると、そのドキュメント用に作成された名前のテーブルがあります。</span><span class="sxs-lookup"><span data-stu-id="694b3-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="694b3-104">属性と要素の名前が入れられます、ドキュメントに XML が読み込まれるか、新しい要素や属性を作成、ときに、 **XmlNameTable**です。</span><span class="sxs-lookup"><span data-stu-id="694b3-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="694b3-105">作成することも、 **XmlDocument**既存**NameTable**別のドキュメントからです。</span><span class="sxs-lookup"><span data-stu-id="694b3-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="694b3-106">ときに**XmlDocuments**を受け取るコンス トラクターで作成された、 **XmlNameTable**パラメーター、ドキュメントがノード名、名前空間、およびに既に格納されているプレフィックスへのアクセス、 **XmlNameTable**です。</span><span class="sxs-lookup"><span data-stu-id="694b3-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="694b3-107">どのような方法で名前テーブルと名前が読み込まれたとしても、いったんテーブルに名前が格納されると、文字列比較によってではなく、オブジェクト比較を利用して高速に名前を比較できます。</span><span class="sxs-lookup"><span data-stu-id="694b3-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="694b3-108">名前のテーブルを使用する文字列を追加することも、<xref:System.Xml.NameTable.Add%2A>です。</span><span class="sxs-lookup"><span data-stu-id="694b3-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="694b3-109">次のコード サンプルは、名前のテーブルを作成し、文字列を示します**MyString**テーブルに追加されています。</span><span class="sxs-lookup"><span data-stu-id="694b3-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="694b3-110">その後、 **XmlDocument**そのテーブル、および内の要素と属性名を使用して作成された**Myfile.xml**既存の名前テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="694b3-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 <span data-ttu-id="694b3-111">ドキュメントを作成し、ドキュメントに 2 つの新しい要素を追加し、それらの要素をドキュメントの名前テーブルにも追加して、名前のオブジェクト比較を実行するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="694b3-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 <span data-ttu-id="694b3-112">上記のように 2 つのドキュメント間で名前テーブルが渡される状況は、同じタイプのドキュメントを繰り返し処理する場合によく発生します。たとえば、XML スキーマ定義言語 (XSD) スキーマまたはドキュメント型定義 (DTD) に準拠し、同じ文字列が繰り返し使われる発注ドキュメントを e コマース サイトで処理する場合などです。</span><span class="sxs-lookup"><span data-stu-id="694b3-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="694b3-113">このような場合は、同じ要素名が複数のドキュメントに現れるため、同じ名前テーブルを使用することによってパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="694b3-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="694b3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="694b3-114">See Also</span></span>  
 [<span data-ttu-id="694b3-115">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="694b3-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
