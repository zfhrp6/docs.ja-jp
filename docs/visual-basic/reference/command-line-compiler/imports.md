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
ms.openlocfilehash: 6cdb7cff2221930113d6b49a640da0844f175f1b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="imports-visual-basic"></a><span data-ttu-id="bf164-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf164-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="bf164-103">指定したアセンブリから名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="bf164-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf164-104">構文</span><span class="sxs-lookup"><span data-stu-id="bf164-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="bf164-105">引数</span><span class="sxs-lookup"><span data-stu-id="bf164-105">Arguments</span></span>  
  
|<span data-ttu-id="bf164-106">用語</span><span class="sxs-lookup"><span data-stu-id="bf164-106">Term</span></span>|<span data-ttu-id="bf164-107">定義</span><span class="sxs-lookup"><span data-stu-id="bf164-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="bf164-108">必須。</span><span class="sxs-lookup"><span data-stu-id="bf164-108">Required.</span></span> <span data-ttu-id="bf164-109">インポートする名前空間のコンマ区切り一覧。</span><span class="sxs-lookup"><span data-stu-id="bf164-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf164-110">コメント</span><span class="sxs-lookup"><span data-stu-id="bf164-110">Remarks</span></span>  
 <span data-ttu-id="bf164-111">`/imports`オプションは、現在のソース ファイルまたは参照先アセンブリのセット内で定義された任意の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="bf164-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="bf164-112">指定された名前空間内のメンバー`/imports`コンパイルですべてのソース コード ファイルに使用します。</span><span class="sxs-lookup"><span data-stu-id="bf164-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="bf164-113">使用して、 [Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)を 1 つのソース コード ファイルの名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="bf164-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="bf164-114">設定する Visual Studio 統合開発環境ではインポート/</span><span class="sxs-lookup"><span data-stu-id="bf164-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="bf164-115">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="bf164-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bf164-116">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bf164-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="bf164-117">2.**[参照]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bf164-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="bf164-118">3.横にあるボックスに名前空間の名前を入力、**ユーザー インポートの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bf164-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="bf164-119">4.クリックして、**ユーザー インポートの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bf164-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bf164-120">例</span><span class="sxs-lookup"><span data-stu-id="bf164-120">Example</span></span>  
 <span data-ttu-id="bf164-121">次のコードをコンパイル時に`/imports:system`を指定します。</span><span class="sxs-lookup"><span data-stu-id="bf164-121">The following code compiles when `/imports:system` is specified.</span></span>  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bf164-122">参照</span><span class="sxs-lookup"><span data-stu-id="bf164-122">See Also</span></span>  
 [<span data-ttu-id="bf164-123">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="bf164-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="bf164-124">参照と Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="bf164-124">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="bf164-125">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="bf164-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
