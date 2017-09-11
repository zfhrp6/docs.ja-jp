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
# <a name="pdb-c-compiler-options"></a><span data-ttu-id="4b1b0-102">/pdb (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="4b1b0-102">/pdb (C# Compiler Options)</span></span>
<span data-ttu-id="4b1b0-103">**/pdb** コンパイラ オプションは、デバッグ シンボル ファイルの場所と名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b1b0-103">The **/pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b1b0-104">構文</span><span class="sxs-lookup"><span data-stu-id="4b1b0-104">Syntax</span></span>  
  
```console  
/pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b1b0-105">引数</span><span class="sxs-lookup"><span data-stu-id="4b1b0-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="4b1b0-106">デバッグ シンボル ファイルの名前と場所です。</span><span class="sxs-lookup"><span data-stu-id="4b1b0-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b1b0-107">コメント</span><span class="sxs-lookup"><span data-stu-id="4b1b0-107">Remarks</span></span>  
 <span data-ttu-id="4b1b0-108">[/debug (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) を指定すると、コンパイラは、コンパイラが出力ファイル (.exe または .dll) を作成するのと同じディレクトリに、出力ファイルと同じ名前のファイル名で .pdb ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4b1b0-108">When you specify [/debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="4b1b0-109">**/pdb** では、.pdb ファイルに対し、既定以外のファイル名と場所を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="4b1b0-109">**/pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="4b1b0-110">このコンパイラ オプションは、Visual Studio 開発環境で設定することはできません。また、プログラムで変更することもできません。</span><span class="sxs-lookup"><span data-stu-id="4b1b0-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b1b0-111">例</span><span class="sxs-lookup"><span data-stu-id="4b1b0-111">Example</span></span>  
 <span data-ttu-id="4b1b0-112">`t.cs` をコンパイルして、tt.pdb と呼ばれる .pdb ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4b1b0-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc /debug /pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b1b0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b1b0-113">See Also</span></span>  
 <span data-ttu-id="4b1b0-114">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b1b0-114">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="4b1b0-115">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="4b1b0-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

