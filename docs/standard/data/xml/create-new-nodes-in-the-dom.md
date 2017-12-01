---
title: "DOM への新しいノードの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ec624a02f98fda4352b5ba8ff43681fba040c676
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="create-new-nodes-in-the-dom"></a>DOM への新しいノードの作成
<xref:System.Xml.XmlDocument> には、すべてのノード型に対応する Create メソッドがあります。 このメソッドに、名前が必要な場合は名前を渡し、コンテンツを持つノードではコンテンツやその他のパラメーターを指定すると、そのノードが作成されます。コンテンツを持つノードには、たとえばテキスト ノードがあります。 次のメソッドは、ノードを適切に作成するために、名前といくつかのパラメーターの指定が必要なメソッドです。  
  
-   <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 その他のノード型では、パラメーターにデータを与えるだけでなく、他の要件を満たす必要もあります。  
  
 属性については、次を参照してください。 [DOM の要素の新しい属性の作成](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md)です。 要素と属性名の検証については、次を参照してください。 [XML 要素と属性名の検証を作成するときに新しいノード](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md)です。 エンティティ参照を作成するには、次を参照してください。[新しいエンティティ参照の作成](../../../../docs/standard/data/xml/creating-new-entity-references.md)です。 エンティティ参照の展開の名前空間の影響については、次を参照してください。 [Namespace に影響を及ぼす新しいノードを含む要素と属性のエンティティ参照の展開](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md)です。  
  
 新しく作成したノードをツリーに挿入するには、いくつかのメソッドを使用できます。 使用できるメソッドと、そのメソッドによって DOM のどこに新しいノードが作成されるかの説明を次の表に示します。  
  
|メソッド|ノードの位置|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|参照ノードの前に挿入されます。 たとえば、5 番目の位置に新しいノードを挿入するには、次のようにします。<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> 詳細については、<xref:System.Xml.XmlNode.InsertBefore%2A> メソッドを参照してください。|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|参照ノードの後に挿入されます。 次に例を示します。<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> 詳細については、<xref:System.Xml.XmlNode.InsertAfter%2A> メソッドを参照してください。|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|当該ノードの子ノードのリストの末尾にノードを追加します。 追加するノードが <xref:System.Xml.XmlDocumentFragment> の場合は、ドキュメント フラグメントの内容全体がこのノードの子リストに移動されます。 詳細については、<xref:System.Xml.XmlNode.AppendChild%2A> メソッドを参照してください。|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|当該ノードの子ノードのリストの先頭にノードを追加します。 追加するノードが <xref:System.Xml.XmlDocumentFragment> の場合は、ドキュメント フラグメントの内容全体がこのノードの子リストに移動されます。 詳細については、<xref:System.Xml.XmlNode.PrependChild%2A> メソッドを参照してください。|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|要素に関連付けられている属性コレクションの末尾に <xref:System.Xml.XmlAttribute> ノードを追加します。 詳細については、<xref:System.Xml.XmlAttributeCollection.Append%2A> メソッドを参照してください。|  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
