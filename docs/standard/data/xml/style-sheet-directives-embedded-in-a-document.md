---
title: "ドキュメントに埋め込まれたスタイル シート ディレクティブ | Microsoft Docs"
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
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 4
---
# ドキュメントに埋め込まれたスタイル シート ディレクティブ
既存の XML に `<?xml:stylesheet?>` というスタイル シート ディレクティブが含まれていることがあります。  Microsoft Internet Explorer は、これを `<?xml-stylesheet?>` 構文に代わるものとして受け入れます。  次のように `<?xml:stylesheet?>` ディレクティブが含まれている XML データを XML ドキュメント オブジェクト モデル \(DOM\) に読み込もうとすると、例外がスローされます。  
  
```  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 例外が発生するのは、`<?xml:stylesheet?>` が DOM に対する無効な **ProcessingInstruction** と見なされるからです。  『Namespaces in XML』仕様によれば、**ProcessingInstruction** は、QNames \(修飾名\) ではなく、NCNames \(コロンが含まれない名前\) にする必要があります。  
  
 『Namespaces in XML』仕様書のセクション 6 によると、**Load** メソッドと **LoadXml** メソッドをこの仕様に準拠させた場合の影響として、ドキュメントには次の規則が適用されることになります。  
  
-   すべての要素型と属性名は、0 個または 1 個のコロンを含みます。  
  
-   エンティティ名、処理命令ターゲット、記法名は、いずれもコロンを含みません。  
  
 コロンが含まれた `<?xml:stylesheet?>` は、2 番目の規則に違反します。  
  
 www.w3.org\/TR\/xml\-stylesheet で公開されている W3C \(World Wide Web Consortium\) 勧告『Associating Style Sheets with XML documents Version 1.0』によれば、XSLT スタイル シートを XML ドキュメントに関連付ける処理命令は、コロンをダッシュに置き換えた `<?xml-stylesheet?>` です。  
  
## 参照  
 [XML ドキュメント オブジェクト モデル \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)