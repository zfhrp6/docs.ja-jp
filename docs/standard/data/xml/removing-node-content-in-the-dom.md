---
title: "DOM のノード コンテンツの削除"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76be90829a414b091d3b311b96bf9bab9a2b56ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="removing-node-content-in-the-dom"></a>DOM のノード コンテンツの削除
<xref:System.Xml.XmlCharacterData> を継承するノード型、つまり <xref:System.Xml.XmlComment>、<xref:System.Xml.XmlText>、<xref:System.Xml.XmlCDataSection>、<xref:System.Xml.XmlWhitespace>、および <xref:System.Xml.XmlSignificantWhitespace> ノード型では、ノードから文字範囲を削除する <xref:System.Xml.XmlCharacterData.DeleteData%2A> メソッドを使用して文字を削除できます。 コンテンツを完全に削除するには、そのコンテンツが含まれているノードを削除します。 ノードを保持する必要があり、コンテンツが正しくない場合は、そのコンテンツを変更します。 ノードのコンテンツを変更する方法については、次を参照してください。[ノードの変更、コンテンツ、および XML ドキュメント内の値](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)です。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
