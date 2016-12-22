---
title: "ドキュメント コメント用の推奨タグ (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "XML [C#]、タグ"
  - "XML ドキュメント [C#]、タグ"
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ドキュメント コメント用の推奨タグ (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コード内のドキュメント コメントは、C\# コンパイラによって処理され、**\/doc** コマンド ライン オプションで指定した名前のファイルに XML 形式で出力されます。  コンパイラによって生成されたファイルに基づいて最終的なドキュメントを作成するには、カスタム ツールを作成するか、ツールを [Sandcastle](http://shfb.codeplex.com/)使用します。  
  
 タグは、型や型メンバーなどのコードの構成体に対して処理されます。  
  
> [!NOTE]
>  ドキュメント コメントは、名前空間に適用できません。  
  
 C\# コンパイラは、有効な XML のタグをすべて処理します。  ユーザー ドキュメントで一般的に使用される機能を提供するタグを次の表に示します。  
  
## タグ  
  
||||  
|-|-|-|  
|[\<c\>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para\>](../../../csharp/programming-guide/xmldoc/para.md)|[\<see\>](../../../csharp/programming-guide/xmldoc/see.md)\*|  
|[\<code\>](../../../csharp/programming-guide/xmldoc/code.md)|[\<param\>](../../../csharp/programming-guide/xmldoc/param.md)\*|[\<seealso\>](../../../csharp/programming-guide/xmldoc/seealso.md)\*|  
|[\<example\>](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref\>](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<summary\>](../Topic/%3Csummary%3E%20\(C%23%20Programming%20Guide\).md)|  
|[\<exception\>](../../../csharp/programming-guide/xmldoc/exception.md)\*|[\<permission\>](../../../csharp/programming-guide/xmldoc/permission.md)\*|[\<typeparam\>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*|  
|[\<include\>](../../../csharp/programming-guide/xmldoc/include.md)\*|[\<remarks\>](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref\>](../Topic/%3Ctypeparamref%3E%20\(C%23%20Programming%20Guide\).md)|  
|[\<list\>](../../../csharp/programming-guide/xmldoc/list.md)|[\<returns\>](../../../csharp/programming-guide/xmldoc/returns.md)|[\<value\>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 \(\* は、コンパイラが構文を検証することを示します\)  
  
 ドキュメント コメントのテキストに山かっこを表示する場合は、次の例に示すように `<` と `>` を使用します。  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [XML ドキュメント コメント](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)