---
title: "-addmodule (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2652102682de9dff24c66180dde36f33b4b6bbfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule-c-compiler-options"></a><span data-ttu-id="3a84b-102">/addmodule (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="3a84b-102">/addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="3a84b-103">このオプションを使用すると、スイッチで作成されたモジュールが現在のコンパイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3a84b-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a84b-104">構文</span><span class="sxs-lookup"><span data-stu-id="3a84b-104">Syntax</span></span>  
  
```console  
/addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3a84b-105">引数</span><span class="sxs-lookup"><span data-stu-id="3a84b-105">Arguments</span></span>  
 <span data-ttu-id="3a84b-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="3a84b-106">`file`, `file2`</span></span>  
 <span data-ttu-id="3a84b-107">メタデータを含む出力ファイル。</span><span class="sxs-lookup"><span data-stu-id="3a84b-107">An output file that contains metadata.</span></span> <span data-ttu-id="3a84b-108">このファイルには、アセンブリ マニフェストを含めることができません。</span><span class="sxs-lookup"><span data-stu-id="3a84b-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="3a84b-109">複数のファイルをインポートするには、コンマかセミコロンでファイル名を区切ります。</span><span class="sxs-lookup"><span data-stu-id="3a84b-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a84b-110">コメント</span><span class="sxs-lookup"><span data-stu-id="3a84b-110">Remarks</span></span>  
 <span data-ttu-id="3a84b-111">**/addmodule** で追加したモジュールはすべて、実行時に出力ファイルと同じディレクトリに置かれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a84b-111">All modules added with **/addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="3a84b-112">つまり、コンパイル時にはあるゆるディレクトリのモジュールを指定できますが、そのモジュールは実行時にアプリケーション ディレクトリに置かれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a84b-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="3a84b-113">実行時にモジュールがアプリケーション ディレクトリにない場合、<xref:System.TypeLoadException> が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3a84b-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="3a84b-114">`file` には、アセンブリを含めることができません。</span><span class="sxs-lookup"><span data-stu-id="3a84b-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="3a84b-115">たとえば、出力ファイルが [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) で作成された場合、そのメタデータは **/addmodule** でインポートできます。</span><span class="sxs-lookup"><span data-stu-id="3a84b-115">For example, if the output file was created with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), its metadata can be imported with **/addmodule**.</span></span>  
  
 <span data-ttu-id="3a84b-116">出力ファイルが **/target:module** ではなく **/target** オプションで作成された場合、そのメタデータは **/addmodule** ではインポートできませんが、[/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) でインポートできます。</span><span class="sxs-lookup"><span data-stu-id="3a84b-116">If the output file was created with a **/target** option other than **/target:module**, its metadata cannot be imported with **/addmodule** but can be imported with [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="3a84b-117">このコンパイラ オプションは Visual Studio では利用できません。プロジェクトはモジュールを参照できません。</span><span class="sxs-lookup"><span data-stu-id="3a84b-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="3a84b-118">また、このコンパイラ オプションをプログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="3a84b-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a84b-119">例</span><span class="sxs-lookup"><span data-stu-id="3a84b-119">Example</span></span>  
 <span data-ttu-id="3a84b-120">ソース ファイル `input.cs` をコンパイルし、`metad1.netmodule` と `metad2.netmodule` からメタデータを追加し、`out.exe` を生成します。</span><span class="sxs-lookup"><span data-stu-id="3a84b-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a84b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a84b-121">See Also</span></span>  
 [<span data-ttu-id="3a84b-122">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="3a84b-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="3a84b-123">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="3a84b-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="3a84b-124">マルチファイル アセンブリ</span><span class="sxs-lookup"><span data-stu-id="3a84b-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)  
 [<span data-ttu-id="3a84b-125">方法: マルチファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="3a84b-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
