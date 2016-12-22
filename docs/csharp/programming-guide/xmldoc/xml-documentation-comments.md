---
title: "XML ドキュメント コメント (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.xml"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, XML コード コメント"
  - "C# ソース コード ファイル"
  - "コメント [C#], XML"
  - "ドキュメント コメント [C#]"
  - "XML [C#], コードのコメント"
  - "XML ドキュメント コメント [C#]"
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# XML ドキュメント コメント (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual C\# では、ソース コード内で、コード ブロックの直前の特別なコメント フィールド \(3 個のスラッシュで示す\) に XML 要素を配置することで、コードのドキュメントを作成できます。例を次に示します。  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) オプションを使用してコンパイルすると、コンパイラは、ソース コード内のすべての XML タグを検索して、XML ドキュメント ファイルを作成します。  コンパイラによって生成されたファイルに基づいて最終的なドキュメントを作成するには、カスタム ツールを作成するか、[Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061) などのツールを使用します。  
  
 XML 要素を参照するには \(たとえば、XML ドキュメント コメントに記述する特定の XML 要素を関数で処理する場合\)、標準の引用のしくみを使用できます \(`<` と `>`\)。コード参照 \(`cref`\) 要素でジェネリック識別子を参照するには、エスケープ文字 \(たとえば、`cref="List<T>"`\) または中かっこ \(`cref="List{T}"`\) を使用できます。特殊なケースとして、コンパイラは中かっこを山かっことして解析し、ジェネリック識別子を参照するときにドキュメント コメントの編集があまり面倒にならないようにしています。  
  
> [!NOTE]
>  XML ドキュメント コメントはメタデータではなく、コンパイルされたアセンブリに含まれないため、リフレクションでアクセスできません。  
  
## このセクションの内容  
  
-   [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [XML ファイルの処理](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [ドキュメント タグの区切り記号](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [方法 : XML ドキュメント機能を使用する \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## 関連項目  
 詳細については、次のトピックを参照してください。  
  
-   [\/doc \(ドキュメント コメントの処理\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)