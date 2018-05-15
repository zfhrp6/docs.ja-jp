---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3764409f13a00f6d8a050bfbdd0f59e537a5ded3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="d7009-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7009-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="d7009-103">コンパイラが自動的に標準のライブラリを参照します。</span><span class="sxs-lookup"><span data-stu-id="d7009-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7009-104">構文</span><span class="sxs-lookup"><span data-stu-id="d7009-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="d7009-105">コメント</span><span class="sxs-lookup"><span data-stu-id="d7009-105">Remarks</span></span>  
 <span data-ttu-id="d7009-106">`-nostdlib`オプションは、System.dll アセンブリへの自動参照を削除し、コンパイラが Vbc.rsp ファイルを読み取ることを防止します。</span><span class="sxs-lookup"><span data-stu-id="d7009-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="d7009-107">Vbc.exe ファイルと同じディレクトリにある、Vbc.rsp ファイルを一般的に使用される参照[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリとインポート、`System`と`Microsoft.VisualBasic`名前空間。</span><span class="sxs-lookup"><span data-stu-id="d7009-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7009-108">Mscorlib.dll および Microsoft.VisualBasic.dll のアセンブリは、常に参照されます。</span><span class="sxs-lookup"><span data-stu-id="d7009-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7009-109">`-nostdlib`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="d7009-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7009-110">例</span><span class="sxs-lookup"><span data-stu-id="d7009-110">Example</span></span>  
 <span data-ttu-id="d7009-111">次のコードのコンパイル`T2.vb`標準ライブラリを参照することがなくです。</span><span class="sxs-lookup"><span data-stu-id="d7009-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="d7009-112">設定する必要があります、`_MYTYPE`条件付きコンパイル定数を削除するには、「空白」の文字列に、`My`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d7009-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7009-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7009-113">See Also</span></span>  
 [<span data-ttu-id="d7009-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="d7009-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="d7009-115">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="d7009-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d7009-116">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="d7009-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="d7009-117">My で利用可能なオブジェクトのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="d7009-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
