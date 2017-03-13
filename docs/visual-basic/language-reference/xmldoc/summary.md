---
title: "&lt;summary&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "<summary> XML tag"
  - "summary XML tag"
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# &lt;summary&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

メンバーの概要を指定します。  
  
## 構文  
  
```  
<summary>description</summary>  
```  
  
#### パラメーター  
 `description`  
 オブジェクトの要約。  
  
## 解説  
 `<summary>` タグは、型または型のメンバーの説明に使用します。  型の説明に補足情報を追加するには、[\<remarks\>](../../../visual-basic/language-reference/xmldoc/remarks.md) タグを使用します。  
  
 `<summary>` のタグのテキストは、IntelliSenseの種類に関する唯一の情報源では、オブジェクト ブラウザーに表示されます。  オブジェクト ブラウザーについては、[コードの構造の表示](/visual-studio/ide/viewing-the-structure-of-code)を参照してください。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 この例では、`<summary>` タグを使用して `ResetCounter` メソッドと `Counter` プロパティを記述します。  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)