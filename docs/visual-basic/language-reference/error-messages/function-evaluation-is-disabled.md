---
title: "前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords: BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05067e730486b443b7a508adb499f34c060d5093
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。
前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。関数の評価をもう一度有効にするには、もう一度ステップを実行するか、またはデバッグを再起動してください。  
  
 Visual Studio デバッガーで、プロシージャ呼び出しが式に指定されていますが、別の評価がタイムアウトしています。  
  
 プロシージャ呼び出しがタイムアウトの原因が考えられます、無限ループまたは*無限ループ*です。 詳細については、次を参照してください[をしています.。次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)します。  
  
 無限ループの特殊なケースは*再帰*です。 詳細については、次を参照してください。[再帰プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)です。  
  
 **エラー ID:** BC30957  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  可能であれば、前回の関数の評価がどれかを判断し、タイムアウトした理由を調べます。判断できない場合、このエラーが再度表示される可能性があります。  
  
2.  デバッガーのステップをもう一度実行するか、デバッガーを終了させて再起動します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)  
 [デバッガーでのコード間の移動](/visualstudio/debugger/navigating-through-code-with-the-debugger)
