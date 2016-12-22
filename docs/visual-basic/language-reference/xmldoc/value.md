---
title: "&lt;value&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "<value> XML tag"
  - "value XML tag"
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;value&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロパティの説明を指定します。  
  
## 構文  
  
```  
<value>property-description</value>  
```  
  
#### パラメーター  
 `property-description`  
 プロパティの説明。  
  
## 解説  
 プロパティの説明を記述するには、`<value>` タグを使用します。  Visual Studio 開発環境のコード ウィザードを使って追加したプロパティには、[\<summary\>](../Topic/%3Csummary%3E%20\(Visual%20Basic\).md) タグが追加されます。  そのプロパティが表す値の説明を記述するには、`<value>` タグを手動で追加する必要があります。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 `<value>` タグを使用して、`Counter` プロパティに格納される値の説明を記述する例は次のようになります。  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)