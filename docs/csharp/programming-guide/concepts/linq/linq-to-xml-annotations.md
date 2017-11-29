---
title: "LINQ to XML の注釈3"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eadbc55ac6188fa3634745bf8bb222f07675a308
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-annotations"></a>LINQ to XML の注釈
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の注釈を使用すると、任意の型の任意のオブジェクトを XML ツリー内の任意の XML コンポーネントに関連付けることができます。  
  
 <xref:System.Xml.Linq.XElement> や <xref:System.Xml.Linq.XAttribute> などの XML コンポーネントに注釈を追加するには、<xref:System.Xml.Linq.XObject.AddAnnotation%2A> メソッドを呼び出します。 注釈は型によって取得します。  
  
 注釈は XML 情報セットの一部ではないことに注意してください。注釈はシリアル化も逆シリアル化もされません。  
  
## <a name="methods"></a>メソッド  
 注釈を操作する場合は、次のメソッドを使用できます。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|オブジェクトを <xref:System.Xml.Linq.XObject> の注釈の一覧に追加します。|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|指定された型の最初の注釈オブジェクトを <xref:System.Xml.Linq.XObject> から取得します。|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<xref:System.Xml.Linq.XObject> について指定された型の注釈のコレクションを取得します。|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|指定された型の注釈を <xref:System.Xml.Linq.XObject> から削除します。|  
  
## <a name="see-also"></a>関連項目  
 [高度な LINQ to XML プログラミング (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
