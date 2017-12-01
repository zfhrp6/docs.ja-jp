---
title: "エンティティ宣言とエンティティ参照の DOM への読み込み"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6370db06cbe7ff8d46258b0315059f5c37587fea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>エンティティ宣言とエンティティ参照の DOM への読み込み
エンティティとは、コンテンツやマークアップの代わりに XML で使われる名前を指定する宣言です。 エンティティを使用するには、2 つの手順が必要です。 まず、エンティティ宣言を使用して、置換するコンテンツに名前を結び付ける必要があります。 エンティティ宣言は、ドキュメント型定義 (DTD) または XML スキーマの中で、`<!ENTITY name "value">` 構文を使って作成します。 次に、エンティティ宣言で定義した名前を XML で使用します。 XML で使用するときは、エンティティ参照と呼ばれます。 たとえば、次のエンティティ宣言は、`publisher` という名前のエンティティを宣言し、それを "Microsoft Press" というコンテンツに関連付けます。  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 このエンティティ宣言を、XML でエンティティ参照として使用する例を次に示します。  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 パーサーの中には、ドキュメントをメモリに読み込むとき、エンティティを自動的に展開するものがあります。 この場合は、XML がメモリに読み込まれるときに、エンティティ宣言が記憶されて保存されます。 その後、一般エンティティ参照を識別する `&;` 文字を検出すると、パーサーはその名前をエンティティ宣言テーブルで検索します。 `&publisher;` という参照は、それが表すコンテンツに置き換えられます。 たとえば、次の XML を使用します。  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 エンティティ参照は展開され、`&publisher;` が Microsoft Press というコンテンツに置き換えられます。展開された XML は次のようになります。  
  
 **出力**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 エンティティには多くの種類があります。 エンティティの分類と用語を次の図に示します。  
  
 ![エンティティ型階層のフロー チャート](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 XML ドキュメント オブジェクト モデル (DOM) の Microsoft .NET Framework の実装の既定では、エンティティ参照を保持し、XML が読み込まれるときに、エンティティが展開されません。 このことは、DOM でドキュメントが読み込まれると、 **XmlEntityReference**参照変数を含むノード`&publisher;`が作成されると、DTD で宣言されているエンティティの内容を表すノードの子ノードをします。  
  
 使用して、`<!ENTITY publisher "Microsoft Press">`エンティティ宣言では、次の図は、 **XmlEntity**と**XmlText**この宣言により作成されたノード。  
  
 ![エンティティ宣言により作成されたノード](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 エンティティ参照が展開されるかどうかによって、メモリの DOM ツリーに生成されるノードが変わります。 生成されるノードの違いは、トピックで説明[保持されるエンティティ参照](../../../../docs/standard/data/xml/entity-references-are-preserved.md)と[保持されずに展開されるエンティティ参照](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md)です。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
