---
title: "(Visual Basic) をインポート/|Microsoft ドキュメント"
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
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
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
ms.openlocfilehash: e994e94dcc3cd00f868b6ae90e4c019eb5b9e2eb
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="imports-visual-basic"></a><span data-ttu-id="6b3e5-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b3e5-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="6b3e5-103">指定したアセンブリから名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b3e5-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b3e5-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="6b3e5-105">引数</span><span class="sxs-lookup"><span data-stu-id="6b3e5-105">Arguments</span></span>  
  
|<span data-ttu-id="6b3e5-106">用語</span><span class="sxs-lookup"><span data-stu-id="6b3e5-106">Term</span></span>|<span data-ttu-id="6b3e5-107">定義</span><span class="sxs-lookup"><span data-stu-id="6b3e5-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="6b3e5-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-108">Required.</span></span> <span data-ttu-id="6b3e5-109">インポートする名前空間のコンマ区切りリスト。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b3e5-110">コメント</span><span class="sxs-lookup"><span data-stu-id="6b3e5-110">Remarks</span></span>  
 <span data-ttu-id="6b3e5-111">`/imports`  オプションは、現在のソース ファイルまたは参照先アセンブリのセットで定義されている任意の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="6b3e5-112">指定された名前空間内のメンバー`/imports`はコンパイル時にすべてのソース コード ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="6b3e5-113">使用して、 [Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)を単一のソース コード ファイルの名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="6b3e5-114">設定する]、[Visual Studio 統合開発環境でのインポート</span><span class="sxs-lookup"><span data-stu-id="6b3e5-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="6b3e5-115">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6b3e5-116">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="6b3e5-117">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="6b3e5-118">2.クリックして、**参照** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-118">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="6b3e5-119">3.横にあるボックスに名前空間の名前を入力、**ユーザー インポートの追加** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-119">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="6b3e5-120">4.クリックして、**ユーザー インポートの追加** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-120">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6b3e5-121">例</span><span class="sxs-lookup"><span data-stu-id="6b3e5-121">Example</span></span>  
 <span data-ttu-id="6b3e5-122">次のコードをコンパイル場合`/imports:system`を指定します。</span><span class="sxs-lookup"><span data-stu-id="6b3e5-122">The following code compiles when `/imports:system` is specified.</span></span>  
  
 <span data-ttu-id="6b3e5-123">[!code-vb[VbVbalrCompiler #&21;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6b3e5-123">[!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b3e5-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b3e5-124">See Also</span></span>  
 <span data-ttu-id="6b3e5-125">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="6b3e5-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="6b3e5-126"> [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="6b3e5-126"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="6b3e5-127"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="6b3e5-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
