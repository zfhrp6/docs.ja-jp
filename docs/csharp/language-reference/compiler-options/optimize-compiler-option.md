---
title: -optimize (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: 86c8ebb2d2061085be4c00e8ac95448e1c341161
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="837d8-102">-optimize (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="837d8-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="837d8-103">**-optimize** オプションは、コンパイラで実行する最適化を有効または無効にします。最適化を実行すると、出力ファイルのサイズが小さくなり、速度と効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="837d8-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="837d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="837d8-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="837d8-105">コメント</span><span class="sxs-lookup"><span data-stu-id="837d8-105">Remarks</span></span>  
 <span data-ttu-id="837d8-106">**-optimize** は実行時にコードを最適化するように共通言語ランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="837d8-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="837d8-107">既定では、最適化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="837d8-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="837d8-108">**-optimize+** を指定して最適化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="837d8-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="837d8-109">モジュールをアセンブリで使用するように作成する場合は、アセンブリと同じ **-optimize** 設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="837d8-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="837d8-110">**-o** は **-optimize** の省略形です。</span><span class="sxs-lookup"><span data-stu-id="837d8-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="837d8-111">**-optimize** オプションと [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) オプションを結合することができます。</span><span class="sxs-lookup"><span data-stu-id="837d8-111">It is possible to combine the **-optimize** and [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="837d8-112">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="837d8-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="837d8-113">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="837d8-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="837d8-114">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="837d8-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="837d8-115">**コードの最適化**プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="837d8-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="837d8-116">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="837d8-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="837d8-117">例</span><span class="sxs-lookup"><span data-stu-id="837d8-117">Example</span></span>  
 <span data-ttu-id="837d8-118">`t2.cs` をコンパイルしてコンパイラの最適化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="837d8-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="837d8-119">参照</span><span class="sxs-lookup"><span data-stu-id="837d8-119">See Also</span></span>  
 [<span data-ttu-id="837d8-120">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="837d8-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="837d8-121">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="837d8-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
