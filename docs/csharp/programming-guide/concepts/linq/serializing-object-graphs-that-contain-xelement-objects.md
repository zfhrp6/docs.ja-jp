---
title: "XElement オブジェクトを含むオブジェクト グラフのシリアル化 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b7da4429360beb20fa304b592020d48666fe732
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="060c5-102">XElement オブジェクトを含むオブジェクト グラフのシリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="060c5-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="060c5-103">このトピックでは、<xref:System.Xml.Linq.XElement> 型のオブジェクトへの参照が含まれているオブジェクト グラフのシリアル化機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="060c5-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="060c5-104">この種のシリアル化を円滑に行うために、<xref:System.Xml.Linq.XElement> は <xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="060c5-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="060c5-105">シリアル化を実装しているのは <xref:System.Xml.Linq.XElement> クラスだけであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="060c5-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="060c5-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="060c5-106">In This Section</span></span>  
  
|<span data-ttu-id="060c5-107">トピック</span><span class="sxs-lookup"><span data-stu-id="060c5-107">Topic</span></span>|<span data-ttu-id="060c5-108">説明</span><span class="sxs-lookup"><span data-stu-id="060c5-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="060c5-109">方法: XmlSerializer を使用してシリアル化する (C#)</span><span class="sxs-lookup"><span data-stu-id="060c5-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="060c5-110"><xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="060c5-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="060c5-111">方法: DataContractSerializer を使用してシリアル化する (C#)</span><span class="sxs-lookup"><span data-stu-id="060c5-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="060c5-112"><xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="060c5-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="060c5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="060c5-113">See Also</span></span>  
 [<span data-ttu-id="060c5-114">高度な LINQ to XML プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="060c5-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
