---
title: "/linkresource (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8d4d2d2fdacef0c830414790efa544a96c35fd3c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="linkresource-visual-basic"></a><span data-ttu-id="46573-102">/linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46573-102">/linkresource (Visual Basic)</span></span>
<span data-ttu-id="46573-103">マネージ リソースへのリンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="46573-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46573-104">構文</span><span class="sxs-lookup"><span data-stu-id="46573-104">Syntax</span></span>  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="46573-105">引数</span><span class="sxs-lookup"><span data-stu-id="46573-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="46573-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="46573-106">Required.</span></span> <span data-ttu-id="46573-107">アセンブリにリンクするリソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="46573-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="46573-108">ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="46573-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="46573-109">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="46573-109">Optional.</span></span> <span data-ttu-id="46573-110">リソースの論理名。</span><span class="sxs-lookup"><span data-stu-id="46573-110">The logical name for the resource.</span></span> <span data-ttu-id="46573-111">リソースを読み込むために使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="46573-111">The name that is used to load the resource.</span></span> <span data-ttu-id="46573-112">既定では、ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="46573-112">The default is the name of the file.</span></span> <span data-ttu-id="46573-113">必要に応じてを指定できるかどうか、ファイルがパブリックかプライベート アセンブリ マニフェストの例:`/linkres:filename.res,myname.res,public`です。</span><span class="sxs-lookup"><span data-stu-id="46573-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `/linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="46573-114">既定では、`filename`はアセンブリ内でパブリックです。</span><span class="sxs-lookup"><span data-stu-id="46573-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46573-115">コメント</span><span class="sxs-lookup"><span data-stu-id="46573-115">Remarks</span></span>  
 <span data-ttu-id="46573-116">`/linkresource`オプションで、出力ファイルのリソース ファイルが埋め込まれません。 を使用して、`/resource`これを行うオプションです。</span><span class="sxs-lookup"><span data-stu-id="46573-116">The `/linkresource` option does not embed the resource file in the output file; use the `/resource` option to do this.</span></span>  
  
 <span data-ttu-id="46573-117">`/linkresource`オプションでは、いずれかが必要です、`/target`以外のオプション`/target:module`します。</span><span class="sxs-lookup"><span data-stu-id="46573-117">The `/linkresource` option requires one of the `/target` options other than `/target:module`.</span></span>  
  
 <span data-ttu-id="46573-118">場合`filename`は、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リソース ファイルの作成例についてで、 [Resgen.exe (リソース ファイル ジェネレーター)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)または開発環境でアクセスできるメンバー間で、<xref:System.Resources>名前空間</xref:System.Resources>。</span><span class="sxs-lookup"><span data-stu-id="46573-118">If `filename` is a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="46573-119">(詳細については、次を参照してください<xref:System.Resources.ResourceManager>。)</xref:System.Resources.ResourceManager> 。実行時にその他のすべてのリソースにアクセスするで始まるメソッドを使用して`GetManifestResource`<xref:System.Reflection.Assembly>クラス</xref:System.Reflection.Assembly>の</span><span class="sxs-lookup"><span data-stu-id="46573-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="46573-120">ファイル名には、任意のファイル形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="46573-120">The file name can be any file format.</span></span> <span data-ttu-id="46573-121">たとえば、ネイティブの DLL が、アセンブリの一部は、グローバル アセンブリ キャッシュにインストールされているし、アセンブリ内のマネージ コードからアクセスできるようにすることがあります。</span><span class="sxs-lookup"><span data-stu-id="46573-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="46573-122">短い形式の`/linkresource`は`/linkres`です。</span><span class="sxs-lookup"><span data-stu-id="46573-122">The short form of `/linkresource` is `/linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46573-123">`/linkresource`オプションは、Visual Studio 開発環境からは使用できません。 は、コマンドラインからコンパイルする場合のみです。</span><span class="sxs-lookup"><span data-stu-id="46573-123">The `/linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46573-124">例</span><span class="sxs-lookup"><span data-stu-id="46573-124">Example</span></span>  
 <span data-ttu-id="46573-125">次のコードのコンパイル`In.vb`とリソース ファイルへのリンク`Rf.resource`します。</span><span class="sxs-lookup"><span data-stu-id="46573-125">The following code compiles `In.vb` and links to resource file `Rf.resource`.</span></span>  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="46573-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="46573-126">See Also</span></span>  
 <span data-ttu-id="46573-127">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="46573-127">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="46573-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="46573-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="46573-129"> [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) </span><span class="sxs-lookup"><span data-stu-id="46573-129"> [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) </span></span>  
<span data-ttu-id="46573-130"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="46573-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
