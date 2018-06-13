---
title: この配列は固定か、または一時的にロックされています。(Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: e912bd202603d9a0f427418708ad584c7d6203e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593565"
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
