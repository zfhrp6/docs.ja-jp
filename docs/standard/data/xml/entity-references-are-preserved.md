---
title: "保持されるエンティティ参照"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 770c714e8f5942ea733c417ae9b06f69e4acf1a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-preserved"></a>保持されるエンティティ参照
エンティティ参照が展開せずに保持されます、XML ドキュメント オブジェクト モデル (DOM) をビルド、 **XmlEntityReference**ノード、エンティティ参照を検出するとします。  
  
 たとえば、次の XML を使用します。  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 DOM のビルド、 **XmlEntityReference**ノードに到達したときに、`&publisher;`参照します。 **XmlEntityReference**エンティティ宣言のコンテンツからコピーされた子ノードが含まれています。 ため、上記のコード例に、エンティティ宣言内のテキストが含まれています、 **XmlText**エンティティ参照ノードの子ノードとしてノードを作成します。  
  
 ![ツリー構造が保持されているエンティティ参照の](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
エンティティ参照が保持される場合のツリー構造  
  
 子ノード、 **XmlEntityReference**ノードから作成されたすべての子のコピーである、 **XmlEntity**ノード、エンティティ宣言が発生したとき。  
  
> [!NOTE]
>  コピーされたノード、 **XmlEntity**常に、エンティティ参照ノードの下に配置される正確なコピーではありません。 エンティティ参照ノードが現れた位置のスコープに名前空間が適用されていると、それが子ノードの最終的な構成に影響する可能性があります。  
  
 既定では、一般エンティティと同様に`&abc;`は保持されますと**XmlEntityReference**ノードは常に作成します。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
