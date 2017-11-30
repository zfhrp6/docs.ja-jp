---
title: "ドキュメントに埋め込まれたスタイル シート ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c5cfcc9f35e4a07e9426a4dd24c1e2f04985f16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>ドキュメントに埋め込まれたスタイル シート ディレクティブ
既存の XML に `<?xml:stylesheet?>` というスタイル シート ディレクティブが含まれていることがあります。 Microsoft Internet Explorer では、これを受け付ける代わりに、`<?xml-stylesheet?>`構文です。 次のように `<?xml:stylesheet?>` ディレクティブが含まれている XML データを XML ドキュメント オブジェクト モデル (DOM) に読み込もうとすると、例外がスローされます。  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 これは、ために発生、`<?xml:stylesheet?>`が無効と見なされます**ProcessingInstruction** DOM に どの**ProcessingInstruction**、namespaces in XML 』 仕様ではなく修飾名 (Qname)、コロンを含まない名前 (NCNames) を指定できますのみです。  
  
 In XML 』 仕様、効果が得名前空間のセクション 6、**ロード**と**LoadXml**に準拠しているメソッドの仕様を文書内にあります。  
  
-   すべての要素型と属性名は、0 個または 1 個のコロンを含みます。  
  
-   エンティティ名、処理命令ターゲット、記法名は、いずれもコロンを含みません。  
  
 コロンが含まれた `<?xml:stylesheet?>` は、2 番目の規則に違反します。  
  
 www.w3.org/TR/xml-stylesheet で公開されている W3C (World Wide Web Consortium) 勧告『Associating Style Sheets with XML documents Version 1.0』によれば、XSLT スタイル シートを XML ドキュメントに関連付ける処理命令は、コロンをダッシュに置き換えた `<?xml-stylesheet?>` です。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
