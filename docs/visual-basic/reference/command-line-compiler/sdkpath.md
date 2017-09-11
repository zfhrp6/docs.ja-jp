---
title: "/sdkpath |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
dev_langs:
- VB
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: 15
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
ms.openlocfilehash: 2e32bb403347063edcf0d47fd4a7511a0da1f340
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="sdkpath"></a><span data-ttu-id="67e23-102">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="67e23-102">/sdkpath</span></span>
<span data-ttu-id="67e23-103">Mscorlib.dll および Microsoft.VisualBasic.dll の位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="67e23-103">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67e23-104">構文</span><span class="sxs-lookup"><span data-stu-id="67e23-104">Syntax</span></span>  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="67e23-105">引数</span><span class="sxs-lookup"><span data-stu-id="67e23-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="67e23-106">コンパイルに使用するには、Mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを含むディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="67e23-106">The directory containing the versions of Mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="67e23-107">読み込まれるまで、このパスは検証されません。</span><span class="sxs-lookup"><span data-stu-id="67e23-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="67e23-108">ディレクトリ名を引用符で囲みます ("")、スペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="67e23-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67e23-109">コメント</span><span class="sxs-lookup"><span data-stu-id="67e23-109">Remarks</span></span>  
 <span data-ttu-id="67e23-110">このオプションでは、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラに既定以外の場所から Mscorlib.dll および Microsoft.VisualBasic.dll のファイルをロードします。</span><span class="sxs-lookup"><span data-stu-id="67e23-110">This option tells the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to load the Mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="67e23-111">`/sdkpath`オプションで使用するように設計されました[/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)します。</span><span class="sxs-lookup"><span data-stu-id="67e23-111">The `/sdkpath` option was designed to be used with [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="67e23-112">[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]これらの異なるバージョンを使用して型と、デバイスが見つかりません。 言語機能の使用を回避するためにライブラリをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="67e23-112">The [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67e23-113">`/sdkpath`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="67e23-113">The `/sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="67e23-114">`/sdkpath`場合は、オプションが設定されて、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]デバイス プロジェクトが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="67e23-114">The `/sdkpath` option is set when a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="67e23-115">使用して、コンパイラが、Visual Basic ランタイム ライブラリへの参照をしないでコンパイルことを指定する、`/vbruntime`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="67e23-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `/vbruntime` compiler option.</span></span> <span data-ttu-id="67e23-116">詳細については、次を参照してください。 [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)します。</span><span class="sxs-lookup"><span data-stu-id="67e23-116">For more information, see [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="67e23-117">例</span><span class="sxs-lookup"><span data-stu-id="67e23-117">Example</span></span>  
 <span data-ttu-id="67e23-118">次のコードのコンパイル`Myfile.vb`で、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]の既定のインストール ディレクトリで見つかった Mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを使用して、 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] C ドライブにします。</span><span class="sxs-lookup"><span data-stu-id="67e23-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] on the C drive.</span></span> <span data-ttu-id="67e23-119">通常の最新バージョンを使用すると、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="67e23-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="67e23-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="67e23-120">See Also</span></span>  
 <span data-ttu-id="67e23-121">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="67e23-121">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="67e23-122"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="67e23-122"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="67e23-123"> [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md) </span><span class="sxs-lookup"><span data-stu-id="67e23-123"> [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md) </span></span>  
<span data-ttu-id="67e23-124"> [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)</span><span class="sxs-lookup"><span data-stu-id="67e23-124"> [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)</span></span>
