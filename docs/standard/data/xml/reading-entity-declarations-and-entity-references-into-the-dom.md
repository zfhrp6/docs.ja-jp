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
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="bf14f-102">エンティティ宣言とエンティティ参照の DOM への読み込み</span><span class="sxs-lookup"><span data-stu-id="bf14f-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="bf14f-103">エンティティとは、コンテンツやマークアップの代わりに XML で使われる名前を指定する宣言です。</span><span class="sxs-lookup"><span data-stu-id="bf14f-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="bf14f-104">エンティティを使用するには、2 つの手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="bf14f-104">There are two parts to entities.</span></span> <span data-ttu-id="bf14f-105">まず、エンティティ宣言を使用して、置換するコンテンツに名前を結び付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf14f-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="bf14f-106">エンティティ宣言は、ドキュメント型定義 (DTD) または XML スキーマの中で、`<!ENTITY name "value">` 構文を使って作成します。</span><span class="sxs-lookup"><span data-stu-id="bf14f-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="bf14f-107">次に、エンティティ宣言で定義した名前を XML で使用します。</span><span class="sxs-lookup"><span data-stu-id="bf14f-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="bf14f-108">XML で使用するときは、エンティティ参照と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="bf14f-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="bf14f-109">たとえば、次のエンティティ宣言は、`publisher` という名前のエンティティを宣言し、それを "Microsoft Press" というコンテンツに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="bf14f-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="bf14f-110">このエンティティ宣言を、XML でエンティティ参照として使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bf14f-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="bf14f-111">パーサーの中には、ドキュメントをメモリに読み込むとき、エンティティを自動的に展開するものがあります。</span><span class="sxs-lookup"><span data-stu-id="bf14f-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="bf14f-112">この場合は、XML がメモリに読み込まれるときに、エンティティ宣言が記憶されて保存されます。</span><span class="sxs-lookup"><span data-stu-id="bf14f-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="bf14f-113">その後、一般エンティティ参照を識別する `&;` 文字を検出すると、パーサーはその名前をエンティティ宣言テーブルで検索します。</span><span class="sxs-lookup"><span data-stu-id="bf14f-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="bf14f-114">`&publisher;` という参照は、それが表すコンテンツに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="bf14f-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="bf14f-115">たとえば、次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="bf14f-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="bf14f-116">エンティティ参照は展開され、`&publisher;` が Microsoft Press というコンテンツに置き換えられます。展開された XML は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="bf14f-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="bf14f-117">**出力**</span><span class="sxs-lookup"><span data-stu-id="bf14f-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="bf14f-118">エンティティには多くの種類があります。</span><span class="sxs-lookup"><span data-stu-id="bf14f-118">There are many kinds of entities.</span></span> <span data-ttu-id="bf14f-119">エンティティの分類と用語を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="bf14f-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="bf14f-120">![エンティティ型階層のフロー チャート](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="bf14f-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="bf14f-121">XML ドキュメント オブジェクト モデル (DOM) の Microsoft .NET Framework の実装の既定では、エンティティ参照を保持し、XML が読み込まれるときに、エンティティが展開されません。</span><span class="sxs-lookup"><span data-stu-id="bf14f-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="bf14f-122">このことは、DOM でドキュメントが読み込まれると、 **XmlEntityReference**参照変数を含むノード`&publisher;`が作成されると、DTD で宣言されているエンティティの内容を表すノードの子ノードをします。</span><span class="sxs-lookup"><span data-stu-id="bf14f-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="bf14f-123">使用して、`<!ENTITY publisher "Microsoft Press">`エンティティ宣言では、次の図は、 **XmlEntity**と**XmlText**この宣言により作成されたノード。</span><span class="sxs-lookup"><span data-stu-id="bf14f-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="bf14f-124">![エンティティ宣言により作成されたノード](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="bf14f-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="bf14f-125">エンティティ参照が展開されるかどうかによって、メモリの DOM ツリーに生成されるノードが変わります。</span><span class="sxs-lookup"><span data-stu-id="bf14f-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="bf14f-126">生成されるノードの違いは、トピックで説明[保持されるエンティティ参照](../../../../docs/standard/data/xml/entity-references-are-preserved.md)と[保持されずに展開されるエンティティ参照](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md)です。</span><span class="sxs-lookup"><span data-stu-id="bf14f-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf14f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf14f-127">See Also</span></span>  
 [<span data-ttu-id="bf14f-128">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="bf14f-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
