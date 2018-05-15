---
title: -lib (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 7db975909f498a0b84e7405a12a8f8ec1e2dd34b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="ee55a-102">-lib (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="ee55a-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="ee55a-103">**-lib** オプションは、[-reference (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) オプションによって参照されるアセンブリの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee55a-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee55a-104">構文</span><span class="sxs-lookup"><span data-stu-id="ee55a-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee55a-105">引数</span><span class="sxs-lookup"><span data-stu-id="ee55a-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="ee55a-106">参照されているアセンブリが現在の作業ディレクトリ (コンパイラを起動したディレクトリ) または共通言語ランタイムのシステム ディレクトリに見つからない場合にコンパイラが検索するディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="ee55a-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="ee55a-107">アセンブリ参照を検索する 1 つまたは複数の追加ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="ee55a-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="ee55a-108">複数のディレクトリはコンマで区切り、それらの間に空白文字は入れません。</span><span class="sxs-lookup"><span data-stu-id="ee55a-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee55a-109">コメント</span><span class="sxs-lookup"><span data-stu-id="ee55a-109">Remarks</span></span>  
 <span data-ttu-id="ee55a-110">コンパイラは、完全に修飾されていないアセンブリ参照を次の順序で検索します。</span><span class="sxs-lookup"><span data-stu-id="ee55a-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="ee55a-111">現在の作業ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="ee55a-111">Current working directory.</span></span> <span data-ttu-id="ee55a-112">これは、コンパイラを起動したディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="ee55a-112">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="ee55a-113">共通言語ランタイムのシステム ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="ee55a-113">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="ee55a-114">**-lib** によって指定されているディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="ee55a-114">Directories specified by **-lib**.</span></span>  
  
4.  <span data-ttu-id="ee55a-115">LIB 環境変数によって指定されているディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="ee55a-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="ee55a-116">アセンブリ参照を指定するには **-reference** を使います。</span><span class="sxs-lookup"><span data-stu-id="ee55a-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="ee55a-117">**-lib** は追加です。複数回指定すると、前の値に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee55a-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="ee55a-118">**-lib** を使う代わりに、必要なアセンブリを作業ディレクトリにコピーしてもかまいません。このようにすると、アセンブリ名を **-reference** に渡すだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="ee55a-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="ee55a-119">後で、作業ディレクトリからアセンブリを削除できます。</span><span class="sxs-lookup"><span data-stu-id="ee55a-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="ee55a-120">依存アセンブリへのパスはアセンブリ マニフェストで指定されていないため、ターゲット コンピューターで開始されたアプリケーションは、グローバル アセンブリ キャッシュでアセンブリを探して使います。</span><span class="sxs-lookup"><span data-stu-id="ee55a-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="ee55a-121">コンパイラがアセンブリを参照できるということは、共通言語ランタイムが実行時にアセンブリを検索して読み込むことができるという意味ではありません。</span><span class="sxs-lookup"><span data-stu-id="ee55a-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="ee55a-122">ランタイムが参照されているアセンブリを検索する方法について詳しくは、「[ランタイムがアセンブリを検索する方法](../../../framework/deployment/how-the-runtime-locates-assemblies.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee55a-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ee55a-123">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="ee55a-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="ee55a-124">プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ee55a-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2.  <span data-ttu-id="ee55a-125">**[参照パス]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee55a-125">Click the **References Path** property page.</span></span>  
  
3.  <span data-ttu-id="ee55a-126">リスト ボックスの内容を変更します。</span><span class="sxs-lookup"><span data-stu-id="ee55a-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="ee55a-127">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee55a-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee55a-128">例</span><span class="sxs-lookup"><span data-stu-id="ee55a-128">Example</span></span>  
 <span data-ttu-id="ee55a-129">t2.cs をコンパイルして .exe ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="ee55a-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="ee55a-130">コンパイラは、作業ディレクトリと C ドライブのルート ディレクトリで、アセンブリ参照を探します。</span><span class="sxs-lookup"><span data-stu-id="ee55a-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee55a-131">参照</span><span class="sxs-lookup"><span data-stu-id="ee55a-131">See Also</span></span>  
 [<span data-ttu-id="ee55a-132">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="ee55a-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ee55a-133">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="ee55a-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
