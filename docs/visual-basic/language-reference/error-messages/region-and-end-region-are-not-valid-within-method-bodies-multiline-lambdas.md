---
title: '&#39;#Region&#39;と&#39;#End Region&#39;ステートメントはメソッド本体に複数行ラムダでは有効ではありません。'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: bf3843e0ec3009f3dc7d60e91c340a7f20543231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593234"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39;#Region&#39;と&#39;#End Region&#39;ステートメントはメソッド本体や複数行ラムダでは有効ではありません。
`#Region`ブロックは、クラス、モジュール、または名前空間レベルで宣言する必要があります。 折りたたみ可能な領域が 1 つ以上のプロシージャを含めることができますが、開始日または終了、プロシージャ内でそのことはできません。  
  
 **エラー ID:** BC32025  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  前の手順がで正常終了したことを確認してください、`End Function`または`End Sub`ステートメントです。  
  
2.  いることを確認、`#Region`と`#End Region`ディレクティブが同じコード ブロックではします。  
  
## <a name="see-also"></a>関連項目  
 [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)
