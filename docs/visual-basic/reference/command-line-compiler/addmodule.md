---
title: /addmodule
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fff292605e125776ae25e667d4813d770ed0a0aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule"></a>/addmodule
指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a>引数  
 `fileList`  
 必須です。 メタデータが含まれますが、アセンブリ マニフェストが含まれていないファイルのコンマ区切り一覧。 空白を含むファイル名を引用符で囲む必要があります ("") です。  
  
## <a name="remarks"></a>コメント  
 によって示されているファイル、`fileList`パラメーターを使って作成する必要があります、`/target:module`オプション、または別のコンパイラのと同じ`/target:module`です。  
  
 追加したすべてのモジュール`/addmodule`実行時に、出力ファイルと同じディレクトリにする必要があります。 つまり、コンパイル時に、任意のディレクトリにモジュールを指定することができますが、モジュールは、実行時にアプリケーションのディレクトリにする必要があります。 そうでない場合、<xref:System.TypeLoadException>エラーです。  
  
 (暗黙的または明示的に) を指定する場合、[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)以外のオプション`/target:module`で`/addmodule`に渡すファイル`/addmodule`プロジェクトのアセンブリの一部になります。 アセンブリが 1 つの出力ファイルを実行するために必要なまたは以上のファイル追加`/addmodule`です。  
  
 使用して[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)アセンブリが格納されているファイルからメタデータをインポートします。  
  
> [!NOTE]
>  `/addmodule`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードでは、モジュールを作成します。  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 次のコードでは、モジュールの型をインポートします。  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 実行すると`t1`、出力`802`です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
