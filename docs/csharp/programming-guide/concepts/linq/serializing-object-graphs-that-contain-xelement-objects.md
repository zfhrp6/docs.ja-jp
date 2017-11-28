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
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a>XElement オブジェクトを含むオブジェクト グラフのシリアル化 (C#)
このトピックでは、<xref:System.Xml.Linq.XElement> 型のオブジェクトへの参照が含まれているオブジェクト グラフのシリアル化機能について説明します。 この種のシリアル化を円滑に行うために、<xref:System.Xml.Linq.XElement> は <xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装しています。  
  
 シリアル化を実装しているのは <xref:System.Xml.Linq.XElement> クラスだけであることに注意してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[方法: XmlSerializer を使用してシリアル化する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化する方法について説明します。|  
|[方法: DataContractSerializer を使用してシリアル化する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化する方法について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [高度な LINQ to XML プログラミング (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
