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
# <a name="changing-namespace-declarations-in-an-xml-document"></a>XML ドキュメントの名前空間宣言の変更
**XmlDocument**名前空間の宣言を公開および**xmlns**属性をドキュメント オブジェクト モデルの一部として使用します。 これらに保存されます、 **XmlDocument**ので、これらの属性の場所を維持して、ドキュメントを保存するときにします。 これらの属性を変更する影響を与えません、**名前**、 **NamespaceURI**、および**プレフィックス**ツリーに既に他のノードのプロパティです。 たとえば、次のドキュメントを読み込む場合、`test`要素には**NamespaceURI**`123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 削除する場合、`xmlns`次のように、属性、`test`要素がまだ、 **NamespaceURI**の`123`します。  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 同様に、異なるを追加する場合`xmlns`属性を`doc`要素は、次のように、`test`要素がまだ**NamespaceURI** `123`です。  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 そのため、変更する`xmlns`属性効果がありませんを保存して再読み込みするまで、 **XmlDocument**オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
