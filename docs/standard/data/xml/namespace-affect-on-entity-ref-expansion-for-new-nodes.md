---
title: "要素と属性を含む新しいノードでのエンティティ参照の展開に対する名前空間の影響"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 39110a9b44e6efbe7ad0331cfdb4fbe6078e7cfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>要素と属性を含む新しいノードでのエンティティ参照の展開に対する名前空間の影響
エンティティ宣言には、原則として任意のコンテンツを含めることができるため、`<!ENTITY aname "<elem>test</elem>">` のような要素が含まれている可能性もあります。  
  
 `&aname;` の置換コンテンツへの展開は、XML の解析時に行われるのではありません。 ノードがドキュメントに配置されるまでは、要素に対する名前空間を解決できないため、XML の展開は実行されません。 スコープ内の名前空間が判明するのは、ノードが配置された後になります。 ノードがドキュメントに配置されると、名前空間の解決が行われ、結果として得られたエンティティ コンテンツが適切なノードに解析されます。  
  
> [!NOTE]
>  新しく作成されたエンティティ参照ノードがいったん展開された後、再び展開されることはありません。 したがって、要素の置換テキストで使われる名前空間は、親ノードの設定時にバインドされます。 ただし、名前空間は変更できますまたはで複製されたエンティティ参照ノードを削除して、別の場所に挿入するときに、既存のエンティティ参照ノードの**CloneNode**メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
