---
title: -pathmap (C# コンパイラ オプション)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 36196ffea19cfde7ff5f830ea358d2bd83edf419
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472815"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="fe65b-102">-pathmap (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="fe65b-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="fe65b-103">**-pathmap** コンパイラ オプションは、コンパイラによるソース パス名出力への物理パスのマップ方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe65b-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="fe65b-104">構文</span><span class="sxs-lookup"><span data-stu-id="fe65b-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="fe65b-105">引数</span><span class="sxs-lookup"><span data-stu-id="fe65b-105">Arguments</span></span>

 <span data-ttu-id="fe65b-106">`path1` 現在の環境でのソース ファイルへの完全なパス</span><span class="sxs-lookup"><span data-stu-id="fe65b-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="fe65b-107">`sourcePath1` 出力ファイルにおいて `path1` の代わりに使用されるソース パス。</span><span class="sxs-lookup"><span data-stu-id="fe65b-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="fe65b-108">複数のマップされるソース パスを指定するには、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="fe65b-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe65b-109">コメント</span><span class="sxs-lookup"><span data-stu-id="fe65b-109">Remarks</span></span>

<span data-ttu-id="fe65b-110">コンパイラは、次の理由でその出力にソース パスを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="fe65b-110">The compiler writes the source path path into its output for the following reasons:</span></span>

1. <span data-ttu-id="fe65b-111"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute> が省略可能なパラメーターに適用される場合、引数はソース パスに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="fe65b-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="fe65b-112">ソース パスは、PDB ファイルに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="fe65b-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="fe65b-113">PDB ファイルのパスは、PE (ポータブル実行可能) ファイルに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="fe65b-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="fe65b-114">このオプションは、コンパイラが実行されるコンピューター上の各物理パスを、出力ファイルに書き込まれる必要がある対応するパスにマップします。</span><span class="sxs-lookup"><span data-stu-id="fe65b-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="fe65b-115">例</span><span class="sxs-lookup"><span data-stu-id="fe65b-115">Example</span></span>

<span data-ttu-id="fe65b-116">ディレクトリ **C:\\work\\tests** 内の `t.cs` をコンパイルし、出力ではそのディレクトリを **\publish** にマップします。</span><span class="sxs-lookup"><span data-stu-id="fe65b-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="fe65b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe65b-117">See also</span></span>

 [<span data-ttu-id="fe65b-118">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="fe65b-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="fe65b-119">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="fe65b-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
