---
title: "/highentropyva (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 34987930b3afd6d95d12190172a5a5e512106f8a
ms.lasthandoff: 03/13/2017

---
# <a name="highentropyva-visual-basic"></a>/highentropyva (Visual Basic)
示す、64 ビット実行可能ファイルまたは実行可能ファイルでマークされているかどうか、 [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md)コンパイラ オプションは、高エントロピ ASLR Address Space Layout Randomization () をサポートしています。  
  
## <a name="syntax"></a>構文  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 省略可能です。 オプションは既定で無効または指定した`/highentropyva-`します。 指定したかどうかに、オプションは、`/highentropyva`または`/highentropyva+`です。  
  
## <a name="remarks"></a>コメント  
 このオプションを指定する場合、Windows カーネルのバージョンに互換性のあるは、カーネル プロセスのアドレス領域のレイアウトを ASLR の一部としてランダムにときにより高度なエントロピーを使用できます。 カーネルより高度なエントロピーを使用している場合、スタックとヒープなどのメモリ領域にアドレスの数が多いを割り当てることができます。 その結果、特定のメモリ領域の位置を推測するより困難です。  
  
 オプションが、ターゲットの実行可能ファイルとすべてのモジュールでのこれらのモジュールは、64 ビット プロセスとして実行しているときに、4 ギガバイト (GB) よりも大きくポインター値を処理できない依存している必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
