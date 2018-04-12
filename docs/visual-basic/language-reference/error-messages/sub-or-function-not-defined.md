---
title: Sub または Function が定義されていません。(Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="01911-102">Sub または Function が定義されていません。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01911-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="01911-103">A`Sub`または`Function`呼び出すには定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01911-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="01911-104">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="01911-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="01911-105">プロシージャ名のスペルが間違っています。</span><span class="sxs-lookup"><span data-stu-id="01911-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="01911-106">別のプロジェクトでそのプロジェクトへの参照を明示的に追加することがなく、プロシージャを呼び出そうとしている、**参照** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="01911-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="01911-107">呼び出し元のプロシージャには表示されませんプロシージャを指定します。</span><span class="sxs-lookup"><span data-stu-id="01911-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="01911-108">Windows ダイナミック リンク ライブラリ (DLL) のルーチンまたは指定したライブラリまたはコード リソースに含まれていない Macintosh コード リソース ルーチンを宣言します。</span><span class="sxs-lookup"><span data-stu-id="01911-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="01911-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="01911-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="01911-110">プロシージャ名のスペルが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="01911-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="01911-111">呼び出しに必要な手順を含むプロジェクトの名前を検索、**参照** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="01911-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="01911-112">表示されない場合にクリックして、**参照**検索ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="01911-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="01911-113">プロジェクト名の左側にチェック ボックスをオンにし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="01911-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="01911-114">ルーチンの名前を確認してください。</span><span class="sxs-lookup"><span data-stu-id="01911-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01911-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="01911-115">See Also</span></span>  
 [<span data-ttu-id="01911-116">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="01911-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="01911-117">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="01911-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="01911-118">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="01911-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="01911-119">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="01911-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
