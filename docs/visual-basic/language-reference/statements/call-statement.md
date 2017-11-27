---
title: "Call ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="32f6f-102">Call ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32f6f-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="32f6f-103">転送コントロールを`Function`、 `Sub`、またはダイナミック リンク ライブラリ (DLL) プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="32f6f-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32f6f-104">構文</span><span class="sxs-lookup"><span data-stu-id="32f6f-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="32f6f-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="32f6f-105">Parts</span></span>  
 `procedureName`  
 <span data-ttu-id="32f6f-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="32f6f-106">Required.</span></span> <span data-ttu-id="32f6f-107">呼び出すプロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="32f6f-107">Name of the procedure to call.</span></span>  
  
 `argumentList`  
 <span data-ttu-id="32f6f-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="32f6f-108">Optional.</span></span> <span data-ttu-id="32f6f-109">変数または呼び出された場合、プロシージャに渡される引数を表す式の一覧です。</span><span class="sxs-lookup"><span data-stu-id="32f6f-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="32f6f-110">複数の引数は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="32f6f-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="32f6f-111">含める場合`argumentList`かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="32f6f-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32f6f-112">コメント</span><span class="sxs-lookup"><span data-stu-id="32f6f-112">Remarks</span></span>  
 <span data-ttu-id="32f6f-113">使用することができます、`Call`キーワード、プロシージャを呼び出すときにします。</span><span class="sxs-lookup"><span data-stu-id="32f6f-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="32f6f-114">ほとんどのプロシージャ呼び出しのためには、このキーワードを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="32f6f-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="32f6f-115">通常使用する、`Call`キーワードと呼ばれる式は、識別子で開始しない場合。</span><span class="sxs-lookup"><span data-stu-id="32f6f-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="32f6f-116">使用、`Call`キーワードの他の使用はお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="32f6f-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="32f6f-117">プロシージャは、値を返す場合、`Call`ステートメントにそれを廃棄します。</span><span class="sxs-lookup"><span data-stu-id="32f6f-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32f6f-118">例</span><span class="sxs-lookup"><span data-stu-id="32f6f-118">Example</span></span>  
 <span data-ttu-id="32f6f-119">次のコードは、2 つの例を示しています。 ここで、`Call`キーワードは、プロシージャを呼び出す必要です。</span><span class="sxs-lookup"><span data-stu-id="32f6f-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="32f6f-120">どちらの例では、呼び出された式は識別子で開始しません。</span><span class="sxs-lookup"><span data-stu-id="32f6f-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="32f6f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="32f6f-121">See Also</span></span>  
 [<span data-ttu-id="32f6f-122">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="32f6f-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="32f6f-123">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="32f6f-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="32f6f-124">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="32f6f-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="32f6f-125">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="32f6f-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
