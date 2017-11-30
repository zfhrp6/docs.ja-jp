---
title: "保持されずに展開されるエンティティ参照"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 069d3b94a0269917400e75fdbe975ec39dcfdb71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>保持されずに展開されるエンティティ参照
エンティティ参照が展開され、それが表すテキストに置き換え場合に、 **XmlEntityReference**ノードは作成されません。 代わりに、エンティティ宣言が解析されの代わりに、宣言のコンテンツから作成されたノードをコピー、 **XmlEntityReference**です。 そのためで、`&publisher;`例では、`&publisher;`は保存されず、代わりに、 **XmlText**ノードを作成します。  
  
 ![ツリー構造を展開](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
エンティティ参照が展開される場合のツリー構造  
  
 `B` や `<` などの文字エンティティは保持されません。 文字エンティティは常に展開され、テキスト ノードとして表されます。  
  
 保持するために**XmlEntityReference**ノードとエンティティ参照の子ノードが接続して、設定、 **EntityHandling**フラグを**ExpandCharEntities**です。 それ以外の場合のままにして、 **EntityHandling**フラグを既定値、つまりを**ExpandEntities**です。 その場合、DOM ではエンティティ参照ノードが認識されません。 エンティティ参照ノードは、エンティティ宣言の子ノードのコピーに置き換えられます。  
  
 エンティティ参照を保持しない場合の副作用の 1 つとして、そのドキュメントを保存して別のアプリケーションに渡したとき、受け取る側のアプリケーションでは、エンティティ参照によってノードが生成されたことを識別できないという点があります。 しかし、エンティティ参照を保持する場合は、受け取り側アプリケーションがエンティティ参照を認識し、子ノードを読み取ります。 子ノードが、エンティティ宣言に含まれていた情報を表していることは明らかです。 たとえば、エンティティ参照が保持される場合、DOM の構造は理論的に次のようになります。  
  
 XmlElement: publisher  
  
 XmlEntityReference: `&publisher;`  
  
 XmlText: Microsoft Press  
  
 DOM でエンティティ参照が展開される場合は、次のようなツリー構造になります。既定のメソッドでは、エンティティ参照が展開されます。  
  
 XmlElement: publisher  
  
 XmlText: Microsoft Press  
  
 エンティティ参照ノードが削除され、受信側のアプリケーションに指示することはできないことに注意してください、 **XmlText**エンティティ宣言から作成された"Microsoft Press"を含むノードです。  
  
 エンティティを解決できないリーダーを使用する場合、**ロード**エンティティ参照を検出すると、メソッドが例外をスローします。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
