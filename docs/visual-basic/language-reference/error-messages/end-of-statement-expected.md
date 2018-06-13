---
title: ステートメントの終わりを指定してください。
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 7b91d13cbcb9d211d4ca18c8e48c7494bf6eccc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588081"
---
# <a name="end-of-statement-expected"></a>ステートメントの終わりを指定してください。
ステートメントが構文的に完了するが、その他のプログラミング要素に依存してステートメントを終了する要素。 行終端記号が、すべてのステートメントの末尾に必要です。
  
 行終端記号は、Visual Basic のソース ファイルの文字を行に分割します。 行の終端記号の例としては、Unicode キャリッジ リターン文字 (& HD) を Unicode とライン フィード文字 (& HA)、Unicode キャリッジ リターン Unicode 改行文字が続く文字とします。 行の終端記号の詳細については、次を参照してください。、 [Visual Basic 言語仕様](../../../visual-basic/reference/language-specification/index.md)です。
  
 **エラー ID:** BC30205
  
## <a name="to-correct-this-error"></a>このエラーを解決するには
  
1.  2 つの異なるステートメントが同じ行に格納された誤ってかどうかを確認します。
  
2.  ステートメントを終了する要素の後に、行終端記号を挿入します。
  
## <a name="see-also"></a>関連項目  
 [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
