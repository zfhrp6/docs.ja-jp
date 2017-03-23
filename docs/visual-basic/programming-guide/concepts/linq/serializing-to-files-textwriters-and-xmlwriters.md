---
title: "ファイル、Textwriter、および XmlWriters3 へのシリアル化 |Microsoft ドキュメント"
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
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
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
ms.openlocfilehash: 98662b8d84459ed051d048084c2755fa7aaf8247
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>ファイル、TextWriter、および XmlWriter へのシリアル化
XML ツリーをシリアル化することができます、 <xref:System.IO.File>、 <xref:System.IO.TextWriter>、または<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File>  
  
 任意の XML コンポーネントをシリアル化することができますを含む<xref:System.Xml.Linq.XDocument>と<xref:System.Xml.Linq.XElement>を使用して文字列に、`ToString`メソッド</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>。  
  
 文字列にシリアル化するときに書式設定されないようにする場合は、使用、<xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>メソッド</xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>。  
  
 ファイルにシリアル化するときの既定動作では、(インデント設定)、結果の XML ドキュメントの書式設定されます。 インデントを設定する場合、XML ツリー内の意味のない空白は保持されません。 書式設定を含む、シリアル化する受け取らない次のメソッドのオーバー ロードのいずれかの操作を使用して<xref:System.Xml.Linq.SaveOptions>を引数として:</xref:System.Xml.Linq.SaveOptions>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 インデントを設定せず、XML ツリー内の余分な空白を保存するオプションを設定する場合は、次のメソッドのオーバー ロードのいずれかを使用<xref:System.Xml.Linq.SaveOptions>を引数として:</xref:System.Xml.Linq.SaveOptions>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 例については、該当するリファレンス トピックを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [XML ツリーをシリアル化する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
