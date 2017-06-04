---
title: "既存のノードのコピー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 既存のノードのコピー
XML ドキュメント オブジェクト モデル \(DOM\) には、**SelectSingleNode**、**ChildNodes\[int i\]**、**Attributes\[int i\]** など、ノードの選択に使用できるメソッドとプロパティが多数用意されています。  ノードを選択すると、その特定のノード型で利用できる挿入メソッドを使用してツリーに挿入できます。  ノードをツリーに挿入するときの唯一の制約は、ノードを挿入した後もドキュメントが整形式になっていなければならないことです。  既存のノードを DOM ツリーに挿入すると、そのノードは元の位置から削除され、挿入先の位置に追加されます。  
  
## 参照  
 [XML ドキュメント オブジェクト モデル \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)