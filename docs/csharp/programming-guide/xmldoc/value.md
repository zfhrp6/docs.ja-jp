---
title: "&lt;value&gt; (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "<value>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<value> C# XML タグ"
  - "value C# XML タグ"
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# &lt;value&gt; (C# プログラミング ガイド)
## 構文  
  
```  
<value>property-description</value>  
```  
  
#### パラメーター  
 `property-description`  
 プロパティの説明。  
  
## 解説  
 \<value\> タグを使用すると、プロパティが表す値の説明を記述できます。  Visual Studio .NET 開発環境のコード ウィザードで追加したプロパティには、[\<summary\>](../../../csharp/programming-guide/xmldoc/summary.md) タグが追加されます。  そのプロパティが表す値を記述するには、\<value\> タグを手動で追加する必要があります。  
  
 コンパイル時に [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
## 使用例  
 [!code-cs[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)