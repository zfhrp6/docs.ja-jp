---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6b5da8e5eacacde9de5bdc54ef2d5e4d7f0d2653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="rootnamespace"></a><span data-ttu-id="11328-102">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="11328-102">/rootnamespace</span></span>
<span data-ttu-id="11328-103">すべての型宣言に対して名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="11328-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11328-104">構文</span><span class="sxs-lookup"><span data-stu-id="11328-104">Syntax</span></span>  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="11328-105">引数</span><span class="sxs-lookup"><span data-stu-id="11328-105">Arguments</span></span>  
  
|<span data-ttu-id="11328-106">用語</span><span class="sxs-lookup"><span data-stu-id="11328-106">Term</span></span>|<span data-ttu-id="11328-107">定義</span><span class="sxs-lookup"><span data-stu-id="11328-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="11328-108">現在のプロジェクトのすべての型宣言を囲む名前空間の名前。</span><span class="sxs-lookup"><span data-stu-id="11328-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11328-109">コメント</span><span class="sxs-lookup"><span data-stu-id="11328-109">Remarks</span></span>  
 <span data-ttu-id="11328-110">使用して、Visual Studio 統合開発環境で作成されたプロジェクトをコンパイルする Visual Studio の実行可能ファイル (Devenv.exe) を使用する場合`/rootnamespace`の値を指定する、<xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="11328-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `/rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="11328-111">参照してください[Devenv コマンド ライン スイッチ](/visualstudio/ide/reference/devenv-command-line-switches)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="11328-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="11328-112">共通言語ランタイム MSIL 逆アセンブラーを使用して (`Ildasm.exe`) を出力ファイルの名前空間の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="11328-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="11328-113">Visual Studio で/rootnamespace を設定するには、統合開発環境</span><span class="sxs-lookup"><span data-stu-id="11328-113">To set /rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="11328-114">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="11328-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="11328-115">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11328-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="11328-116">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11328-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="11328-117">2.**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="11328-117">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="11328-118">3.値を変更、**ルート Namespace**ボックス。</span><span class="sxs-lookup"><span data-stu-id="11328-118">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="11328-119">例</span><span class="sxs-lookup"><span data-stu-id="11328-119">Example</span></span>  
 <span data-ttu-id="11328-120">次のコードのコンパイル`In.vb`名前空間のすべての型宣言を囲むおよび`mynamespace`です。</span><span class="sxs-lookup"><span data-stu-id="11328-120">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="11328-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="11328-121">See Also</span></span>  
 [<span data-ttu-id="11328-122">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="11328-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="11328-123">Ildasm.exe (IL 逆アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="11328-123">Ildasm.exe (IL Disassembler)</span></span>](https://msdn.microsoft.com/library/f7dy01k1)  
 [<span data-ttu-id="11328-124">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="11328-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
