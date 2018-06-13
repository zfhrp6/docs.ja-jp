---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac495e10be2ec1534dc9d9081aef369773d93e17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649875"
---
# <a name="-win32resource"></a><span data-ttu-id="9fbf3-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="9fbf3-102">-win32resource</span></span>
<span data-ttu-id="9fbf3-103">出力ファイルには、Win32 リソース ファイルを挿入します。</span><span class="sxs-lookup"><span data-stu-id="9fbf3-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fbf3-104">構文</span><span class="sxs-lookup"><span data-stu-id="9fbf3-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9fbf3-105">引数</span><span class="sxs-lookup"><span data-stu-id="9fbf3-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="9fbf3-106">出力ファイルに追加するリソース ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="9fbf3-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="9fbf3-107">ファイル名を引用符で囲みます ("")、スペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="9fbf3-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fbf3-108">コメント</span><span class="sxs-lookup"><span data-stu-id="9fbf3-108">Remarks</span></span>  
 <span data-ttu-id="9fbf3-109">Microsoft Windows リソース コンパイラ (RC) とは、Win32 リソース ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9fbf3-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="9fbf3-110">Win32 リソースは、バージョンを含めることができますか、ビットマップ (アイコン) 情報を入力でアプリケーションを識別する**ファイル エクスプ ローラー**です。</span><span class="sxs-lookup"><span data-stu-id="9fbf3-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="9fbf3-111">指定しない場合`-win32resource`コンパイラはアセンブリのバージョンに基づくバージョン情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="9fbf3-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="9fbf3-112">`-win32resource`と`-win32icon`オプションは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="9fbf3-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="9fbf3-113">参照してください[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)参照に、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]リソース ファイル、または[-リソース (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)をアタッチする、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]リソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="9fbf3-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fbf3-114">`-win32resource`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="9fbf3-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fbf3-115">例</span><span class="sxs-lookup"><span data-stu-id="9fbf3-115">Example</span></span>  
 <span data-ttu-id="9fbf3-116">次のコードのコンパイル`In.vb`Win32 リソース ファイルをアタッチおよび`Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="9fbf3-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fbf3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fbf3-117">See Also</span></span>  
 [<span data-ttu-id="9fbf3-118">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="9fbf3-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9fbf3-119">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="9fbf3-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
