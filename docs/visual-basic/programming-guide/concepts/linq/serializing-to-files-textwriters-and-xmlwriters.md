---
title: "ファイル、Textwriter、および XmlWriters3 にシリアル化します。"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f4c5578bc20f91eb35f78355dff0fc4c44e878e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>ファイル、TextWriter、および XmlWriter へのシリアル化
XML ツリーは、<xref:System.IO.File>、<xref:System.IO.TextWriter>、または <xref:System.Xml.XmlWriter> にシリアル化できます。  
  
 <xref:System.Xml.Linq.XDocument> メソッドを使用すると、<xref:System.Xml.Linq.XElement> や `ToString` など任意の XML コンポーネントを文字列にシリアル化できます。  
  
 文字列にシリアル化するときに書式設定されないようにするには、<xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> メソッドを使用します。  
  
 ファイルにシリアル化するときの既定の動作では、結果の XML ドキュメントの書式設定 (インデント設定) が行われます。 インデントを設定する場合、XML ツリー内の意味のない空白は保持されません。 書式を設定してシリアル化するには、<xref:System.Xml.Linq.SaveOptions> を引数として受け取らない次のメソッドのいずれかのオーバーロードを使用します。  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 インデントを設定せず、XML ツリー内の意味のない空白を保持できるようにするには、<xref:System.Xml.Linq.SaveOptions> を引数として受け取る次のメソッドのいずれかのオーバーロードを使用します。  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 例については、該当するリファレンス トピックを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [(Visual Basic) の XML ツリーをシリアル化します。](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
