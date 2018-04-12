---
title: この配列は固定か、または一時的にロックされています。(Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adff10d4ae61e45402df64ebaa3baf146371ff9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>この配列は固定か、または一時的にロックされています。(Visual Basic)
このエラーには、次の考えられる原因があります。  
  
-   使用して`ReDim`固定サイズの配列の要素の数を変更します。  
  
-   1 つの要素が渡されている引数としてプロシージャに、モジュール レベル動的配列の次元です。 配列を防ぐためにロックされている要素が渡された場合、プロシージャ内での参照パラメーターのメモリ割り当てを解除します。  
  
-   値を代入しようとして、 `Variant` 、配列を含む変数が、`Variant`現在ロックされています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  元の配列を作成してと共に宣言することにより固定ではなく動的`ReDim`(配列が宣言されているプロシージャ内で)、または (配列は、モジュール レベルで宣言されて場合、要素の数を指定せずに宣言しています。  
  
2.  本当にモジュール内のすべてのプロシージャ内で参照可能であるため、要素を渡す必要があるかどうかを決定します。  
  
3.  新機能がロックを判断、`Variant`およびそれを解決します。  
  
## <a name="see-also"></a>関連項目  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
