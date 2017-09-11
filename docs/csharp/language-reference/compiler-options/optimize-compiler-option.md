---
title: "-optimize (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /optimize
dev_langs:
- CSharp
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: 15
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
ms.openlocfilehash: 75a2b65c159e9adb0103765468182919ed6b0a23
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="optimize-c-compiler-options"></a><span data-ttu-id="795fb-102">/optimize (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="795fb-102">/optimize (C# Compiler Options)</span></span>
<span data-ttu-id="795fb-103">**/optimize** オプションは、コンパイラで実行する最適化を有効または無効にします。最適化を実行すると、出力ファイルのサイズが小さくなり、速度と効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="795fb-103">The **/optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="795fb-104">構文</span><span class="sxs-lookup"><span data-stu-id="795fb-104">Syntax</span></span>  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="795fb-105">コメント</span><span class="sxs-lookup"><span data-stu-id="795fb-105">Remarks</span></span>  
 <span data-ttu-id="795fb-106">**/optimize** は実行時にコードを最適化するように共通言語ランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="795fb-106">**/optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="795fb-107">既定では、最適化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="795fb-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="795fb-108">**/optimize+** を指定して最適化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="795fb-108">Specify **/optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="795fb-109">モジュールをアセンブリで使用するように作成する場合は、アセンブリと同じ **/optimize** 設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="795fb-109">When building a module to be used by an assembly, use the same **/optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="795fb-110">**/o** は **/optimize** の省略形です。</span><span class="sxs-lookup"><span data-stu-id="795fb-110">**/o** is the short form of **/optimize**.</span></span>  
  
 <span data-ttu-id="795fb-111">**/optimize** オプションと [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) オプションを結合することができます。</span><span class="sxs-lookup"><span data-stu-id="795fb-111">It is possible to combine the **/optimize** and [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="795fb-112">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="795fb-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="795fb-113">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="795fb-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="795fb-114">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="795fb-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="795fb-115">**コードの最適化**プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="795fb-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="795fb-116">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="795fb-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="795fb-117">例</span><span class="sxs-lookup"><span data-stu-id="795fb-117">Example</span></span>  
 <span data-ttu-id="795fb-118">`t2.cs` をコンパイルしてコンパイラの最適化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="795fb-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="795fb-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="795fb-119">See Also</span></span>  
 <span data-ttu-id="795fb-120">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="795fb-120">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="795fb-121">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="795fb-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

