---
title: /nostdlib (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9d76563a5b3d439495899e07ce2df59c0acd75e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nostdlib-visual-basic"></a>/nostdlib (Visual Basic)
コンパイラが自動的に標準のライブラリを参照します。  
  
## <a name="syntax"></a>構文  
  
```  
/nostdlib  
```  
  
## <a name="remarks"></a>コメント  
 `/nostdlib`オプションは、System.dll アセンブリへの自動参照を削除し、コンパイラが Vbc.rsp ファイルを読み取ることを防止します。 Vbc.rsp ファイル-Vbc.exe ファイルと同じディレクトリに配置された: 一般的に使用される参照[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリとインポート、`System`と`Microsoft.VisualBasic`名前空間。  
  
> [!NOTE]
>  Mscorlib.dll および Microsoft.VisualBasic.dll のアセンブリは、常に参照されます。  
  
> [!NOTE]
>  `/nostdlib`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`標準ライブラリを参照することがなくです。 設定する必要があります、`_MYTYPE`条件付きコンパイル定数を削除するには、「空白」の文字列に、`My`オブジェクト。  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
