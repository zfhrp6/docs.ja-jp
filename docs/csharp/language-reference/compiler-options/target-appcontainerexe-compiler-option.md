---
title: "-target:appcontainerexe (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 61fc914b0d956bcca8e0d574296fa0723b0e1406
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/22/2018
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="2d105-102">-target:appcontainerexe (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="2d105-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="2d105-103">**-target:appcontainerexe** コンパイラ オプションを使用すると、アプリケーション コンテナーで実行する必要のある Windows 実行可能ファイル (.exe) がコンパイラによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="2d105-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="2d105-104">このオプションは [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) に相当しますが、[!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] アプリ用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="2d105-104">This option is equivalent to [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d105-105">構文</span><span class="sxs-lookup"><span data-stu-id="2d105-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="2d105-106">コメント</span><span class="sxs-lookup"><span data-stu-id="2d105-106">Remarks</span></span>  
 <span data-ttu-id="2d105-107">アプリケーション コンテナーでのアプリケーションの実行を要求するために、このオプションは、[Portable Executable](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) (PE) ファイルでビットを設定します。</span><span class="sxs-lookup"><span data-stu-id="2d105-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) (PE) file.</span></span> <span data-ttu-id="2d105-108">このビットが設定されている場合、CreateProcess メソッドがアプリケーション コンテナー外の実行可能ファイルを起動しようとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="2d105-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="2d105-109">[-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションを使用しない限り、出力ファイル名は [Main](../../../csharp/programming-guide/main-and-command-args/index.md) メソッドを含む入力ファイルと同じになります。</span><span class="sxs-lookup"><span data-stu-id="2d105-109">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="2d105-110">コマンド ラインで指定すると、次の **-out** オプションまたは **-target** オプションまでのすべてのファイルが、実行可能ファイルの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="2d105-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="2d105-111">IDE でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="2d105-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="2d105-112">**ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d105-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="2d105-113">**[アプリケーション]** タブの **[出力の種類]** ボックスの一覧で、**[Windows ストア アプリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d105-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="2d105-114">このオプションは [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] アプリケーション テンプレートでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d105-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="2d105-115">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d105-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d105-116">例</span><span class="sxs-lookup"><span data-stu-id="2d105-116">Example</span></span>  
 <span data-ttu-id="2d105-117">次のコマンドは、アプリケーション コンテナーでのみ実行できる Windows 実行可能ファイルに `filename.cs` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="2d105-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d105-118">参照</span><span class="sxs-lookup"><span data-stu-id="2d105-118">See Also</span></span>  
 [<span data-ttu-id="2d105-119">-target (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="2d105-119">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="2d105-120">-target:winexe (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="2d105-120">-target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [<span data-ttu-id="2d105-121">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="2d105-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
