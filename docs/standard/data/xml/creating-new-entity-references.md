---
title: "新しいエンティティ参照の作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22e9b66f58275141cf9da154573ca43a0b90affc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-entity-references"></a>新しいエンティティ参照の作成
**CreateEntityReference**メソッドが新たに作成**XmlEntityReference**ノード。 XML ドキュメント オブジェクト モデル (DOM) は、参照されているエンティティ名が既に宣言されているかどうかを確認します。 場合は、子ノード**XmlEntityReference**ノードは、エンティティ宣言ノードからコピーします。 一致するエンティティ宣言がない場合、エンティティ参照ノードには、唯一の子として空のテキスト ノードが追加されます。 の子ノード、 **XmlEntityReference**ノードは他のノードのコピーであり、これらの子ノードは読み取り専用と変更できません。  
  
 ノードがコピーされるとき、そのエンティティ参照が存在する位置のスコープに、名前空間が適用されていることがあります。 生成される要素ノードまたは属性ノードの構成は、この名前空間の影響を受けます。  
  
> [!NOTE]
>  DOM は子ノードを追加、 **EntityReference**のみを挿入するとき、 **EntityReference**ドキュメントにノードです。 新しく作成された**EntityReference**子ノードを持つノードがありません。  
  
 場合でも、 **XmlDataDocument**の派生クラスには、 **XmlDocument**、 **XmlDataDocument**エンティティ参照の作成をサポートしていません。 これは、ため**EntityReference**子は読み取り専用です。 子、 **EntityReference**ノードが複数の地域にまたがることができます。 ここでは、行の一部の一部を含む領域に関連付けられている、 **EntityReference**読み取り専用になります。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
