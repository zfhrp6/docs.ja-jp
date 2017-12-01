---
title: "NodeLists および NamedNodeMaps の動的更新"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 459d746ff278ac4affa0318c1fad0aeb6a73e560
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>NodeLists および NamedNodeMaps の動的更新
**XmlNodeList**と**XmlNamedNodeMap** XML ドキュメントがメモリに読み込まれますが変更されている、まだ、ノードのセットを含む、World Wide Web コンソーシアム (W3C) の状態をこれらのオブジェクト動的であるノードの必要性の設定が含まれているとします。 つまり、基になっているドキュメントが変更されたら、これら 2 つのオブジェクトも変更される必要があります。 したがってがある場合、 **XmlNodeList**特定の要素 (たとえば、要素 X) のすべての子要素を格納している、要素 X 下のドキュメントに要素 Q は、要素を追加します。**XmlNodeList**その新しい要素 Q をそのコレクションに追加された必要もあります。 逆の場合も同様です。 ノードが追加された場合、 **XmlNodeList**、基になるドキュメントが同様に更新します。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
