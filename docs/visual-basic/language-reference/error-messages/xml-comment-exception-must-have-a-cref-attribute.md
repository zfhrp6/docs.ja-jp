---
title: XML コメントの例外があります、 &#39;cref&#39;属性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: ee91513ef94e2abbe01d3ac09796b7fdf8e129ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597384"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>XML コメントの例外があります、 &#39;cref&#39;属性
\<例外 > タグは、メソッドによってスローされる可能性がありますのある例外を文書化する方法を提供します。 必要な`cref`属性は、ドキュメント ジェネレーターによってチェックされているメンバーの名前を指定します。 メンバーが存在する場合は、ドキュメント ファイル内の標準要素名に変換されます。  
  
 **エラー ID:** BC42319  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   追加、`cref`属性は、例外を次のようにします。  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>関連項目  
 [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
