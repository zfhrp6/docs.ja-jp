---
title: "XML ドキュメント オブジェクト モデル (DOM) の階層構造"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6dec61860fba5815b1dae802d280e8df6628ab91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a>XML ドキュメント オブジェクト モデル (DOM) の階層構造
XML ドキュメント オブジェクト モデル (DOM) のクラスの階層構造を次の図に示します。クラス名に続くかっこ内の名前は、W3C (World Wide Web Consortium) 名です。  
  
 ![XML ドキュメント オブジェクト モデル &#40;DOM&#41;階層](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
XML ドキュメント オブジェクト モデル (DOM) の階層構造  
  
 次のクラスを継承しない、 **XmlNode**:  
  
-   **XmlImplementation**  
  
-   **XmlNamedNodeMap**  
  
-   **XmlNodeList**  
  
-   **XmlNodeChangedEventArgs**  
  
 **XmlImplementation**クラスは XML ドキュメントの作成に使用します。 詳細については、次を参照してください。 [XML ドキュメントの作成](../../../../docs/standard/data/xml/xml-document-creation.md)です。  
  
 **XmlNamedNodeMap**クラスは、順序付けられていないノードのセットを処理します。 詳細については、次を参照してください。[名前またはインデックスによる順序付けられていないノードの取得](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md)です。  
  
 **XmlNodeList**クラスは、ノードの順序付きリストを処理します。 詳細については、次を参照してください。[インデックスによる順序付けられたノードの取得](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md)です。  
  
 **XmlNodeChangedEventArgs**クラスに登録されたイベント ハンドラーの処理、 **XmlDocument**です。 詳細については、次を参照してください。 [XmlNodeChangedEventArgs による XML ドキュメントでのイベント処理](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)です。  
  
 **XmlLinkedNode**クラスから継承**XmlNode**です。 その目的は、2 つのメソッドをオーバーライドする**XmlNode**: **PreviousSibling**と**NextSibling**メソッドです。 これらのオーバーライドされたメソッドは、によって継承および使用**XmlCharacterData**、 **XmlDeclaration**、 **XmlDocumentType**、 **XmlElement**、 **XmlEntityReference**、および**XmlProcessingInstruction**、これらは前または次の兄弟を持つクラス。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
