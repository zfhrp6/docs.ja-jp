---
title: "&lt;include&gt; (Visual Basic) | Microsoft Docs"
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
  - "include XML tag"
  - "<include> XML tag"
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &lt;include&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ソース コード内の型やメンバーを記述する別のファイルを参照します。  
  
## 構文  
  
```  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### パラメーター  
 `filename`  
 必ず指定します。  ドキュメントを含むファイルの名前。  ファイル名にパスを指定することもできます。  `filename` は二重引用符 \(" "\) で囲みます。  
  
 `tagpath`  
 必ず指定します。  `filename` のタグのパス。その後ろにタグの `name` を指定します。  パスは二重引用符 \(" "\) で囲みます。  
  
 `name`  
 必ず指定します。  タグの名前指定子。その後ろにコメントを指定します。  `Name` には `id` を指定します。  
  
 `id`  
 必ず指定します。  タグの ID。その後ろにコメントを指定します。  ID は、単一引用符 \(' '\) で囲みます。  
  
## 解説  
 `<include>` タグを使用すると、ソース コード内の型およびメンバーの説明として、別のファイル内のコメントを参照できます。  これはソース コードのファイルにドキュメント コメントを直接記述しない方法です。  
  
 `<include>` タグは、W3C の XML Path Language \(XPath\) Version 1.0 Recommendation を使用します。  `<include>` のカスタマイズ方法の詳細については、http:\/\/www.w3.org\/TR\/xpath を参照してください。  
  
## 使用例  
 この例では、`<include>` タグを使用してメンバーもドキュメントのコメントを `commentFile.xml` ファイルからインポートします。  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 `commentFile.xml` の形式は次のとおりです。  
  
```  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## 参照  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)