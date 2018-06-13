---
title: '&lt;see&gt; (C# プログラミング ガイド)'
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 24fa317a0f89568d9aa1b53849e327ef7615cc7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348792"
---
# <a name="ltseegt-c-programming-guide"></a>&lt;see&gt; (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>パラメーター  
 cref = "`member`"  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。 コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。*member* は二重引用符で囲んで配置します。  
  
## <a name="remarks"></a>コメント  
 \<see> タグを使用すると、テキスト内でリンクを指定できます。 テキストが参照セクションに配置されていることを示すには、[\<<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) を使用します。 コード要素のドキュメント ページへの内部ハイパーリンクを作成するには、[cref 属性](../../../csharp/programming-guide/xmldoc/cref-attribute.md)を使用します。  
  
 コンパイル時に [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
 次の例では、summary セクション内の \<see> タグを示しています。  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
