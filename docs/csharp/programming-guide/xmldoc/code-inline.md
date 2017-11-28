---
title: "&lt;c&gt; (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 21c7830c03b0b93e3597835954ac9e7d2feb49e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcgt-c-programming-guide"></a>&lt;c&gt; (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `text`  
 コードとして指定するテキストです。  
  
## <a name="remarks"></a>コメント  
 \<c> タグを使用すると、説明内のテキストをコードとして指定できます。 複数行をコードとして指定する場合は、[\<code>](../../../csharp/programming-guide/xmldoc/code.md) タグを使用します。  
  
 コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
