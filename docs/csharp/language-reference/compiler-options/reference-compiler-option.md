---
title: -reference (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: 4a96da3668a73368dd98055a9082479f162b7b45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218177"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="4a60f-102">-reference (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="4a60f-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="4a60f-103">**-reference** オプションを指定すると、コンパイラは指定されたファイルの [public](../../../csharp/language-reference/keywords/public.md) 型の情報を現在のプロジェクトにインポートし、指定されたアセンブリ ファイルからメタデータを参照できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4a60f-103">The **-reference** option causes the compiler to import [public](../../../csharp/language-reference/keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a60f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4a60f-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a60f-105">引数</span><span class="sxs-lookup"><span data-stu-id="4a60f-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="4a60f-106">アセンブリ マニフェストを含むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="4a60f-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="4a60f-107">複数のファイルをインポートするには、ファイルごとに個別に **-reference** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="4a60f-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="4a60f-108">アセンブリ内のすべての名前空間を格納するルート名前空間を表す有効な C# 識別子。</span><span class="sxs-lookup"><span data-stu-id="4a60f-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a60f-109">コメント</span><span class="sxs-lookup"><span data-stu-id="4a60f-109">Remarks</span></span>  
 <span data-ttu-id="4a60f-110">複数のファイルからインポートするには、ファイルごとに **-reference** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="4a60f-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="4a60f-111">インポートするファイルは、マニフェストが含まれている必要があります。出力ファイルは、[-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 以外のいずれかの [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) オプションでコンパイルされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a60f-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="4a60f-112">**-r** は **-reference** の省略形です。</span><span class="sxs-lookup"><span data-stu-id="4a60f-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="4a60f-113">アセンブリ マニフェストを含まない出力ファイルからメタデータをインポートするには、[-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="4a60f-113">Use [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="4a60f-114">あるアセンブリ (アセンブリ A) を参照していて、そのアセンブリが別のアセンブリ (アセンブリ B) を参照している場合は、以下の条件が当てはまる場合はアセンブリ B を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a60f-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="4a60f-115">アセンブリ A から使う型がアセンブリ B の型から継承されているか、アセンブリ B からインターフェイスを実装している。</span><span class="sxs-lookup"><span data-stu-id="4a60f-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="4a60f-116">アセンブリ B の戻り値の型またはパラメーターの型を使用するフィールド、プロパティ、イベント、またはメソッドを呼び出す。</span><span class="sxs-lookup"><span data-stu-id="4a60f-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="4a60f-117">アセンブリ参照が存在するディレクトリを指定するには、[-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="4a60f-117">Use [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="4a60f-118">**-lib** のトピックでは、コンパイラがアセンブリを検索するディレクトリについても説明されています。</span><span class="sxs-lookup"><span data-stu-id="4a60f-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="4a60f-119">モジュールではなくアセンブリ内の型をコンパイラで認識するには、型の解決を強制する必要があります。そのためには、型のインスタンスを定義します。</span><span class="sxs-lookup"><span data-stu-id="4a60f-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="4a60f-120">アセンブリの型名を解決する方法は他にもあります。たとえば、アセンブリの型を継承すると、コンパイラで型名が認識されます。</span><span class="sxs-lookup"><span data-stu-id="4a60f-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="4a60f-121">1 つのアセンブリ内から、同じコンポーネントの 2 つの異なるバージョンを参照することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4a60f-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="4a60f-122">そのためには、ファイルごとに **-reference** スイッチの alias サブオブションを使って、2 つのファイルを区別します。</span><span class="sxs-lookup"><span data-stu-id="4a60f-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="4a60f-123">この別名は、コンポーネント名の修飾子として使われ、いずれかのファイルのコンポーネントに解決されます。</span><span class="sxs-lookup"><span data-stu-id="4a60f-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="4a60f-124">既定では、よく使われる .NET Framework アセンブリを参照する csc 応答 (.rsp) ファイルが使われます。</span><span class="sxs-lookup"><span data-stu-id="4a60f-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="4a60f-125">コンパイラが csc.rsp を使わないようにする場合は、[-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) を指定します。</span><span class="sxs-lookup"><span data-stu-id="4a60f-125">Use [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a60f-126">Visual Studio では、**[参照の追加]** ダイアログ ボックスを使います。</span><span class="sxs-lookup"><span data-stu-id="4a60f-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="4a60f-127">詳細については、「[方法: 参照マネージャーを使用して参照を追加または削除する](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a60f-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="4a60f-128">`-reference` を使った場合と **[参照の追加]** ダイアログ ボックスを使った場合で、参照の追加の動作が同じになるようにするには、追加するアセンブリの **[相互運用型の埋め込み]** プロパティを **[False]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="4a60f-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="4a60f-129">このプロパティの既定値は **[True]** です。</span><span class="sxs-lookup"><span data-stu-id="4a60f-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a60f-130">例</span><span class="sxs-lookup"><span data-stu-id="4a60f-130">Example</span></span>  
 <span data-ttu-id="4a60f-131">この例では、[extern alias](../../../csharp/language-reference/keywords/extern-alias.md) 機能を使う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4a60f-131">This example shows how to use the [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="4a60f-132">ソース ファイルをコンパイルし、`grid.dll` と `grid20.dll` からメタデータをインポートします。これらは事前にコンパイルしておきます。</span><span class="sxs-lookup"><span data-stu-id="4a60f-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`,which have been compiled previously.</span></span> <span data-ttu-id="4a60f-133">2 つの DLL には同じコンポーネントの異なるバージョンが含まれており、ソース ファイルをコンパイルするには 2 つの **-reference** と別名オプションを使います。</span><span class="sxs-lookup"><span data-stu-id="4a60f-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="4a60f-134">オプションは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4a60f-134">The options look like this:</span></span>  
  
 <span data-ttu-id="4a60f-135">-reference:GridV1=grid.dll と -reference:GridV2=grid20.dll</span><span class="sxs-lookup"><span data-stu-id="4a60f-135">-reference:GridV1=grid.dll and -reference:GridV2=grid20.dll</span></span>  
  
 <span data-ttu-id="4a60f-136">これは、外部別名 "GridV1" と "GridV2" を設定します。プログラムではこれらを extern ステートメントで使います。</span><span class="sxs-lookup"><span data-stu-id="4a60f-136">This sets up the external aliases "GridV1" and "GridV2," which you use in your program by means of an extern statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="4a60f-137">このようにすると、コントロール名にプレフィックス GridV1 を付けることで、grid.dll のグリッド コントロールを参照できます。次に示すのはその例です。</span><span class="sxs-lookup"><span data-stu-id="4a60f-137">Once this is done, you can refer to the grid control from grid.dll by prefixing the control name with GridV1, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="4a60f-138">さらに、コントロール名にプレフィックス GridV2 を付けると、grid20.dll のグリッド コントロールを参照できます。次に示すのはその例です。</span><span class="sxs-lookup"><span data-stu-id="4a60f-138">In addition, you can refer to the grid control from grid20.dll by prefixing the control name with GridV2 like this:</span></span>  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a><span data-ttu-id="4a60f-139">参照</span><span class="sxs-lookup"><span data-stu-id="4a60f-139">See Also</span></span>  
 [<span data-ttu-id="4a60f-140">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="4a60f-140">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="4a60f-141">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="4a60f-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
