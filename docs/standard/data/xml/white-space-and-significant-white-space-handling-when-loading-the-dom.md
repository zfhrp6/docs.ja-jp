---
title: "DOM を読み込むときの空白および有意の空白の処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>DOM を読み込むときの空白および有意の空白の処理
ドキュメントを読み込む場合は、空白を保持し、作成するオプションを設定できます**XmlWhitespace**ドキュメント ツリーにおいてノード。 空白のノードを作成するには、設定、 **PreserveWhitespace**プロパティを true にします。 プロパティ設定されている場合**false**が既定値である空白ノードは作成されません。 有意の空白ノードは常に保持、および**XmlSignificantWhitespace**ノードは常にメモリの設定に関係なく、このデータを表すために作成、 **PreserveWhitespace**フラグです。  
  
 ドキュメントがリーダーから読み込まれている場合、設定、 **PreserveWhitespace**フラグ プロパティ、 **XmlDocument**クラスの作成に影響**XmlWhitespace**ノード場合にのみ、 **WhitespaceHandling**プロパティを**XmlTextReader**に設定されていない**WhitespaceHandling.None**です。 値では、 **WhitespaceHandling**プロパティでそのフラグの設定よりも優先するリーダーを**XmlDocument**です。 詳細については**XmlSignificantWhitespace**を参照してください<xref:System.Xml.XmlSignificantWhitespace>です。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
