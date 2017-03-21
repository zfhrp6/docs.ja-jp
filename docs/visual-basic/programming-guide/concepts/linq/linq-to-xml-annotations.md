---
title: "LINQ to XML Annotations2 |Microsoft ドキュメント"
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
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1f2e5bea1cde74548daa1697b6a0a819e3eba3e4
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-annotations"></a>LINQ to XML の注釈
内の注釈[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]任意の型の任意のオブジェクトを XML ツリー内の任意の XML コンポーネントに関連付けることができます。  
  
 など、XML コンポーネントに注釈を追加する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>を呼び出す、<xref:System.Xml.Linq.XObject.AddAnnotation%2A>メソッド</xref:System.Xml.Linq.XObject.AddAnnotation%2A></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>。 注釈は型によって取得します。  
  
 注釈は XML 情報セットの一部ではないことに注意してください。注釈はシリアル化も逆シリアル化もされません。  
  
## <a name="methods"></a>メソッド  
 注釈を操作する場合は、次のメソッドを使用できます。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A></xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>の注釈の一覧にオブジェクトを追加します。|  
|<xref:System.Xml.Linq.XObject.Annotation%2A></xref:System.Xml.Linq.XObject.Annotation%2A>|<xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>から指定した型の最初の注釈オブジェクトを取得します。|  
|<xref:System.Xml.Linq.XObject.Annotations%2A></xref:System.Xml.Linq.XObject.Annotations%2A>|<xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>の指定した型の注釈のコレクションを取得します。|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>から指定した型の注釈を削除します。|  
  
## <a name="see-also"></a>関連項目  
 [高度な LINQ to XML のプログラミング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
