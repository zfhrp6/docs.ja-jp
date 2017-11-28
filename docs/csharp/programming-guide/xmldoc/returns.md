---
title: "&lt;returns&gt; (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0313e9584ae6a94469db17e15f8b6b509b8aebd5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltreturnsgt-c-programming-guide"></a>&lt;returns&gt; (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `description`  
 戻り値の説明。  
  
## <a name="remarks"></a>コメント  
 \<returns> タグは、戻り値を説明するためにメソッドの宣言のコメントで使用する必要があります。  
  
 コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#10](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/returns_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
