---
title: "DOM における名前空間のサポート | Microsoft Docs"
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
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# DOM における名前空間のサポート
XML ドキュメント オブジェクト モデル \(DOM\) は名前空間に完全に対応しています。  名前空間に対応している XML ドキュメントだけがサポートされます。  W3C \(World Wide Web Consortium\) の仕様によれば、DOM Level 1 を実装する DOM アプリケーションは名前空間に対応していなくてもかまいませんが、DOM Level 2 の機能は名前空間に対応しています。  ただし、メソッドが DOM 勧告の Level 1 または Level 2 のどちらに準拠しているかに関係なく、XML DOM のすべての機能は名前空間に対応しています。  
  
 たとえば、名前空間に対応していない環境では、DOM Level 1 勧告の規定に従って `setAttribute("A:b", "123")` を呼び出しても、プレフィックス `A` とローカル名 `b` を持つ属性は設定されません。  この結果は、`A:b` という値の属性になります。  
  
 名前空間に対応している環境では、DOM Level 2 の `setAttribute("A:b", "123")` を呼び出すと、属性のプレフィックスが `A` になり、ローカル名が `b` になります。  これが Microsoft .NET DOM の動作です。  
  
 したがって、名前パラメーターを受け取るすべてのメソッドは、名前を修飾するプレフィックスも受け取ります。  DOM Level 1 の **setAttribute** メソッドの `A:b` のような名前パラメーターは、次のように解析されます。  
  
-   コロン \(:\) が含まれない場合は、ローカル名が `name` パラメーターに設定され、プレフィックスと名前空間 URI は空の文字列になります。  
  
-   コロンが見つかると、最初のコロンの位置に基づいて名前が 2 つの部分に分割されます。  プレフィックスはコロンより前の文字列に設定され、ローカル名はコロンより後の文字列に設定されます。  名前空間 URI の値をとらないメソッドでは、名前空間 URI は解決されず、空の文字列のままになります。  それ以外の場合は、メソッドに渡された文字列が名前空間 URI として設定されます。  プレフィックスが定義されていない場合、**Save** メソッド、**InnerXml** プロパティ、および **OuterXml** プロパティは失敗します。  
  
## 参照  
 [XML ドキュメント オブジェクト モデル \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)