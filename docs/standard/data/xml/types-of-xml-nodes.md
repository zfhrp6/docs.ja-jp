---
title: "XML ノードの種類"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3914a2c5c06a2cc73f14bc473984094b474d537e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-xml-nodes"></a>XML ノードの種類
XML ドキュメントがノードのツリーとしてメモリに読み込まれると、ノードの作成時にノード型が決まります。 XML ドキュメント オブジェクト モデル (DOM) では複数のノード型が定義されています。これらのノード型は W3C (World Wide Web Consortium) で規定されているもので、セクション 1.1.1「The DOM Structure Model」に記載されています。 ノード型、ノード型に割り当てられるオブジェクト、およびそれぞれの簡単な説明を次の表に示します。  
  
|DOM ノード型|Object|説明|  
|-------------------|------------|-----------------|  
|ドキュメント|<xref:System.Xml.XmlDocument>|ツリー内のすべてのノードのコンテナーです。 ドキュメントのルートとも呼ばれますが、常にルート要素と一致するとは限りません。|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|1 つ以上のノードを非ツリー構造で格納する一時的なバッグです。|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|`<!DOCTYPE…>` ノードを表します。|  
|EntityReference|<xref:System.Xml.XmlEntityReference>|展開されていないエンティティ参照テキストを表します。|  
|要素|<xref:System.Xml.XmlElement>|要素ノードを表します。|  
|Attr|<xref:System.Xml.XmlAttribute>|要素の属性です。|  
|ProcessingInstruction|<xref:System.Xml.XmlProcessingInstruction>|処理命令ノードです。|  
|コメント|<xref:System.Xml.XmlComment>|コメント ノードです。|  
|テキスト|<xref:System.Xml.XmlText>|要素または属性に含まれるテキストです。|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|CDATA を表します。|  
|エンティティ|<xref:System.Xml.XmlEntity>|内部ドキュメント型定義 (DTD) のサブセットまたは外部 DTD とパラメーター エンティティから取得され、XML ドキュメントに含まれている `<!ENTITY…>` 宣言を表します。|  
|Notation|<xref:System.Xml.XmlNotation>|DTD で宣言された記法を表します。|  
  
 属性 (*attr*) が表示されている、W3C DOM Level 1 セクション 1.2 基本的なインターフェイスをノードとしてと任意の要素ノードの子は見なされません。  
  
 ただしとして Microsoft .NET Framework のオブジェクト モデルで使用可能な次の表は、W3C で定義されていないその他のノード型**XmlNodeType**列挙体です。 そのため、これらのノード型に対応する DOM ノード型の列はありません。  
  
|ノード型|説明|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|宣言ノード `<?xml version="1.0"…>` を表します。|  
|<xref:System.Xml.XmlSignificantWhitespace>|有意の空白を表します。これは混合コンテンツの空白です。|  
|<xref:System.Xml.XmlWhitespace>|要素コンテンツ内の空白を表します。|  
|EndElement|ときに返される**XmlReader**要素の終わりを取得します。<br /><br /> XML の例: **\<項目/>**<br /><br /> 詳細については、「<xref:System.Xml.XmlNodeType>」を参照してください。|  
|EndEntity|ときに返される**XmlReader**はエンティティの置換への呼び出しの結果として最後に取得<xref:System.Xml.XmlReader.ResolveEntity%2A>です。 詳細については、「<xref:System.Xml.XmlNodeType>」を参照してください。|  
  
 XML では読み取り、ノードとその内容に関する情報を印刷するノードの種類の case の構文を使用しているコード例を表示するを参照してください。<xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>です。  
  
 ノードの種類とその対応するオブジェクト名のオブジェクト階層の詳細については、次を参照してください。 [XML ドキュメント オブジェクト モデル (DOM) の階層](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)です。 ノード ツリーに作成されたオブジェクトの詳細については、次を参照してください。[オブジェクト階層の XML データへのマップ](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)です。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
