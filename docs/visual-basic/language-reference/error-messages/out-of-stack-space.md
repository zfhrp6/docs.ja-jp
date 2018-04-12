---
title: スタック領域が不足しています。(Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3959c24aa4e95204e156a9863ef0ce237af1fcda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="out-of-stack-space-visual-basic"></a>スタック領域が不足しています。(Visual Basic)
スタックは、実行しているプログラムの要求で動的に拡大および縮小するメモリの作業領域です。 上限を超えました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  プロシージャが深すぎます。 入れ子にできないことを確認してください。  
  
2.  再帰プロシージャが正常に終了することを確認します。  
  
3.  ローカル変数では、ローカル変数領域を超える領域がある必要がある場合は、モジュール レベルでのいくつかの変数を宣言してみてください。 宣言することも、プロシージャのすべての変数静的前に追加して、 `Property`、 `Sub`、または`Function`キーワード`Static`です。 使用することができます、`Static`ステートメントをプロシージャ内で個別に静的変数を宣言します。  
  
4.  固定長文字列可変長文字列よりも多くのスタック領域を使用すると、可変長文字列として、固定長文字列の一部を再定義します。 ここでは必要ありませんスタック領域モジュール レベルで文字列を定義することもできます。  
  
5.  数を確認して入れ子になった`DoEvents`関数を使用して呼び出し、`Calls`ダイアログ ボックスで、スタック上でアクティブなプロシージャ ビューをします。  
  
6.  スタックで既にイベント プロシージャを呼び出すイベントをトリガーすることによって、「イベントの連鎖」を発生しないことを確認してください。 イベント cascade は、未終了の再帰的なプロシージャの呼び出しに似ていますが、によって呼び出されるために、わかりにくくが[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]のコード内の明示的な呼び出しではなくです。 使用して、`Calls`ダイアログ ボックスで、スタック上でアクティブなプロシージャ ビューをします。  
  
## <a name="see-also"></a>関連項目  
 [[メモリ] ウィンドウ](/visualstudio/debugger/memory-windows)
