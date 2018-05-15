---
title: -nowarn (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 1c5e8bc7ad065c4662cd489930b2226e8a4b8962
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="7a15e-102">-nowarn (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="7a15e-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="7a15e-103">**-nowarn** オプションを使用すると、コンパイラから警告が出力されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="7a15e-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="7a15e-104">警告番号が複数ある場合は、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="7a15e-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a15e-105">構文</span><span class="sxs-lookup"><span data-stu-id="7a15e-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7a15e-106">引数</span><span class="sxs-lookup"><span data-stu-id="7a15e-106">Arguments</span></span>  
 <span data-ttu-id="7a15e-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="7a15e-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="7a15e-108">コンパイラで表示しないようにする警告番号。</span><span class="sxs-lookup"><span data-stu-id="7a15e-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a15e-109">コメント</span><span class="sxs-lookup"><span data-stu-id="7a15e-109">Remarks</span></span>  
 <span data-ttu-id="7a15e-110">警告 ID の数値だけを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a15e-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="7a15e-111">たとえば、CS0028 を抑制する場合は、`-nowarn:28` と指定します。</span><span class="sxs-lookup"><span data-stu-id="7a15e-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="7a15e-112">`-nowarn` に渡された警告番号が以前のリリースでは有効であったが、今はコンパイラから削除されている場合、コンパイラはその番号を自動的に無視します。</span><span class="sxs-lookup"><span data-stu-id="7a15e-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="7a15e-113">たとえば、CS0679 は Visual Studio .NET 2002 のコンパイラでは有効でしたが、その後削除されました。</span><span class="sxs-lookup"><span data-stu-id="7a15e-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="7a15e-114">`-nowarn` オプションでは、次の警告は抑制されません。</span><span class="sxs-lookup"><span data-stu-id="7a15e-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
-   <span data-ttu-id="7a15e-115">コンパイラの警告 (レベル 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="7a15e-115">Compiler Warning (level 1) CS2002</span></span>  
  
-   <span data-ttu-id="7a15e-116">コンパイラの警告 (レベル 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="7a15e-116">Compiler Warning (level 1) CS2023</span></span>  
  
-   <span data-ttu-id="7a15e-117">コンパイラの警告 (レベル 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="7a15e-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7a15e-118">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="7a15e-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="7a15e-119">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="7a15e-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="7a15e-120">詳細については、「[[ビルド] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a15e-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="7a15e-121">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a15e-121">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="7a15e-122">**[警告の表示なし]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="7a15e-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="7a15e-123">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.DelaySign%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a15e-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a15e-124">参照</span><span class="sxs-lookup"><span data-stu-id="7a15e-124">See Also</span></span>  
 [<span data-ttu-id="7a15e-125">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="7a15e-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="7a15e-126">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="7a15e-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="7a15e-127">C# コンパイラ エラー</span><span class="sxs-lookup"><span data-stu-id="7a15e-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
