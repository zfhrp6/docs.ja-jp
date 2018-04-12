---
title: XML コメントの例外があります、&#39; cref &#39;属性
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c22c9cd9415faf17d027c3751d166662a92b50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>XML コメントの例外があります、&#39; cref &#39;属性
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
