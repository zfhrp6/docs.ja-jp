---
title: "-target:exe (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /exe
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
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
ms.openlocfilehash: bd035bffb697e895da8765f9e5d230fa84e98f04
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="targetexe-c-compiler-options"></a><span data-ttu-id="41e5e-102">/target:exe (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="41e5e-102">/target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="41e5e-103">**/target:exe** オプションを指定した場合、コンパイラは実行可能な (EXE) コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="41e5e-103">The **/target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e5e-104">構文</span><span class="sxs-lookup"><span data-stu-id="41e5e-104">Syntax</span></span>  
  
```console  
/target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="41e5e-105">コメント</span><span class="sxs-lookup"><span data-stu-id="41e5e-105">Remarks</span></span>  
 <span data-ttu-id="41e5e-106">**/target:exe** オプションは既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="41e5e-106">The **/target:exe** option is in effect by default.</span></span> <span data-ttu-id="41e5e-107">.exe 拡張子の実行可能ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="41e5e-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="41e5e-108">Windows プログラムの実行可能ファイルを作成する場合は、[/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="41e5e-108">Use [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="41e5e-109">[/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションで特に指定しない限り、出力ファイル名は [Main](../../../csharp/programming-guide/main-and-command-args/index.md) メソッドを含む入力ファイルと同じになります。</span><span class="sxs-lookup"><span data-stu-id="41e5e-109">Unless otherwise specified with the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="41e5e-110">コマンド ラインで指定すると、次の **/out** または **/target:module** オプションまでのすべてのファイルが .exe ファイルを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="41e5e-110">When specified at the command line, all files up to the next **/out** or **/target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="41e5e-111">**Main** メソッドは、.exe ファイルにコンパイルされるソース コード ファイル内で 1 つだけ必要になります。</span><span class="sxs-lookup"><span data-stu-id="41e5e-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="41e5e-112">コードに **Main** メソッドを含むクラスが複数ある場合は、[/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) コンパイラ オプションを使用して、**Main** メソッドを含めるクラスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="41e5e-112">The [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="41e5e-113">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="41e5e-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="41e5e-114">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="41e5e-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="41e5e-115">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="41e5e-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="41e5e-116">**[出力の種類]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="41e5e-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="41e5e-117">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="41e5e-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41e5e-118">例</span><span class="sxs-lookup"><span data-stu-id="41e5e-118">Example</span></span>  
 <span data-ttu-id="41e5e-119">次のコマンド ラインのいずれかで `in.cs` がコンパイルされ、`in.exe` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="41e5e-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc /target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="41e5e-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="41e5e-120">See Also</span></span>  
 <span data-ttu-id="41e5e-121">[/target (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="41e5e-121">[/target (C# Compiler Options)](../../../csharp/language-reference/compiler-options/target-compiler-option.md) </span></span>  
 [<span data-ttu-id="41e5e-122">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="41e5e-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

