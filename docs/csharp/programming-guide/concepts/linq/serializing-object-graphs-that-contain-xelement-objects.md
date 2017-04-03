---
title: "XElement オブジェクトを含むオブジェクト グラフのシリアル化 (C#) | Microsoft Docs"
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
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 752092f7455fa0a10efcaa41166b66ff1f87b16e
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a>XElement オブジェクトを含むオブジェクト グラフのシリアル化 (C#)
このトピックでは、<xref:System.Xml.Linq.XElement> 型のオブジェクトへの参照を含むオブジェクト グラフをシリアル化する機能について説明します。 この種のシリアル化を円滑に行うために、<xref:System.Xml.Linq.XElement> は <xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装しています。  
  
 シリアル化を実装しているのは <xref:System.Xml.Linq.XElement> クラスだけであることに注意してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[方法: XmlSerializer を使用してシリアル化する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化する方法について説明します。|  
|[方法: DataContractSerializer を使用してシリアル化する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化する方法について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [高度な LINQ to XML プログラミング (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
