---
title: "名前空間の概要 (LINQ to XML) |Microsoft ドキュメント"
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
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cec2efd31c96af17ad717abaa8f4359210e99a78
ms.lasthandoff: 03/13/2017

---
# <a name="namespaces-overview-linq-to-xml"></a>名前空間の概要 (LINQ to XML)
このトピック<xref:System.Xml.Linq.XName>クラス、および<xref:System.Xml.Linq.XNamespace>クラス</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName>の名前空間が導入されています  
  
## <a name="xml-names"></a>XML 名  
 XML 名は、多くの場合、XML プログラミングを複雑にしている原因です。 XML 名は、XML 名前空間 (XML 名前空間 URI) とローカル名で構成されます。 XML 名前空間は、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] ベースのプログラムにおける名前空間と似ています。 これを使用すると、要素と属性の名前を一意に修飾できます。 このため、XML ドキュメントのさまざまな部分の間で、名前の競合を回避するのに役立ちます。 XML 名前空間を宣言した後は、その名前空間内でのみ一意であるローカル名を選択できます。  
  
 XML 名の別の要素が XML*名前空間プレフィックス*します。 XML プレフィックスは、XML 名の複雑さの主要な原因です。 このプレフィックスを使用すると、XML 名前空間に対するショートカットを作成できるため、XML ドキュメントがより簡潔でわかりやすくなります。 ただし XML プレフィックスはコンテキストによって意味が異なり、これが複雑さの原因となります。 たとえば、XML プレフィックス `aw` に関連付けられている XML 名前空間が、同じ XML ツリー内でも部分によって異なる可能性があります。  
  
 使用する場合[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Visual Basic および XML リテラルと名前空間内のドキュメントを操作するときに、名前空間プレフィックスを使用する必要があります。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]、XML 名を表すクラスが<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> XML 名は、全体で頻繁に表示、 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API、XML 名が必要な場所にして見つかります、<xref:System.Xml.Linq.XName>パラメーター</xref:System.Xml.Linq.XName> 。 ただし、ほとんどを使用する直接<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XName>文字列からの暗黙的な変換が含まれています。</xref:System.Xml.Linq.XName>  
  
 詳細については、「 <xref:System.Xml.Linq.XNamespace> <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XNamespace>の使用」を参照していますください。  
  
## <a name="see-also"></a>関連項目  
 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
