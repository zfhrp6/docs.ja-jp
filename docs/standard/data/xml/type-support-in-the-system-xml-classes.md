---
title: "System.Xml クラスでの型のサポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 14821ef78f20d1ff303afacb42415e4017a92742
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="398af-102">System.Xml クラスでの型のサポート</span><span class="sxs-lookup"><span data-stu-id="398af-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="398af-103">.NET Framework Version 2.0 では、コアの XML クラスが強化され、型サポート機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="398af-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="398af-104"><xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、および <xref:System.Xml.XPath.XPathNavigator> クラスには、XML スキーマ型と共通言語ランタイム (CLR) 型の間の変換機能を含む型サポート機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="398af-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="398af-105">.NET Framework Version 2.0 では、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、および <xref:System.Xml.XPath.XPathNavigator> クラスが強化され、型サポート機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="398af-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
-   <span data-ttu-id="398af-106"><xref:System.Xml.XmlReader>と<xref:System.Xml.XPath.XPathNavigator>各クラスに含まれる、 **SchemaInfo**ノードでスキーマ情報を返します。</span><span class="sxs-lookup"><span data-stu-id="398af-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
-   <span data-ttu-id="398af-107">**ReadContentAs**と**ReadElementContentAs**とメソッドを<xref:System.Xml.XmlReader>クラスは、テキスト値を読み取るし、1 つのメソッドの呼び出しでの CLR 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="398af-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
-   <span data-ttu-id="398af-108"><xref:System.Xml.XmlWriter.WriteValue%2A> クラスの <xref:System.Xml.XmlWriter> メソッドは、XML の書き出し時に、CLR 型を XML スキーマ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="398af-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
-   <span data-ttu-id="398af-109">**ValueAs**と<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>プロパティを<xref:System.Xml.XPath.XPathNavigator>クラスは、ノードの値を返すし、1 つのメソッドの呼び出しでの CLR 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="398af-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="398af-110">.NET Framework Version 1.0 では、XML スキーマ型と CLR 型の間の変換に <xref:System.Xml.XmlConvert> クラスが必要でした。</span><span class="sxs-lookup"><span data-stu-id="398af-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="398af-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="398af-111">In This Section</span></span>  
 [<span data-ttu-id="398af-112">CLR 型に XML データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="398af-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="398af-113">XML データ型から CLR 型への既定のマッピングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="398af-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="398af-114">XML 型サポート実装に関するメモ</span><span class="sxs-lookup"><span data-stu-id="398af-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="398af-115">型サポート実装の詳細のいくつかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="398af-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="398af-116">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="398af-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="398af-117">XML スキーマ型と CLR 型の間の変換に <xref:System.Xml.XmlConvert> クラスを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="398af-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="398af-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="398af-118">Related Sections</span></span>  
 [<span data-ttu-id="398af-119">XPathNavigator による XML データに型指定された厳密にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="398af-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
