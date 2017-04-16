---
title: "NodeLists および NamedNodeMaps の動的更新 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# NodeLists および NamedNodeMaps の動的更新
**XmlNodeList** と **XmlNamedNodeMap** にはノード セットが格納されますが、XML ドキュメントはメモリに読み込まれ、変更されるため、W3C \(World Wide Web Consortium\) では、ノード セットが格納されるこれらのオブジェクトは動的でなければならないと規定しています。  つまり、基になっているドキュメントが変更されたら、これら 2 つのオブジェクトも変更される必要があります。  したがって、特定の要素 \(たとえば要素 X\) のすべての子要素が **XmlNodeList** に格納されている場合、別の要素である要素 Q は、要素 X の下のドキュメントに追加されます。  **XmlNodeList** のコレクションにも、その新しい要素 Q を追加する必要があります。  逆の場合も同様です。  **XmlNodeList** にノードが追加された場合は、基になっているドキュメントも同様に更新されます。  
  
## 参照  
 [XML ドキュメント オブジェクト モデル \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)