---
title: "-target:winexe (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target:winexe
dev_langs:
- CSharp
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: 11
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
ms.openlocfilehash: afb49fc6d45cc904c97988ab1b569f37a4e44a51
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="targetwinexe-c-compiler-options"></a><span data-ttu-id="72927-102">/target:winexe (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="72927-102">/target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="72927-103">**/target:winexe** オプションを使用すると、実行可能な (EXE) Windows プログラムがコンパイラによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="72927-103">The **/target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72927-104">構文</span><span class="sxs-lookup"><span data-stu-id="72927-104">Syntax</span></span>  
  
```console  
/target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="72927-105">コメント</span><span class="sxs-lookup"><span data-stu-id="72927-105">Remarks</span></span>  
 <span data-ttu-id="72927-106">実行可能ファイルは、.exe という拡張子で作成されます。</span><span class="sxs-lookup"><span data-stu-id="72927-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="72927-107">Windows プログラムは、.NET Framework ライブラリまたは Win32 API のユーザー インターフェイスを提供するプログラムです。</span><span class="sxs-lookup"><span data-stu-id="72927-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Win32 APIs.</span></span>  
  
 <span data-ttu-id="72927-108">コンソール アプリケーションを作成するには、[/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="72927-108">Use [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="72927-109">[/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションで指定しない限り、出力ファイル名は [Main](../../../csharp/programming-guide/main-and-command-args/index.md) メソッドを含む入力ファイルと同じになります。</span><span class="sxs-lookup"><span data-stu-id="72927-109">Unless otherwise specified with the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="72927-110">コマンド ラインで指定すると、次の **/out** オプションまたは [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) オプションまでのすべてのファイルが、Windows プログラムの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="72927-110">When specified at the command line, all files until the next **/out** or [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="72927-111">**Main** メソッドは、.exe ファイルにコンパイルされるソース コード ファイル内に 1 つだけ必要です。</span><span class="sxs-lookup"><span data-stu-id="72927-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="72927-112">コードに **Main** メソッドを含むクラスが複数ある場合は、[/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) オプションを使用して、**Main** メソッドを含めるクラスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="72927-112">The [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="72927-113">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="72927-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="72927-114">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="72927-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="72927-115">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="72927-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="72927-116">**[出力の種類]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="72927-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="72927-117">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="72927-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72927-118">例</span><span class="sxs-lookup"><span data-stu-id="72927-118">Example</span></span>  
 <span data-ttu-id="72927-119">`in.cs` をコンパイルし、Windows プログラムを生成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="72927-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc /target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="72927-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="72927-120">See Also</span></span>  
 <span data-ttu-id="72927-121">[/target (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="72927-121">[/target (C# Compiler Options)](../../../csharp/language-reference/compiler-options/target-compiler-option.md) </span></span>  
 [<span data-ttu-id="72927-122">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="72927-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

