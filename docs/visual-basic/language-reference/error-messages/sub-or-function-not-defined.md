---
title: "Sub または Function (Visual Basic) を定義されていない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
dev_langs:
- VB
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
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
ms.openlocfilehash: 837beec039e1fb8f8a796b2781d93de6d4cfb33a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="ad47b-102">Sub または Function が定義されていません。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad47b-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="ad47b-103">A`Sub`または`Function`呼び出せるために定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad47b-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="ad47b-104">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="ad47b-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="ad47b-105">プロシージャ名のスペルが間違っています。</span><span class="sxs-lookup"><span data-stu-id="ad47b-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="ad47b-106">別のプロジェクトでそのプロジェクトへの参照を明示的に追加することがなく、プロシージャを呼び出そうとしている、**参照** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="ad47b-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="ad47b-107">呼び出し元のプロシージャには表示されないプロシージャを指定します。</span><span class="sxs-lookup"><span data-stu-id="ad47b-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="ad47b-108">Windows ダイナミック リンク ライブラリ (DLL) のルーチンまたは指定したライブラリまたはコードのリソースに含まれていない Macintosh コード リソース ルーチンを宣言します。</span><span class="sxs-lookup"><span data-stu-id="ad47b-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ad47b-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ad47b-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="ad47b-110">プロシージャ名のスペルが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ad47b-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="ad47b-111">呼び出すには必要な手順を含むプロジェクトの名前を検索、**参照** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="ad47b-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="ad47b-112">表示されない場合は、クリックして、**参照**を検索 ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ad47b-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="ad47b-113">プロジェクト名の左側にチェック ボックスを選択し、クリックして**OK**します。</span><span class="sxs-lookup"><span data-stu-id="ad47b-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="ad47b-114">ルーチンの名前を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ad47b-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad47b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad47b-115">See Also</span></span>  
 <span data-ttu-id="ad47b-116">[エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md) </span><span class="sxs-lookup"><span data-stu-id="ad47b-116">[Error Types](../../../visual-basic/programming-guide/language-features/error-types.md) </span></span>  
<span data-ttu-id="ad47b-117"> [プロジェクトの参照を管理します。](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="ad47b-117"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="ad47b-118"> [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ad47b-118"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="ad47b-119"> [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)</span><span class="sxs-lookup"><span data-stu-id="ad47b-119"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)</span></span>
