---
title: "@ (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '@'
dev_langs:
- CSharp
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 219c12e4e3c9b847400f00a135d58506c72d2e7f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-c-compiler-options"></a>@ (C# コンパイラ オプション)
@ オプションを使用すると、コンパイラ オプションおよびコンパイルするソース コード ファイルを含むファイルを指定できます。  
  
## <a name="syntax"></a>構文  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>引数  
 `response_file`  
 コンパイラ オプションやコンパイルするソース コード ファイルの一覧を含むファイルです。  
  
## <a name="remarks"></a>コメント  
 コンパイラ オプションとソース コード ファイルは、コマンド ラインで指定した場合と同じように、コンパイラによって処理されます。  
  
 コンパイル時に複数の応答ファイルを指定するには、複数の応答ファイル オプションを指定します。 例:  
  
```  
@file1.rsp @file2.rsp  
```  
  
 応答ファイルでは、複数のコンパイラ オプションとソース コード ファイルを 1 行に記述できます。 1 つのコンパイラ オプションは 1 行に指定する必要があり、複数行にわたって指定できません。 応答ファイルには、シャープ記号 (#) で始まるコメントを記述できます。  
  
 応答ファイルでのコンパイラ オプションの指定方法は、コマンド ラインでのコンパイラ オプションの指定方法と同じです。 詳細については、「[Building from the Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)」(コマンド ラインからのビルド) を参照してください。  
  
 コンパイラは、検出した順にコマンド オプションを処理します。 このため、コマンド ライン引数によって、応答ファイルで先に指定したオプションをオーバーライドできます。 逆に、応答ファイルのオプションが、コマンド ラインや他の応答ファイルで先に指定したオプションをオーバーライドすることもあります。  
  
 C# では、csc.exe ファイルと同じディレクトリに csc.rsp ファイルがあります。 csc.rsp の詳細については、「[/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)」を参照してください。  
  
 このコンパイラ オプションは、Visual Studio 開発環境で設定することはできません。また、プログラムで変更することもできません。  
  
## <a name="example"></a>例  
 サンプルの応答ファイルの一部を次に示します。  
  
```console  
# build the first output file  
/target:exe /out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)

