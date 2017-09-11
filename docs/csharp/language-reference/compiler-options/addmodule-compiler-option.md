---
title: "-addmodule (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /addmodule
dev_langs:
- CSharp
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: 13
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
ms.openlocfilehash: 79fdad111b1f059e6a3b00e393ea2474f71db947
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="addmodule-c-compiler-options"></a><span data-ttu-id="97c87-102">/addmodule (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="97c87-102">/addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="97c87-103">このオプションを使用すると、スイッチで作成されたモジュールが現在のコンパイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="97c87-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c87-104">構文</span><span class="sxs-lookup"><span data-stu-id="97c87-104">Syntax</span></span>  
  
```console  
/addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="97c87-105">引数</span><span class="sxs-lookup"><span data-stu-id="97c87-105">Arguments</span></span>  
 <span data-ttu-id="97c87-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="97c87-106">`file`, `file2`</span></span>  
 <span data-ttu-id="97c87-107">メタデータを含む出力ファイル。</span><span class="sxs-lookup"><span data-stu-id="97c87-107">An output file that contains metadata.</span></span> <span data-ttu-id="97c87-108">このファイルには、アセンブリ マニフェストを含めることができません。</span><span class="sxs-lookup"><span data-stu-id="97c87-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="97c87-109">複数のファイルをインポートするには、コンマかセミコロンでファイル名を区切ります。</span><span class="sxs-lookup"><span data-stu-id="97c87-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97c87-110">コメント</span><span class="sxs-lookup"><span data-stu-id="97c87-110">Remarks</span></span>  
 <span data-ttu-id="97c87-111">**/addmodule** で追加したモジュールはすべて、実行時に出力ファイルと同じディレクトリに置かれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="97c87-111">All modules added with **/addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="97c87-112">つまり、コンパイル時にはあるゆるディレクトリのモジュールを指定できますが、そのモジュールは実行時にアプリケーション ディレクトリに置かれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="97c87-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="97c87-113">実行時にモジュールがアプリケーション ディレクトリにない場合、<xref:System.TypeLoadException> が生成されます。</span><span class="sxs-lookup"><span data-stu-id="97c87-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="97c87-114">`file` には、アセンブリを含めることができません。</span><span class="sxs-lookup"><span data-stu-id="97c87-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="97c87-115">たとえば、出力ファイルが [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) で作成された場合、そのメタデータは **/addmodule** でインポートできます。</span><span class="sxs-lookup"><span data-stu-id="97c87-115">For example, if the output file was created with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), its metadata can be imported with **/addmodule**.</span></span>  
  
 <span data-ttu-id="97c87-116">出力ファイルが **/target:module** ではなく **/target** オプションで作成された場合、そのメタデータは **/addmodule** ではインポートできませんが、[/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) でインポートできます。</span><span class="sxs-lookup"><span data-stu-id="97c87-116">If the output file was created with a **/target** option other than **/target:module**, its metadata cannot be imported with **/addmodule** but can be imported with [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="97c87-117">このコンパイラ オプションは Visual Studio では利用できません。プロジェクトはモジュールを参照できません。</span><span class="sxs-lookup"><span data-stu-id="97c87-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="97c87-118">また、このコンパイラ オプションをプログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="97c87-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97c87-119">例</span><span class="sxs-lookup"><span data-stu-id="97c87-119">Example</span></span>  
 <span data-ttu-id="97c87-120">ソース ファイル `input.cs` をコンパイルし、`metad1.netmodule` と `metad2.netmodule` からメタデータを追加し、`out.exe` を生成します。</span><span class="sxs-lookup"><span data-stu-id="97c87-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="97c87-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="97c87-121">See Also</span></span>  
 <span data-ttu-id="97c87-122">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="97c87-122">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 <span data-ttu-id="97c87-123">[プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties) </span><span class="sxs-lookup"><span data-stu-id="97c87-123">[Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties) </span></span>  
 <span data-ttu-id="97c87-124">[マルチファイル アセンブリ](../../../framework/app-domains/multifile-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="97c87-124">[Multifile Assemblies](../../../framework/app-domains/multifile-assemblies.md) </span></span>  
 [<span data-ttu-id="97c87-125">方法: マルチファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="97c87-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)

