---
title: '&lt;seealso&gt; (C# プログラミング ガイド)'
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e3c9d68884e5cd4f5a4f81580f60cdde775458a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349136"
---
# <a name="ltseealsogt-c-programming-guide"></a>&lt;seealso&gt; (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>パラメーター  
 cref = "`member`"  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。 コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。`member` は二重引用符 (" ") で囲む必要があります。  
  
 ジェネリック型への cref 参照を作成する方法については、「[\<see>](../../../csharp/programming-guide/xmldoc/see.md)」を参照してください。  
  
## <a name="remarks"></a>コメント  
 \<seealso > タグを使用して、「See Also」セクションに表示するテキストを指定することができます。 [\<see>](../../../csharp/programming-guide/xmldoc/see.md) タグを使用すると、テキスト内からリンクを指定できます。  
  
 コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 \<seealso> の使用例については、[\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) を参照してください。  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
