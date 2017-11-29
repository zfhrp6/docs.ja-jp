---
title: "& #39 です。ReDim & #39;右端の次元のみ変更できます。"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 989a06f94824dfd051d1a7d2e7749dbb8c8e11a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>& #39 です。ReDim & #39;右端の次元のみ変更できます。
`ReDim` ステートメントが `Preserve` キーワードを使用して、最後のディメンションではない配列のディメンションを変更しようとしました。 `Preserve`を使用すると、配列の最後のディメンションについてのみ、サイズを変更できます。 他のすべてのディメンションに対しては、既存の配列と同じサイズを指定する必要があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   `Preserve` キーワードを削除します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における配列](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Visual Basic における配列の次元](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [ReDim ステートメント](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Dim ステートメント](../../visual-basic/language-reference/statements/dim-statement.md)  
 [保存 - 削除](http://msdn.microsoft.com/en-us/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
