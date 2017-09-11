---
title: "/rootnamespace |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
dev_langs:
- VB
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: 13
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
ms.openlocfilehash: 9a7a26407e981d3aea58d970d88bf25025e6bba6
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="rootnamespace"></a><span data-ttu-id="acf34-102">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="acf34-102">/rootnamespace</span></span>
<span data-ttu-id="acf34-103">すべての型宣言に対して名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="acf34-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf34-104">構文</span><span class="sxs-lookup"><span data-stu-id="acf34-104">Syntax</span></span>  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="acf34-105">引数</span><span class="sxs-lookup"><span data-stu-id="acf34-105">Arguments</span></span>  
  
|<span data-ttu-id="acf34-106">用語</span><span class="sxs-lookup"><span data-stu-id="acf34-106">Term</span></span>|<span data-ttu-id="acf34-107">定義</span><span class="sxs-lookup"><span data-stu-id="acf34-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="acf34-108">現在のプロジェクトのすべての型宣言を囲む名前空間の名前。</span><span class="sxs-lookup"><span data-stu-id="acf34-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acf34-109">コメント</span><span class="sxs-lookup"><span data-stu-id="acf34-109">Remarks</span></span>  
 <span data-ttu-id="acf34-110">使用して、Visual Studio 統合開発環境で作成したプロジェクトをコンパイルする Visual Studio の実行可能ファイル (Devenv.exe) を使用する場合`/rootnamespace`の値を指定する、<xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>プロパティ</xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>。</span><span class="sxs-lookup"><span data-stu-id="acf34-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `/rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="acf34-111">参照してください[Devenv コマンド ライン スイッチ](https://docs.microsoft.com/visualstudio/ide/reference/devenv-command-line-switches)の詳細。</span><span class="sxs-lookup"><span data-stu-id="acf34-111">See [Devenv Command Line Switches](https://docs.microsoft.com/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="acf34-112">共通言語ランタイム MSIL 逆アセンブラーを使用して (は`ldasm.exe`) を出力ファイルの名前空間の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="acf34-112">Use the common language runtime MSIL Disassembler (I`ldasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="acf34-113">統合開発環境 Visual Studio で/rootnamespace を設定するには</span><span class="sxs-lookup"><span data-stu-id="acf34-113">To set /rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="acf34-114">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="acf34-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="acf34-115">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="acf34-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="acf34-116">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acf34-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="acf34-117">2.**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="acf34-117">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="acf34-118">3.値を変更、**ルート Namespace**ボックス。</span><span class="sxs-lookup"><span data-stu-id="acf34-118">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="acf34-119">例</span><span class="sxs-lookup"><span data-stu-id="acf34-119">Example</span></span>  
 <span data-ttu-id="acf34-120">次のコードのコンパイル`In.vb`し、名前空間内のすべての型宣言を囲む`mynamespace`します。</span><span class="sxs-lookup"><span data-stu-id="acf34-120">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="acf34-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="acf34-121">See Also</span></span>  
 <span data-ttu-id="acf34-122">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="acf34-122">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="acf34-123"> [Ildasm.exe (IL 逆アセンブラー)](https://msdn.microsoft.com/library/f7dy01k1) </span><span class="sxs-lookup"><span data-stu-id="acf34-123"> [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1) </span></span>  
<span data-ttu-id="acf34-124"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="acf34-124"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
