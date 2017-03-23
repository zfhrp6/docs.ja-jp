---
title: "/addmodule |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 949962905ec933dc42301bf8c21654e73dbe2f70
ms.lasthandoff: 03/13/2017

---
# <a name="addmodule"></a>/addmodule
指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a>引数  
 `fileList`  
 必須です。 メタデータが含まれますが、アセンブリのマニフェストが含まれていないファイルのコンマ区切りリスト。 空白を含むファイル名を引用符で囲む必要があります ("") です。  
  
## <a name="remarks"></a>コメント  
 示されているファイル、`fileList`パラメーターを使って作成する必要があります、`/target:module`オプション、または別のコンパイラのと同じ`/target:module`します。  
  
 追加したすべてのモジュール`/addmodule`実行時に出力ファイルと同じディレクトリにある必要があります。 つまり、コンパイル時に任意のディレクトリにモジュールを指定することができますが、モジュールは、実行時にアプリケーション ディレクトリにある必要があります。 そうでない場合、<xref:System.TypeLoadException>エラー</xref:System.TypeLoadException> 。  
  
 (暗黙的または明示的に) を指定する場合、[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)以外のオプション`/target:module`と`/addmodule`に渡すファイル`/addmodule`プロジェクトのアセンブリの一部になります。 いずれかを含む出力ファイルを実行するアセンブリが必要かで追加された複数のファイル`/addmodule`します。  
  
 使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)アセンブリが格納されているファイルからメタデータをインポートします。  
  
> [!NOTE]
>  `/addmodule`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。  
  
## <a name="example"></a>例  
 次のコードでは、モジュールを作成します。  
  
 [!code-vb[VbVbalrCompiler #&47;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 次のコードでは、モジュールの型をインポートします。  
  
 [!code-vb[VbVbalrCompiler #&48;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 実行すると`t1`、出力`802`します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
