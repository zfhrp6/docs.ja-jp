---
title: "新しいノードの作成時における XML 要素名および属性名の検証 | Microsoft Docs"
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
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# 新しいノードの作成時における XML 要素名および属性名の検証
XML ドキュメント オブジェクト モデル \(DOM\) は、新しい要素ノードまたは属性ノードを作成するときに名前の有効性を確認します。  名前に無効な文字が含まれていると、例外がスローされます。  名前が正しくエンコードされ、有効であることを保証するには、**XmlConvert** クラスを使用して名前をエンコードし、アプリケーション レベルで名前をデコードする必要があります。  **XmlWriter** には、整形式の XML を生成するための追加の処理を行うメソッドが用意されています。  
  
## 参照  
 [XML ドキュメント オブジェクト モデル \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)