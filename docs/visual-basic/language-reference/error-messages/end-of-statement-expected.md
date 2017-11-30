---
title: "ステートメントの終わりを指定してください。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords: BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4934952015cb4871bcd90cef982eab5425b1617f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
