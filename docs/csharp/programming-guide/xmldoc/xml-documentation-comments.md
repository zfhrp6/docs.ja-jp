---
title: "XML ドキュメント コメント (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.xml
dev_langs:
- CSharp
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0762bd31ef7732ac6ed91a10aead9dca8050f862
ms.lasthandoff: 03/13/2017

---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML ドキュメント コメント (C# プログラミング ガイド)
Visual C# では、ソース コード内で、コード ブロックの直前の特別なコメント フィールド (3 個のスラッシュで示す) に XML 要素を配置することで、コードのドキュメントを作成できます。例を次に示します。  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) オプションを使用してコンパイルすると、コンパイラは、ソース コード内のすべての XML タグを検索して、XML ドキュメント ファイルを作成します。 コンパイラによって生成されたファイルに基づいて最終的なドキュメントを作成するには、カスタム ツールを作成するか、[Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061) などのツールを使用します。  
  
 XML 要素を参照するには (たとえば、XML ドキュメント コメントに記述する特定の XML 要素を関数で処理する場合)、標準の引用のしくみを使用できます (`<` と `>`)。  コード参照 (`cref`) 要素でジェネリック識別子を参照するには、エスケープ文字 (たとえば、`cref=”List<T>”`) または中かっこ (`cref=”List{T}”`) を使用できます。  特殊なケースとして、コンパイラは中かっこを山かっことして解析し、ジェネリック識別子を参照するときにドキュメント コメントの編集があまり面倒にならないようにしています。  
  
> [!NOTE]
>  XML ドキュメント コメントはメタデータではなく、コンパイルされたアセンブリに含まれないため、リフレクションでアクセスできません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [XML ファイルの処理](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [ドキュメント タグの区切り記号](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [方法: XML ドキュメント機能を使用する (C# プログラミング ガイド)](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a>関連項目  
 詳細については次を参照してください:  
  
-   [/doc (ドキュメント コメントの処理)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
