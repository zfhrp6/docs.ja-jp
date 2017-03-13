---
title: "&lt;param&gt; (Visual Basic) | Microsoft Docs"
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
  - "param XML tag"
  - "<param> XML tag"
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# &lt;param&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

パラメーターの名前と説明を定義します。  
  
## 構文  
  
```  
<param name="name">description</param>  
```  
  
#### パラメーター  
 `name`  
 メソッド パラメーターの名前。  名前は、二重引用符 \(" "\) で囲みます。  
  
 `description`  
 パラメーターの説明。  
  
## 解説  
 `<param>` タグは、メソッド宣言のコメント内で使用して、メソッドのパラメーターの 1 つを説明します。  
  
 `<param>` のタグのテキストは、次の場所に表示されます:  
  
-   Intellisenseのパラメーター情報。  詳細については、「[IntelliSense の使用方法](/visual-studio/ide/using-intellisense)」を参照してください。  
  
-   オブジェクト ブラウザー。  詳細については、「[コードの構造の表示](/visual-studio/ide/viewing-the-structure-of-code)」を参照してください。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 `<param>` タグを使って `id` パラメーターの説明を記述する例を次に示します。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)