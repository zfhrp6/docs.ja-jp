---
title: /sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 876922385124db3e8db12c93c75194da83d2526c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sdkpath"></a><span data-ttu-id="52563-102">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="52563-102">/sdkpath</span></span>
<span data-ttu-id="52563-103">Mscorlib.dll および Microsoft.VisualBasic.dll の位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="52563-103">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52563-104">構文</span><span class="sxs-lookup"><span data-stu-id="52563-104">Syntax</span></span>  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="52563-105">引数</span><span class="sxs-lookup"><span data-stu-id="52563-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="52563-106">コンパイルに使用するには、Mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを含むディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="52563-106">The directory containing the versions of Mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="52563-107">読み込まれるまで、このパスは検証されません。</span><span class="sxs-lookup"><span data-stu-id="52563-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="52563-108">ディレクトリ名を引用符で囲みます ("")、スペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="52563-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52563-109">コメント</span><span class="sxs-lookup"><span data-stu-id="52563-109">Remarks</span></span>  
 <span data-ttu-id="52563-110">このオプションでは、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラに既定以外の場所から Mscorlib.dll および Microsoft.VisualBasic.dll のファイルをロードします。</span><span class="sxs-lookup"><span data-stu-id="52563-110">This option tells the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to load the Mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="52563-111">`/sdkpath`オプションで使用するように設計されました[/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)です。</span><span class="sxs-lookup"><span data-stu-id="52563-111">The `/sdkpath` option was designed to be used with [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="52563-112">[!INCLUDE[Compact](~/includes/compact-md.md)]これらの異なるバージョンを使用してサポート ライブラリを型と、デバイスが見つかりません。 言語機能は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="52563-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52563-113">`/sdkpath`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="52563-113">The `/sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="52563-114">`/sdkpath`場合は、オプションが設定されて、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]デバイス プロジェクトが読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="52563-114">The `/sdkpath` option is set when a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="52563-115">使用して、Visual Basic ランタイム ライブラリへの参照なしコンパイラでコンパイルする必要があることを指定することができます、`/vbruntime`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="52563-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `/vbruntime` compiler option.</span></span> <span data-ttu-id="52563-116">詳細については、次を参照してください。 [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)です。</span><span class="sxs-lookup"><span data-stu-id="52563-116">For more information, see [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52563-117">例</span><span class="sxs-lookup"><span data-stu-id="52563-117">Example</span></span>  
 <span data-ttu-id="52563-118">次のコードのコンパイル`Myfile.vb`で、[!INCLUDE[Compact](~/includes/compact-md.md)]の既定のインストール ディレクトリで見つかった Mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを使用して、[!INCLUDE[Compact](~/includes/compact-md.md)]が C ドライブにします。</span><span class="sxs-lookup"><span data-stu-id="52563-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="52563-119">通常の最新バージョンを使用すると、[!INCLUDE[Compact](~/includes/compact-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="52563-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="52563-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="52563-120">See Also</span></span>  
 [<span data-ttu-id="52563-121">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="52563-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="52563-122">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="52563-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="52563-123">/netcf</span><span class="sxs-lookup"><span data-stu-id="52563-123">/netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="52563-124">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="52563-124">/vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
