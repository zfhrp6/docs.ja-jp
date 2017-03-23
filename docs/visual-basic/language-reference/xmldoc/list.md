---
title: "&lt;list&gt; (Visual Basic) | Microsoft Docs"
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
  - "listheader XML tag"
  - "<item> XML tag"
  - "<list> XML tag"
  - "<listheader> XML tag"
  - "term XML tag"
  - "list XML tag"
  - "<description> XML tag"
  - "description XML tag"
  - "item XML tag"
  - "<term> XML tag"
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# &lt;list&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

リストまたは表を定義します。  
  
## 構文  
  
```  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### パラメーター  
 `type`  
 リストの型を指定します。  箇条書きリストの場合は "bullet"、番号付きリストの場合は "number"、2 列の表の場合は "table" です。  
  
 `term`  
 `type` が "table" の場合のみ使用されます。説明タグで定義された、定義する用語です。  
  
 `description`  
 `type` が "bullet" または "number" の場合、`description` はリスト内の項目です。`type` が "table" の場合、`description` は `term` の定義です。  
  
## 解説  
 `<listheader>` ブロックは、表または定義リストの見出しを定義します。  表を定義するとき、見出しで指定する必要があるのは、`term` のエントリだけです。  
  
 リストの各項目は、`<item>` ブロックで指定します。  定義リストを作成するときは、`term` と `description` の両方を指定する必要があります。  ただし、表、箇条書きリスト、または番号付きリストに指定する必要があるのは、`description` のエントリだけです。  
  
 リストや表には、必要な数だけ `<item>` ブロックを指定できます。  
  
 コンパイル時に [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 この例では、`<list>` タグを使って、解説セクションに箇条書きリストを定義します。  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)