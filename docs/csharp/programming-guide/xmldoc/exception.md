---
title: '&lt;例外&gt; (C# プログラミング ガイド)'
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: eca61416077896c9fa7d5828bbab79b399ad69d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltexceptiongt-c-programming-guide"></a>&lt;例外&gt; (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>パラメーター  
 cref = "`member`"  
 現在のコンパイル環境から使用できる例外の参照。 コンパイラは、指定された例外が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。 `member` は、二重引用符 (" ") で囲む必要があります。  
  
 ジェネリック型への cref 参照を作成する方法については、[\<see>](../../../csharp/programming-guide/xmldoc/see.md) を参照してください。  
  
 `description`  
 例外の説明。  
  
## <a name="remarks"></a>コメント  
 \<exception> タグを使用すると、スローできる例外を指定できます。 このタブは、メソッド、プロパティ、イベント、インデクサーの定義に適用できます。  
  
 コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。  
  
 例外処理の詳細については、「[例外と例外処理](../../../csharp/programming-guide/exceptions/index.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
