---
title: "-resource (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /resource
dev_langs:
- CSharp
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: 16
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
ms.openlocfilehash: fdb7be630300e11c2e63d88bd6add7d229714bfa
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="resource-c-compiler-options"></a><span data-ttu-id="3897a-102">/resource (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="3897a-102">/resource (C# Compiler Options)</span></span>
<span data-ttu-id="3897a-103">指定されたリソースを出力ファイルに埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="3897a-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3897a-104">構文</span><span class="sxs-lookup"><span data-stu-id="3897a-104">Syntax</span></span>  
  
```console  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3897a-105">引数</span><span class="sxs-lookup"><span data-stu-id="3897a-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="3897a-106">出力ファイルに埋め込む .NET Framework リソース ファイルです。</span><span class="sxs-lookup"><span data-stu-id="3897a-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="3897a-107">`identifier` (省略可能)</span><span class="sxs-lookup"><span data-stu-id="3897a-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="3897a-108">リソースの論理名。リソースを読み込むために使われる名前です。</span><span class="sxs-lookup"><span data-stu-id="3897a-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="3897a-109">既定値はファイル名です。</span><span class="sxs-lookup"><span data-stu-id="3897a-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="3897a-110">`accessibility-modifier` (省略可能)</span><span class="sxs-lookup"><span data-stu-id="3897a-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="3897a-111">リソースのアクセシビリティ。パブリックまたはプライベートです。</span><span class="sxs-lookup"><span data-stu-id="3897a-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="3897a-112">既定値はパブリックです。</span><span class="sxs-lookup"><span data-stu-id="3897a-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3897a-113">コメント</span><span class="sxs-lookup"><span data-stu-id="3897a-113">Remarks</span></span>  
 <span data-ttu-id="3897a-114">[/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) を使用すると、リソースがアセンブリにリンクされ、リソース ファイルは出力ファイルに追加されません。</span><span class="sxs-lookup"><span data-stu-id="3897a-114">Use [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="3897a-115">既定では、リソースは、C# コンパイラを使用して作成されるときにアセンブリ内でパブリックになります。</span><span class="sxs-lookup"><span data-stu-id="3897a-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="3897a-116">リソースをプライベートにするには、アクセシビリティ修飾子として `private` を指定します。</span><span class="sxs-lookup"><span data-stu-id="3897a-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="3897a-117">`public` と `private` 以外のアクセシビリティは使用できません。</span><span class="sxs-lookup"><span data-stu-id="3897a-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="3897a-118">`filename` が [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) や開発環境などで作成された .NET Framework リソース ファイルである場合は、<xref:System.Resources> 名前空間のメンバーを使ってそのファイルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3897a-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="3897a-119">詳細については、「<xref:System.Resources.ResourceManager?displayProperty=fullName>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3897a-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=fullName>.</span></span> <span data-ttu-id="3897a-120">それ以外のすべてのリソースについては、<xref:System.Reflection.Assembly> クラスの `GetManifestResource`* メソッドを使って、実行時にリソースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3897a-120">For all other resources, use the `GetManifestResource`* methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="3897a-121">**/res** は **/resource** の省略形です。</span><span class="sxs-lookup"><span data-stu-id="3897a-121">**/res** is the short form of **/resource**.</span></span>  
  
 <span data-ttu-id="3897a-122">出力ファイルにおけるリソースの順序は、コマンド ラインでの指定順序に基づいて決定されます。</span><span class="sxs-lookup"><span data-stu-id="3897a-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3897a-123">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="3897a-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="3897a-124">プロジェクトにリソース ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="3897a-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="3897a-125">**ソリューション エクスプローラー**で、埋め込むファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3897a-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="3897a-126">選択したファイルの **[プロパティ]** ウィンドウで、**[ビルド アクション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3897a-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="3897a-127">**[ビルド アクション]** を **[埋め込まれたリソース]**に設定します。</span><span class="sxs-lookup"><span data-stu-id="3897a-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="3897a-128">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.FileProperties2.BuildAction%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3897a-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3897a-129">例</span><span class="sxs-lookup"><span data-stu-id="3897a-129">Example</span></span>  
 <span data-ttu-id="3897a-130">`in.cs` をコンパイルし、リソース ファイル `rf.resource` をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="3897a-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc /resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3897a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="3897a-131">See Also</span></span>  
 <span data-ttu-id="3897a-132">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="3897a-132">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="3897a-133">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="3897a-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

