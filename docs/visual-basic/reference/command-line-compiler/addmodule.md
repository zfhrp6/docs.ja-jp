---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2fefdf81ab25d2e109f265f0c895a3415ad5673d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656007"
---
# <a name="-addmodule"></a>-addmodule
指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>引数  
 `fileList`  
 必須。 メタデータが含まれますが、アセンブリ マニフェストが含まれていないファイルのコンマ区切り一覧。 空白を含むファイル名を引用符で囲む必要があります ("") です。  
  
## <a name="remarks"></a>コメント  
 によって示されているファイル、`fileList`パラメーターを使って作成する必要があります、`-target:module`オプション、または別のコンパイラのと同じ`-target:module`です。  
  
 追加したすべてのモジュール`-addmodule`実行時に、出力ファイルと同じディレクトリにする必要があります。 つまり、コンパイル時に、任意のディレクトリにモジュールを指定することができますが、モジュールは、実行時にアプリケーションのディレクトリにする必要があります。 そうでない場合、<xref:System.TypeLoadException>エラーです。  
  
 (暗黙的または明示的に) を指定する場合、[-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)以外のオプション`-target:module`で`-addmodule`に渡すファイル`-addmodule`プロジェクトのアセンブリの一部になります。 アセンブリが 1 つの出力ファイルを実行するために必要なまたは以上のファイル追加`-addmodule`です。  
  
 使用して[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)アセンブリが格納されているファイルからメタデータをインポートします。  
  
> [!NOTE]
>  `-addmodule`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードでは、モジュールを作成します。  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 次のコードでは、モジュールの型をインポートします。  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 実行すると`t1`、出力`802`です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-参照 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
