---
title: "-resource (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a305f98b09d390afbeba7b55ab44ff09abc74617
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2018
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="dfad0-102">-resource (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="dfad0-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="dfad0-103">指定されたリソースを出力ファイルに埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="dfad0-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfad0-104">構文</span><span class="sxs-lookup"><span data-stu-id="dfad0-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="dfad0-105">引数</span><span class="sxs-lookup"><span data-stu-id="dfad0-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="dfad0-106">出力ファイルに埋め込む .NET Framework リソース ファイルです。</span><span class="sxs-lookup"><span data-stu-id="dfad0-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="dfad0-107">`identifier` (省略可能)</span><span class="sxs-lookup"><span data-stu-id="dfad0-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="dfad0-108">リソースの論理名。リソースを読み込むために使われる名前です。</span><span class="sxs-lookup"><span data-stu-id="dfad0-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="dfad0-109">既定値はファイル名です。</span><span class="sxs-lookup"><span data-stu-id="dfad0-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="dfad0-110">`accessibility-modifier` (省略可能)</span><span class="sxs-lookup"><span data-stu-id="dfad0-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="dfad0-111">リソースのアクセシビリティ。パブリックまたはプライベートです。</span><span class="sxs-lookup"><span data-stu-id="dfad0-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="dfad0-112">既定値はパブリックです。</span><span class="sxs-lookup"><span data-stu-id="dfad0-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfad0-113">コメント</span><span class="sxs-lookup"><span data-stu-id="dfad0-113">Remarks</span></span>  
 <span data-ttu-id="dfad0-114">[-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) を使用すると、リソースがアセンブリにリンクされ、リソース ファイルは出力ファイルに追加されません。</span><span class="sxs-lookup"><span data-stu-id="dfad0-114">Use [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="dfad0-115">既定では、リソースは、C# コンパイラを使用して作成されるときにアセンブリ内でパブリックになります。</span><span class="sxs-lookup"><span data-stu-id="dfad0-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="dfad0-116">リソースをプライベートにするには、アクセシビリティ修飾子として `private` を指定します。</span><span class="sxs-lookup"><span data-stu-id="dfad0-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="dfad0-117">`public` と `private` 以外のアクセシビリティは使用できません。</span><span class="sxs-lookup"><span data-stu-id="dfad0-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="dfad0-118">`filename` が [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) や開発環境などで作成された .NET Framework リソース ファイルである場合は、<xref:System.Resources> 名前空間のメンバーを使ってそのファイルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="dfad0-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="dfad0-119">詳細については、「<xref:System.Resources.ResourceManager?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfad0-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dfad0-120">それ以外のすべてのリソースに対しては、<xref:System.Reflection.Assembly> クラスの `GetManifestResource` メソッドを使用して、実行時にリソースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="dfad0-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="dfad0-121">**-res** は **-resource** の省略形です。</span><span class="sxs-lookup"><span data-stu-id="dfad0-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="dfad0-122">出力ファイルにおけるリソースの順序は、コマンド ラインでの指定順序に基づいて決定されます。</span><span class="sxs-lookup"><span data-stu-id="dfad0-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="dfad0-123">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="dfad0-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="dfad0-124">プロジェクトにリソース ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="dfad0-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="dfad0-125">**ソリューション エクスプローラー**で、埋め込むファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="dfad0-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="dfad0-126">選択したファイルの **[プロパティ]** ウィンドウで、**[ビルド アクション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dfad0-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="dfad0-127">**[ビルド アクション]** を **[埋め込まれたリソース]**に設定します。</span><span class="sxs-lookup"><span data-stu-id="dfad0-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="dfad0-128">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.FileProperties2.BuildAction%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfad0-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfad0-129">例</span><span class="sxs-lookup"><span data-stu-id="dfad0-129">Example</span></span>  
 <span data-ttu-id="dfad0-130">`in.cs` をコンパイルし、リソース ファイル `rf.resource` をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="dfad0-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfad0-131">参照</span><span class="sxs-lookup"><span data-stu-id="dfad0-131">See Also</span></span>  
 [<span data-ttu-id="dfad0-132">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="dfad0-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="dfad0-133">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="dfad0-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
