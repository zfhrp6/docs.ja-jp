---
title: '@ (応答ファイルの指定) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad4201dcc094364899984e13c85f2f43a6467ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653625"
---
# <a name="-specify-response-file-visual-basic"></a>@ (応答ファイルの指定) (Visual Basic)
コンパイラ オプションを含むファイルをコンパイルするソース コード ファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>引数  
 `response_file`  
 必須。 ファイルをコンパイルするには、コンパイラ オプションまたはソース コード ファイルの一覧です。 ファイル名を引用符で囲みます ("")、スペースが含まれている場合。  
  
## <a name="remarks"></a>コメント  
 コンパイラは、コンパイラ オプションとコマンド ラインで指定した場合、応答ファイルで指定されたソース コード ファイルを処理します。  
  
 コンパイル時に 1 つ以上の応答ファイルを指定するには、次などの複数の応答ファイル オプションを指定します。  
  
```  
@file1.rsp @file2.rsp  
```  
  
 応答ファイルでは、複数のコンパイラ オプションおよびソース コード ファイルが 1 行に表示されることができます。 コンパイラ オプションの 1 つ指定する必要があります (複数行にまたがることはできません) 1 つの行に表示されます。 応答ファイルで始まるコメントを持つことができます、`#`シンボル。  
  
 1 つまたは複数の応答ファイルで指定されたオプションで、コマンドラインで指定できるオプションを組み合わせることができます。 コンパイラは、検出すると、それらのコマンド オプションを処理します。 したがって、コマンドライン引数は、応答ファイルで指定したオプションをオーバーライドすることができます。 逆に、応答ファイル内のオプションは、前の表に、コマンドラインで、または他の応答ファイルのオプションをオーバーライドします。  
  
 Visual Basic では、Vbc.exe ファイルと同じディレクトリにある Vbc.rsp ファイルを提供します。 しない限り、既定では、Vbc.rsp ファイルが含まれている、`-noconfig`オプションを使用します。 詳細については、次を参照してください。 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)です。  
  
> [!NOTE]
>  `@`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次の行は、サンプルの応答ファイルからです。  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>例  
 次の例で使用する方法、`@`という名前の応答ファイルを持つオプション`File1.rsp`です。  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
