---
title: "/nostdlib (Visual Basic) |Microsoft ドキュメント"
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
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: 18
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
ms.openlocfilehash: 046e2b845324ed1c2f8c15bbb029fe84f7693f6e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="nostdlib-visual-basic"></a><span data-ttu-id="b9351-102">/nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9351-102">/nostdlib (Visual Basic)</span></span>
<span data-ttu-id="b9351-103">コンパイラが自動的に標準のライブラリを参照します。</span><span class="sxs-lookup"><span data-stu-id="b9351-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9351-104">構文</span><span class="sxs-lookup"><span data-stu-id="b9351-104">Syntax</span></span>  
  
```  
/nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="b9351-105">コメント</span><span class="sxs-lookup"><span data-stu-id="b9351-105">Remarks</span></span>  
 <span data-ttu-id="b9351-106">`/nostdlib`  オプションは、System.dll アセンブリへの自動参照を削除され、コンパイラが、Vbc.rsp ファイルの読み取りができなくなります。</span><span class="sxs-lookup"><span data-stu-id="b9351-106">The `/nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="b9351-107">Vbc.rsp ファイル-Vbc.exe ファイルと同じディレクトリにある、一般的に使用される参照[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリとインポート、`System`と`Microsoft.VisualBasic`名前空間。</span><span class="sxs-lookup"><span data-stu-id="b9351-107">The Vbc.rsp file—which is located in the same directory as the Vbc.exe file—references the commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9351-108">Mscorlib.dll および Microsoft.VisualBasic.dll のアセンブリは常に参照します。</span><span class="sxs-lookup"><span data-stu-id="b9351-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9351-109">`/nostdlib`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="b9351-109">The `/nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9351-110">例</span><span class="sxs-lookup"><span data-stu-id="b9351-110">Example</span></span>  
 <span data-ttu-id="b9351-111">次のコードのコンパイル`T2.vb`標準ライブラリを参照しなくてもします。</span><span class="sxs-lookup"><span data-stu-id="b9351-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="b9351-112">設定する必要があります、`_MYTYPE`条件付きコンパイル定数文字列を削除するには、「空」を`My`オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="b9351-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9351-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9351-113">See Also</span></span>  
 <span data-ttu-id="b9351-114">[/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="b9351-114">[/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="b9351-115"> [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="b9351-115"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="b9351-116"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="b9351-116"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="b9351-117"> [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)</span><span class="sxs-lookup"><span data-stu-id="b9351-117"> [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)</span></span>
