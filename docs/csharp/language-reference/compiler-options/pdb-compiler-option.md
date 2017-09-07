---
title: "-pdb (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /pdb
dev_langs:
- CSharp
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: 8
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
ms.openlocfilehash: 7c72c12347a9096aeed063b84310356cb07b49c3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="pdb-c-compiler-options"></a>/pdb (C# コンパイラ オプション)
**/pdb** コンパイラ オプションは、デバッグ シンボル ファイルの場所と名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
/pdb:filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 デバッグ シンボル ファイルの名前と場所です。  
  
## <a name="remarks"></a>コメント  
 [/debug (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) を指定すると、コンパイラは、コンパイラが出力ファイル (.exe または .dll) を作成するのと同じディレクトリに、出力ファイルと同じ名前のファイル名で .pdb ファイルを作成します。  
  
 **/pdb** では、.pdb ファイルに対し、既定以外のファイル名と場所を指定することができます。  
  
 このコンパイラ オプションは、Visual Studio 開発環境で設定することはできません。また、プログラムで変更することもできません。  
  
## <a name="example"></a>例  
 `t.cs` をコンパイルして、tt.pdb と呼ばれる .pdb ファイルを作成します。  
  
```console  
csc /debug /pdb:tt t.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)

