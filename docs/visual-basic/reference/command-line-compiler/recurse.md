---
title: /recurse
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb69c7c44dcc2e8da5eb8a76f7d22f936a6d948f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="recurse"></a>/recurse
指定されたディレクトリまたはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルします。  
  
## <a name="syntax"></a>構文  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引数  
 `dir`  
 省略可能です。 検索を開始するディレクトリ。 指定しない場合、プロジェクト ディレクトリ内で検索を開始します。  
  
 `file`  
 必須です。 検索するファイル。 ワイルドカード文字を使用できます。  
  
## <a name="remarks"></a>コメント  
 ファイル名にワイルドカードを使用して、プロジェクト ディレクトリ内のすべての一致するファイルを使用せずにコンパイルできます`/recurse`です。 出力ファイル名が指定されていない場合、コンパイラは処理される最初の入力ファイルに出力ファイル名に基づいて行います。 これは、一般に、アルファベット順に表示されるときにコンパイルされたファイルの一覧の最初のファイルです。 この理由は、使用して出力ファイルを指定することをお、`/out`オプション。  
  
> [!NOTE]
>  `/recurse`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードをコンパイルすべて[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]現在のディレクトリ内のファイルです。  
  
```  
vbc *.vb  
```  
  
 すべて次のコードをコンパイル[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]内のファイル、`Test\ABC`ディレクトリと、その下には、そのディレクトリを生成し、`Test.ABC.dll`です。  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
