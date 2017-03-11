---
title: "&lt;list&gt; (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "list"
  - "<list>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<item> C# XML タグ"
  - "<list> C# XML タグ"
  - "<listheader> C# XML タグ"
  - "item C# XML タグ"
  - "list C# XML タグ"
  - "listheader C# XML タグ"
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# &lt;list&gt; (C# プログラミング ガイド)
## 構文  
  
```  
<list type="bullet" | "number" | "table">  
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
 `term`  
 定義する用語。定義は、`description` に記述されます。  
  
 `description`  
 箇条書きリストまたは番号付きリストの項目、あるいは `term` の定義のいずれか。  
  
## 解説  
 \<listheader\> ブロックは、表または定義リストの見出し行の定義に使用します。  表を定義する場合は、見出しには用語のエントリだけを指定します。  
  
 リストの各項目は、\<item\> ブロックで指定します。  定義リストを作成するときは、`term` と `description` の両方を指定します。  ただし、表、箇条書きリスト、または番号付きリストに指定する必要があるのは、`description` のエントリだけです。  
  
 リストや表には、必要な数だけ \<item\> ブロックを指定できます。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/list_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)