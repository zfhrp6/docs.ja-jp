---
title: リソース (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab5593455546e65bdd760d9e60532031dc1f12a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654438"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="e8bb6-102">リソース (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8bb6-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="e8bb6-103">マネージ リソースをアセンブリに埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8bb6-104">構文</span><span class="sxs-lookup"><span data-stu-id="e8bb6-104">Syntax</span></span>  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e8bb6-105">引数</span><span class="sxs-lookup"><span data-stu-id="e8bb6-105">Arguments</span></span>  
  
|<span data-ttu-id="e8bb6-106">用語</span><span class="sxs-lookup"><span data-stu-id="e8bb6-106">Term</span></span>|<span data-ttu-id="e8bb6-107">定義</span><span class="sxs-lookup"><span data-stu-id="e8bb6-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="e8bb6-108">必須。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-108">Required.</span></span> <span data-ttu-id="e8bb6-109">出力ファイルに埋め込むには、リソース ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="e8bb6-110">既定では、`filename`がアセンブリに公開します。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="e8bb6-111">ファイル名を引用符で囲みます ("")、スペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="e8bb6-112">任意。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-112">Optional.</span></span> <span data-ttu-id="e8bb6-113">リソースの論理名ファイルを読み込むための名前。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="e8bb6-114">既定値は、ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-114">The default is the name of the file.</span></span> <span data-ttu-id="e8bb6-115">必要に応じて、かどうか、リソースは、パブリックまたはプライベート アセンブリ マニフェストとに、次を指定できます。 `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="e8bb6-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8bb6-116">コメント</span><span class="sxs-lookup"><span data-stu-id="e8bb6-116">Remarks</span></span>  
 <span data-ttu-id="e8bb6-117">使用して`-linkresource`出力ファイルにリソース ファイルを配置することがなく、アセンブリにリソースをリンクします。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-117">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="e8bb6-118">場合`filename`は、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]作成されたリソース ファイル、たとえば、によって、 [Resgen.exe (リソース ファイル ジェネレーター)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)または開発環境でアクセスできるメンバー間で、<xref:System.Resources>名前空間 (参照<xref:System.Resources.ResourceManager>詳細については)。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="e8bb6-119">実行時にその他のすべてのリソースにアクセスするには、次のいずれかを使用: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>、 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>、または<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>です。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="e8bb6-120">`-resource` の省略形は `-res` です。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-120">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="e8bb6-121">設定する方法については`-resource`Visual Studio IDE で、次を参照してください。[を管理するアプリケーションのリソース (.NET)](/visualstudio/ide/managing-application-resources-dotnet)です。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-121">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8bb6-122">例</span><span class="sxs-lookup"><span data-stu-id="e8bb6-122">Example</span></span>  
 <span data-ttu-id="e8bb6-123">次のコードのコンパイル`In.vb`とアタッチのリソース ファイル`Rf.resource`です。</span><span class="sxs-lookup"><span data-stu-id="e8bb6-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8bb6-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8bb6-124">See Also</span></span>  
 [<span data-ttu-id="e8bb6-125">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="e8bb6-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e8bb6-126">-win32resource</span><span class="sxs-lookup"><span data-stu-id="e8bb6-126">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [<span data-ttu-id="e8bb6-127">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8bb6-127">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [<span data-ttu-id="e8bb6-128">-ターゲット (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8bb6-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="e8bb6-129">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="e8bb6-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
