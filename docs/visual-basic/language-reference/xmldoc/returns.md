---
title: "&lt;returns&gt; (Visual Basic) | Microsoft Docs"
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
  - "returns XML tag"
  - "<returns> XML tag"
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;returns&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロパティまたは関数の戻り値を指定します。  
  
## 構文  
  
```  
<returns>description</returns>  
```  
  
#### パラメーター  
 `description`  
 戻り値の説明。  
  
## 解説  
 `<returns>` タグは、メソッド宣言のコメント内で使用され、戻り値について説明します。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 この例では、`<returns>` タグを使用して `DoesRecordExist` 関数が返す値について説明します。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)