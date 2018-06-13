---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd5dde46cdea67825b14a6f5fa96a82c8bab8d3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652423"
---
# <a name="-recurse"></a>-recurse
指定されたディレクトリまたはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルします。  
  
## <a name="syntax"></a>構文  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引数  
 `dir`  
 任意。 検索を開始するディレクトリ。 指定しない場合、プロジェクト ディレクトリ内で検索を開始します。  
  
 `file`  
 必須。 検索するファイル。 ワイルドカード文字を使用できます。  
  
## <a name="remarks"></a>コメント  
 ファイル名にワイルドカードを使用して、プロジェクト ディレクトリ内のすべての一致するファイルを使用せずにコンパイルできます`-recurse`です。 出力ファイル名が指定されていない場合、コンパイラは処理される最初の入力ファイルに出力ファイル名に基づいて行います。 これは、一般に、アルファベット順に表示されるときにコンパイルされたファイルの一覧の最初のファイルです。 この理由は、使用して出力ファイルを指定することをお、`-out`オプション。  
  
> [!NOTE]
>  `-recurse`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコマンドは、現在のディレクトリ内のすべての Visual Basic ファイルをコンパイルします。  
  
```console
vbc *.vb  
```  
  
 次のコマンドですべての Visual Basic ファイルのコンパイル、`Test\ABC`ディレクトリと、その下には、そのディレクトリを生成し、`Test.ABC.dll`です。  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-除外 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
