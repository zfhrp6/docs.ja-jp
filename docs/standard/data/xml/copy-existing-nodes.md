---
title: 既存のノードのコピー
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e7f5638d0d1f7bf450be526d7c295d4bb6a79eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="copy-existing-nodes"></a>既存のノードのコピー
XML ドキュメント オブジェクト モデル (DOM) には、**SelectSingleNode**、**ChildNodes[int i]**、**Attributes[int i]** など、ノードの選択に使用できるメソッドとプロパティが多数用意されています。 ノードを選択すると、その特定のノード型で利用できる挿入メソッドを使用してツリーに挿入できます。 ノードをツリーに挿入するときの唯一の制約は、ノードを挿入した後もドキュメントが整形式になっていなければならないことです。 既存のノードを DOM ツリーに挿入すると、そのノードは元の位置から削除され、挿入先の位置に追加されます。  
  
## <a name="see-also"></a>参照  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
