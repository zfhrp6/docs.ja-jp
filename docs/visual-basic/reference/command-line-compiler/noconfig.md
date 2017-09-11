---
title: "/noconfig |Microsoft ドキュメント"
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
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
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
ms.openlocfilehash: fe3271e4a119e0c40370a7351bb39188f4d1c8ef
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="noconfig"></a><span data-ttu-id="df8dc-102">/noconfig</span><span class="sxs-lookup"><span data-stu-id="df8dc-102">/noconfig</span></span>
<span data-ttu-id="df8dc-103">コンパイラが含まれていないことに自動的に一般的に使用される指定[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリまたはインポート、`System`と`Microsoft.VisualBasic`名前空間。</span><span class="sxs-lookup"><span data-stu-id="df8dc-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df8dc-104">構文</span><span class="sxs-lookup"><span data-stu-id="df8dc-104">Syntax</span></span>  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="df8dc-105">コメント</span><span class="sxs-lookup"><span data-stu-id="df8dc-105">Remarks</span></span>  
 <span data-ttu-id="df8dc-106">`/noconfig`オプション Vbc.exe ファイルと同じディレクトリにあると、Vbc.rsp ファイルでコンパイルしていないコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="df8dc-106">The `/noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="df8dc-107">Vbc.rsp ファイルを参照して、一般的に使用される[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリとインポート、`System`と`Microsoft.VisualBasic`名前空間。</span><span class="sxs-lookup"><span data-stu-id="df8dc-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="df8dc-108">しない限り、System.dll アセンブリが、コンパイラによって暗黙的に参照、`/nostdlib`オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="df8dc-108">The compiler implicitly references the System.dll assembly unless the `/nostdlib` option is specified.</span></span> <span data-ttu-id="df8dc-109">`/nostdlib`オプションと、Vbc.rsp でコンパイルや System.dll アセンブリを自動的に参照を行わないコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="df8dc-109">The `/nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df8dc-110">Mscorlib.dll および Microsoft.VisualBasic.dll のアセンブリは常に参照します。</span><span class="sxs-lookup"><span data-stu-id="df8dc-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="df8dc-111">すべて Vbc.exe のコンパイル時に含める必要がある追加のコンパイラ オプションを指定すると、Vbc.rsp ファイルを変更することができます (を指定する場合を除いて、`/noconfig`オプション)。</span><span class="sxs-lookup"><span data-stu-id="df8dc-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `/noconfig` option).</span></span> <span data-ttu-id="df8dc-112">詳しくは、「[@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="df8dc-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="df8dc-113">コンパイラに渡されるオプションの処理、`vbc`コマンドの最後です。</span><span class="sxs-lookup"><span data-stu-id="df8dc-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="df8dc-114">そのため、コマンドラインに指定したオプションは、Vbc.rsp ファイル内の同じオプションの設定を上書きします。</span><span class="sxs-lookup"><span data-stu-id="df8dc-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df8dc-115">`/noconfig`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="df8dc-115">The `/noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df8dc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="df8dc-116">See Also</span></span>  
 <span data-ttu-id="df8dc-117">[/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md) </span><span class="sxs-lookup"><span data-stu-id="df8dc-117">[/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md) </span></span>  
<span data-ttu-id="df8dc-118"> [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="df8dc-118"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="df8dc-119"> [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md) </span><span class="sxs-lookup"><span data-stu-id="df8dc-119"> [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md) </span></span>  
<span data-ttu-id="df8dc-120"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)</span><span class="sxs-lookup"><span data-stu-id="df8dc-120"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)</span></span>
