---
title: "&lt;remarks&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- remarks
- <remarks>
dev_langs:
- CSharp
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
caps.latest.revision: 15
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cd11865fb0d4c8d21294107542fe39ad7e2b690a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltremarksgt-c-programming-guide"></a>&lt;remarks&gt; (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Description`  
 メンバーの説明。  
  
## <a name="remarks"></a>コメント  
 \<remarks> タグを使用して、型の情報を追加し、[\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) で指定された情報を補足します。 この情報はオブジェクト ブラウザー ウィンドウに表示されます。  
  
 コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-cs[csProgGuideDocComments#9](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/remarks_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

