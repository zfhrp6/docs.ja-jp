---
title: /utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23c7c308865a6b6afb07443a42090fff3d9e2efb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="utf8output-visual-basic"></a>/utf8output (Visual Basic)
UTF-8 エンコードを使用してコンパイラ出力を表示します。  
  
## <a name="syntax"></a>構文  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 省略可能です。 このオプションの既定値は`/utf8output-`、つまり、コンパイラの出力は utf-8 エンコードを使用しません。 指定する`/utf8output`を指定することと同じ`/utf8output+`です。  
  
## <a name="remarks"></a>コメント  
 国際対応の構成によっては、コンパイラの出力は、コンソールで正常に表示できません。 このような状況で使用して`/utf8output`してコンパイラ出力をファイルにリダイレクトします。  
  
> [!NOTE]
>  `/utf8output`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`表示をコンパイラに指示して utf-8 エンコードを使用して出力します。  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
