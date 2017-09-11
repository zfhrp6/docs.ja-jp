---
title: "/resource (Visual Basic) |Microsoft ドキュメント"
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
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2278902f96f7b6349e91a9803f58c3caa89f4f33
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="resource-visual-basic"></a><span data-ttu-id="079f8-102">/resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="079f8-102">/resource (Visual Basic)</span></span>
<span data-ttu-id="079f8-103">マネージ リソースをアセンブリに埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="079f8-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="079f8-104">構文</span><span class="sxs-lookup"><span data-stu-id="079f8-104">Syntax</span></span>  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="079f8-105">引数</span><span class="sxs-lookup"><span data-stu-id="079f8-105">Arguments</span></span>  
  
|<span data-ttu-id="079f8-106">用語</span><span class="sxs-lookup"><span data-stu-id="079f8-106">Term</span></span>|<span data-ttu-id="079f8-107">定義</span><span class="sxs-lookup"><span data-stu-id="079f8-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="079f8-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="079f8-108">Required.</span></span> <span data-ttu-id="079f8-109">出力ファイルに埋め込まれるリソース ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="079f8-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="079f8-110">既定では、`filename`はアセンブリ内でパブリックです。</span><span class="sxs-lookup"><span data-stu-id="079f8-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="079f8-111">ファイル名を引用符で囲みます ("")、スペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="079f8-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="079f8-112">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="079f8-112">Optional.</span></span> <span data-ttu-id="079f8-113">リソースの論理名それを読み込むために使用する名前です。</span><span class="sxs-lookup"><span data-stu-id="079f8-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="079f8-114">既定では、ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="079f8-114">The default is the name of the file.</span></span> <span data-ttu-id="079f8-115">同様に、次が、パブリックまたはプライベート アセンブリ マニフェスト内にリソースかどうかを指定できます必要に応じて、: `/res:``filename.res`、`myname.res`、`public`</span><span class="sxs-lookup"><span data-stu-id="079f8-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `/res:``filename.res`,`myname.res`,`public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="079f8-116">コメント</span><span class="sxs-lookup"><span data-stu-id="079f8-116">Remarks</span></span>  
 <span data-ttu-id="079f8-117">使用`/linkresource`出力ファイルにリソース ファイルをかけることがなく、アセンブリにリソースをリンクします。</span><span class="sxs-lookup"><span data-stu-id="079f8-117">Use `/linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="079f8-118">場合`filename`は、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リソース ファイルの作成例についてで、 [Resgen.exe (リソース ファイル ジェネレーター)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)または開発環境でアクセスできるメンバー間で、<xref:System.Resources>名前空間 (を参照してください<xref:System.Resources.ResourceManager>の詳細).</xref:System.Resources.ResourceManager> </xref:System.Resources></span><span class="sxs-lookup"><span data-stu-id="079f8-118">If `filename` is a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="079f8-119">実行時にその他のすべてのリソースにアクセスするには、次のいずれかを使用します<xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>、 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>、または<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</xref:System.Reflection.Assembly.GetManifestResourceStream%2A> </xref:System.Reflection.Assembly.GetManifestResourceNames%2A> </xref:System.Reflection.Assembly.GetManifestResourceInfo%2A> 。</span><span class="sxs-lookup"><span data-stu-id="079f8-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="079f8-120">短い形式の`/resource`は`/res`です。</span><span class="sxs-lookup"><span data-stu-id="079f8-120">The short form of `/resource` is `/res`.</span></span>  
  
 <span data-ttu-id="079f8-121">設定する方法については`/resource`Visual Studio ide では、次を参照してください。[を管理するアプリケーションのリソース (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)します。</span><span class="sxs-lookup"><span data-stu-id="079f8-121">For information about how to set `/resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="079f8-122">例</span><span class="sxs-lookup"><span data-stu-id="079f8-122">Example</span></span>  
 <span data-ttu-id="079f8-123">次のコードのコンパイル`In.vb`とアタッチのリソース ファイル`Rf.resource`します。</span><span class="sxs-lookup"><span data-stu-id="079f8-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="079f8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="079f8-124">See Also</span></span>  
 <span data-ttu-id="079f8-125">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="079f8-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="079f8-126"> [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) </span><span class="sxs-lookup"><span data-stu-id="079f8-126"> [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) </span></span>  
<span data-ttu-id="079f8-127"> [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) </span><span class="sxs-lookup"><span data-stu-id="079f8-127"> [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) </span></span>  
<span data-ttu-id="079f8-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="079f8-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="079f8-129"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="079f8-129"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
