---
title: /linkresource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e51f844695985485210a1e4bedfef7ac968326c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-visual-basic"></a><span data-ttu-id="8b6e4-102">/linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b6e4-102">/linkresource (Visual Basic)</span></span>
<span data-ttu-id="8b6e4-103">マネージ リソースへのリンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b6e4-104">構文</span><span class="sxs-lookup"><span data-stu-id="8b6e4-104">Syntax</span></span>  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b6e4-105">引数</span><span class="sxs-lookup"><span data-stu-id="8b6e4-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="8b6e4-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-106">Required.</span></span> <span data-ttu-id="8b6e4-107">アセンブリにリンクするリソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="8b6e4-108">ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="8b6e4-109">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-109">Optional.</span></span> <span data-ttu-id="8b6e4-110">リソースの論理名。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-110">The logical name for the resource.</span></span> <span data-ttu-id="8b6e4-111">リソースの読み込みに使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-111">The name that is used to load the resource.</span></span> <span data-ttu-id="8b6e4-112">既定値は、ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-112">The default is the name of the file.</span></span> <span data-ttu-id="8b6e4-113">かどうか、ファイルがパブリックかプライベート アセンブリ マニフェストに例を指定することができます必要に応じて、:`/linkres:filename.res,myname.res,public`です。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `/linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="8b6e4-114">既定では、`filename`がアセンブリに公開します。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b6e4-115">コメント</span><span class="sxs-lookup"><span data-stu-id="8b6e4-115">Remarks</span></span>  
 <span data-ttu-id="8b6e4-116">`/linkresource`オプションは、リソース ファイルを出力ファイルに埋め込まれません。 を使用して、`/resource`これを行うオプション。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-116">The `/linkresource` option does not embed the resource file in the output file; use the `/resource` option to do this.</span></span>  
  
 <span data-ttu-id="8b6e4-117">`/linkresource`オプションでは、いずれかが必要です、`/target`以外のオプション`/target:module`です。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-117">The `/linkresource` option requires one of the `/target` options other than `/target:module`.</span></span>  
  
 <span data-ttu-id="8b6e4-118">場合`filename`は、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]作成されたリソース ファイル、たとえば、によって、 [Resgen.exe (リソース ファイル ジェネレーター)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)または開発環境でアクセスできるメンバー間で、<xref:System.Resources>名前空間。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="8b6e4-119">(詳細については、「<xref:System.Resources.ResourceManager>」を参照してください)。実行時にその他のすべてのリソースにアクセスするで始まるメソッドを使用して`GetManifestResource`で、<xref:System.Reflection.Assembly>クラスです。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="8b6e4-120">ファイル名には、任意のファイル形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-120">The file name can be any file format.</span></span> <span data-ttu-id="8b6e4-121">たとえば、ネイティブ DLL をアセンブリの一部にすることで、グローバル アセンブリ キャッシュにインストールして、アセンブリ内のマネージ コードからアクセスできるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="8b6e4-122">`/linkresource` の省略形は `/linkres` です。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-122">The short form of `/linkresource` is `/linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b6e4-123">`/linkresource`オプションは、Visual Studio 開発環境からは使用できません。 使用可能なコマンドラインからコンパイルするときにのみです。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-123">The `/linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b6e4-124">例</span><span class="sxs-lookup"><span data-stu-id="8b6e4-124">Example</span></span>  
 <span data-ttu-id="8b6e4-125">次のコードのコンパイル`In.vb`とリソース ファイルへのリンク`Rf.resource`です。</span><span class="sxs-lookup"><span data-stu-id="8b6e4-125">The following code compiles `In.vb` and links to resource file `Rf.resource`.</span></span>  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b6e4-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b6e4-126">See Also</span></span>  
 [<span data-ttu-id="8b6e4-127">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="8b6e4-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="8b6e4-128">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b6e4-128">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="8b6e4-129">/resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b6e4-129">/resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [<span data-ttu-id="8b6e4-130">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="8b6e4-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
