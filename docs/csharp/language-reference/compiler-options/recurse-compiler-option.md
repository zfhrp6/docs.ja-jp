---
title: "-recurse (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /recurse
dev_langs:
- CSharp
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: 12
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
ms.openlocfilehash: 99664f8b32f5f9e5bf491c5bfde2c1649de42dd9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="recurse-c-compiler-options"></a><span data-ttu-id="7b3d6-102">/recurse (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="7b3d6-102">/recurse (C# Compiler Options)</span></span>
<span data-ttu-id="7b3d6-103">/recurse オプションを使用すると、指定のディレクトリ (dir) またはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="7b3d6-103">The /recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b3d6-104">構文</span><span class="sxs-lookup"><span data-stu-id="7b3d6-104">Syntax</span></span>  
  
```console  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b3d6-105">引数</span><span class="sxs-lookup"><span data-stu-id="7b3d6-105">Arguments</span></span>  
 <span data-ttu-id="7b3d6-106">`dir` (省略可能)</span><span class="sxs-lookup"><span data-stu-id="7b3d6-106">`dir` (optional)</span></span>  
 <span data-ttu-id="7b3d6-107">検索を開始するディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="7b3d6-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="7b3d6-108">指定しない場合は、プロジェクト ディレクトリから検索されます。</span><span class="sxs-lookup"><span data-stu-id="7b3d6-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="7b3d6-109">検索するファイル。</span><span class="sxs-lookup"><span data-stu-id="7b3d6-109">The file(s) to search for.</span></span> <span data-ttu-id="7b3d6-110">ワイルドカード文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b3d6-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b3d6-111">コメント</span><span class="sxs-lookup"><span data-stu-id="7b3d6-111">Remarks</span></span>  
 <span data-ttu-id="7b3d6-112">**/recurse** オプションを使用すると、指定のディレクトリ (`dir`) またはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="7b3d6-112">The **/recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="7b3d6-113">**/recurse** を使用しなくても、ファイル名にワイルドカードを使用すると、プロジェクト ディレクトリ内で一致するすべてのファイルをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="7b3d6-113">You can use wildcards in a file name to compile all matching files in the project directory without using **/recurse**.</span></span>  
  
 <span data-ttu-id="7b3d6-114">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="7b3d6-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b3d6-115">例</span><span class="sxs-lookup"><span data-stu-id="7b3d6-115">Example</span></span>  
 <span data-ttu-id="7b3d6-116">現在のディレクトリ内のすべての C# ファイルをコンパイルするには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b3d6-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="7b3d6-117">dir1\dir2 ディレクトリおよびそのディレクトリの下の全ディレクトリ内の C# ファイルすべてをコンパイルし、dir2.dll を生成するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b3d6-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc /target:library /out:dir2.dll /recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b3d6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b3d6-118">See Also</span></span>  
 <span data-ttu-id="7b3d6-119">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="7b3d6-119">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="7b3d6-120">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="7b3d6-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

