---
title: "XML ドキュメントの名前空間宣言の変更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 627882efcbc41310ee177cba984e4add5b07bd15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="539d8-102">XML ドキュメントの名前空間宣言の変更</span><span class="sxs-lookup"><span data-stu-id="539d8-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="539d8-103">**XmlDocument**名前空間の宣言を公開および**xmlns**属性をドキュメント オブジェクト モデルの一部として使用します。</span><span class="sxs-lookup"><span data-stu-id="539d8-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="539d8-104">これらに保存されます、 **XmlDocument**ので、これらの属性の場所を維持して、ドキュメントを保存するときにします。</span><span class="sxs-lookup"><span data-stu-id="539d8-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="539d8-105">これらの属性を変更する影響を与えません、**名前**、 **NamespaceURI**、および**プレフィックス**ツリーに既に他のノードのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="539d8-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="539d8-106">たとえば、次のドキュメントを読み込む場合、`test`要素には**NamespaceURI**`123.`</span><span class="sxs-lookup"><span data-stu-id="539d8-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="539d8-107">削除する場合、`xmlns`次のように、属性、`test`要素がまだ、 **NamespaceURI**の`123`します。</span><span class="sxs-lookup"><span data-stu-id="539d8-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="539d8-108">同様に、異なるを追加する場合`xmlns`属性を`doc`要素は、次のように、`test`要素がまだ**NamespaceURI** `123`です。</span><span class="sxs-lookup"><span data-stu-id="539d8-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="539d8-109">そのため、変更する`xmlns`属性効果がありませんを保存して再読み込みするまで、 **XmlDocument**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="539d8-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="539d8-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="539d8-110">See Also</span></span>  
 [<span data-ttu-id="539d8-111">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="539d8-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
