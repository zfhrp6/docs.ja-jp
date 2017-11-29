---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8e9cd761263b3b61a4e6d3e33c5f7f875be7a1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imports-visual-basic"></a><span data-ttu-id="1e2b8-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e2b8-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="1e2b8-103">指定したアセンブリから名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e2b8-104">構文</span><span class="sxs-lookup"><span data-stu-id="1e2b8-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e2b8-105">引数</span><span class="sxs-lookup"><span data-stu-id="1e2b8-105">Arguments</span></span>  
  
|<span data-ttu-id="1e2b8-106">用語</span><span class="sxs-lookup"><span data-stu-id="1e2b8-106">Term</span></span>|<span data-ttu-id="1e2b8-107">定義</span><span class="sxs-lookup"><span data-stu-id="1e2b8-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="1e2b8-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-108">Required.</span></span> <span data-ttu-id="1e2b8-109">インポートする名前空間のコンマ区切り一覧。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e2b8-110">コメント</span><span class="sxs-lookup"><span data-stu-id="1e2b8-110">Remarks</span></span>  
 <span data-ttu-id="1e2b8-111">`/imports`オプションは、現在のソース ファイルまたは参照先アセンブリのセット内で定義された任意の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="1e2b8-112">指定された名前空間内のメンバー`/imports`コンパイルですべてのソース コード ファイルに使用します。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="1e2b8-113">使用して、 [Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)を 1 つのソース コード ファイルの名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="1e2b8-114">設定する Visual Studio 統合開発環境ではインポート/</span><span class="sxs-lookup"><span data-stu-id="1e2b8-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1e2b8-115">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1e2b8-116">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="1e2b8-117">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="1e2b8-118">2.**[参照]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-118">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="1e2b8-119">3.横にあるボックスに名前空間の名前を入力、**ユーザー インポートの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-119">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="1e2b8-120">4.クリックして、**ユーザー インポートの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-120">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1e2b8-121">例</span><span class="sxs-lookup"><span data-stu-id="1e2b8-121">Example</span></span>  
 <span data-ttu-id="1e2b8-122">次のコードをコンパイル時に`/imports:system`を指定します。</span><span class="sxs-lookup"><span data-stu-id="1e2b8-122">The following code compiles when `/imports:system` is specified.</span></span>  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1e2b8-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e2b8-123">See Also</span></span>  
 [<span data-ttu-id="1e2b8-124">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="1e2b8-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1e2b8-125">参照と Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="1e2b8-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="1e2b8-126">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="1e2b8-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
