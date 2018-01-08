---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e157fb0e1fcdb3899440eed02a42b16f75541989
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="optimize"></a>/optimize
有効またはコンパイラの最適化を無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`+` &#124; `-`|任意。 `/optimize-`オプションは、コンパイラの最適化を無効になります。 `/optimize+`最適化を有効にします。 既定では、最適化が無効になります。|  
  
## <a name="remarks"></a>コメント  
 コンパイラを最適化すると、出力ファイルのサイズが小さくなり、動作が速くなり、処理の効率が向上します。 ただし、出力ファイルでコードの再配置の最適化を行うので、`/optimize+`デバッグが困難です。  
  
 生成されるすべてのモジュール`/target:module`アセンブリを使用する必要があります同じ`/optimize`アセンブリとして設定します。 詳細については、次を参照してください。 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)です。  
  
 組み合わせることができます、`/optimize`と`/debug`オプション。  
  
|Visual Studio 統合開発環境で/optimize を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。<br />     <br />2.**[コンパイル]** タブをクリックします。<br />3.**[詳細設定]** ボタンをクリックします。<br />4.変更、**の最適化を有効にする**チェック ボックスをオンします。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`とコンパイラの最適化を有効にします。  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a>参照  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
