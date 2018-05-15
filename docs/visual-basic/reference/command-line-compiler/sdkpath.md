---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 162c7d58350c381ec667e8a4cd11c03e83fcdf44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-sdkpath"></a><span data-ttu-id="494bc-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="494bc-102">-sdkpath</span></span>
<span data-ttu-id="494bc-103">Mscorlib.dll および Microsoft.VisualBasic.dll の位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="494bc-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="494bc-104">構文</span><span class="sxs-lookup"><span data-stu-id="494bc-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="494bc-105">引数</span><span class="sxs-lookup"><span data-stu-id="494bc-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="494bc-106">Mscorlib.dll および Microsoft.VisualBasic.dll のコンパイルを使用するのバージョンを含むディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="494bc-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="494bc-107">読み込まれるまで、このパスは検証されません。</span><span class="sxs-lookup"><span data-stu-id="494bc-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="494bc-108">ディレクトリ名を引用符で囲みます ("")、スペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="494bc-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="494bc-109">コメント</span><span class="sxs-lookup"><span data-stu-id="494bc-109">Remarks</span></span>  
 <span data-ttu-id="494bc-110">このオプションは、既定以外の場所から mscorlib.dll および Microsoft.VisualBasic.dll のファイルを読み込む Visual Basic コンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="494bc-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="494bc-111">`-sdkpath`オプションで使用するように設計されました[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)です。</span><span class="sxs-lookup"><span data-stu-id="494bc-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="494bc-112">[!INCLUDE[Compact](~/includes/compact-md.md)]これらの異なるバージョンを使用してサポート ライブラリを型と、デバイスが見つかりません。 言語機能は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="494bc-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="494bc-113">`-sdkpath`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="494bc-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="494bc-114">`-sdkpath` Visual Basic プロジェクトのデバイスが読み込まれるときに、オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="494bc-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="494bc-115">使用して、Visual Basic ランタイム ライブラリへの参照なしコンパイラでコンパイルする必要があることを指定することができます、`-vbruntime`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="494bc-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="494bc-116">詳細については、次を参照してください。 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)です。</span><span class="sxs-lookup"><span data-stu-id="494bc-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="494bc-117">例</span><span class="sxs-lookup"><span data-stu-id="494bc-117">Example</span></span>  
 <span data-ttu-id="494bc-118">次のコードのコンパイル`Myfile.vb`で、[!INCLUDE[Compact](~/includes/compact-md.md)]の既定のインストール ディレクトリで見つかった Mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを使用して、[!INCLUDE[Compact](~/includes/compact-md.md)]が C ドライブにします。</span><span class="sxs-lookup"><span data-stu-id="494bc-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="494bc-119">通常の最新バージョンを使用すると、[!INCLUDE[Compact](~/includes/compact-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="494bc-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="494bc-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="494bc-120">See Also</span></span>  
 [<span data-ttu-id="494bc-121">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="494bc-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="494bc-122">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="494bc-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="494bc-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="494bc-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="494bc-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="494bc-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
