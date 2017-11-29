---
title: /noconfig
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94d13ccf0168027f4560b980c41e2a001ff503fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig"></a>/noconfig
コンパイラいない自動的を参照することはよく使用される指定[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリまたはインポート、`System`と`Microsoft.VisualBasic`名前空間。  
  
## <a name="syntax"></a>構文  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a>コメント  
 `/noconfig`オプション Vbc.exe ファイルと同じディレクトリにある Vbc.rsp ファイルでコンパイルしていないコンパイラに指示します。 Vbc.rsp ファイルを参照して、一般的に使用される[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリとインポート、`System`と`Microsoft.VisualBasic`名前空間。 コンパイラは、System.dll アセンブリを暗黙的に参照しない限り、`/nostdlib`オプションを指定します。 `/nostdlib`オプションは、コンパイラが Vbc.rsp でコンパイルするか、System.dll アセンブリを自動的に参照を指定します。  
  
> [!NOTE]
>  Mscorlib.dll および Microsoft.VisualBasic.dll のアセンブリは、常に参照されます。  
  
 Vbc.exe のコンパイルごとに含める必要がある追加のコンパイラ オプションを指定する Vbc.rsp ファイルを変更することができます (を指定する場合を除いて、`/noconfig`オプション)。 詳しくは、「[@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)」をご覧ください。  
  
 コンパイラに渡されるオプションの処理、`vbc`最後コマンドします。 そのため、コマンドラインに指定したオプションは、Vbc.rsp ファイル内の同じオプションの設定を上書きします。  
  
> [!NOTE]
>  `/noconfig`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="see-also"></a>関連項目  
 [/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
