---
title: "パラメーターと引数の違い (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="4159d-102">パラメーターと引数の違い (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4159d-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="4159d-103">ほとんどの場合、プロシージャが呼び出されたときの状況に関する情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="4159d-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="4159d-104">繰り返しまたは共有のタスクを実行する手順は、呼び出しごとに異なる情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="4159d-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="4159d-105">この情報は、変数、定数、およびメソッドを呼び出すときに、プロシージャに渡す式で構成されます。</span><span class="sxs-lookup"><span data-stu-id="4159d-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="4159d-106">プロシージャの定義、プロシージャにこの情報を通信するために、*パラメーター*、呼び出し元のコードに渡すと、*引数*そのパラメーターにします。</span><span class="sxs-lookup"><span data-stu-id="4159d-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="4159d-107">駐車場パラメーターと引数は、自動車を検討することができます。</span><span class="sxs-lookup"><span data-stu-id="4159d-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="4159d-108">な車は、異なる時刻で駐車場駐車できる、同様呼び出し元のコードは、するには、プロシージャが呼び出されるたびに同じパラメーターに別の引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4159d-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="4159d-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4159d-109">Parameters</span></span>  
 <span data-ttu-id="4159d-110">A*パラメーター*プロシージャには、このメソッドを呼び出すときに渡すことが期待される値を表します。</span><span class="sxs-lookup"><span data-stu-id="4159d-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="4159d-111">プロシージャの宣言では、そのパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="4159d-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="4159d-112">定義するとき、`Function`または`Sub`プロシージャを指定する、*パラメーター リスト*プロシージャ名をすぐに続くかっこにします。</span><span class="sxs-lookup"><span data-stu-id="4159d-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="4159d-113">各パラメーターの名前、データ型、および引き渡し方法を指定 ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md))。</span><span class="sxs-lookup"><span data-stu-id="4159d-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="4159d-114">パラメーターが省略可能であることもあります。</span><span class="sxs-lookup"><span data-stu-id="4159d-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="4159d-115">これは、値を渡すことを呼び出し元のコードがないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="4159d-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="4159d-116">各パラメーターの名前を果たす、*ローカル変数*の手順でします。</span><span class="sxs-lookup"><span data-stu-id="4159d-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="4159d-117">パラメーター名を使用すると、他の変数を使用するのと同様にします。</span><span class="sxs-lookup"><span data-stu-id="4159d-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="4159d-118">引数</span><span class="sxs-lookup"><span data-stu-id="4159d-118">Arguments</span></span>  
 <span data-ttu-id="4159d-119">*引数*プロシージャを呼び出す場合、プロシージャのパラメーターに渡す値を表します。</span><span class="sxs-lookup"><span data-stu-id="4159d-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="4159d-120">呼び出し元のコードは、プロシージャを呼び出すときに、引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4159d-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="4159d-121">呼び出すと、`Function`または`Sub`が含まれて、プロシージャには、*引数リスト*プロシージャ名をすぐに続くかっこ内です。</span><span class="sxs-lookup"><span data-stu-id="4159d-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="4159d-122">各引数は、一覧内の同じ位置でのパラメーターに対応します。</span><span class="sxs-lookup"><span data-stu-id="4159d-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="4159d-123">パラメーターの定義とは対照的引数には名前がありません。</span><span class="sxs-lookup"><span data-stu-id="4159d-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="4159d-124">各引数は、ゼロまたは複数の変数、定数、およびリテラルに含めることができる式です。</span><span class="sxs-lookup"><span data-stu-id="4159d-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="4159d-125">式の評価結果のデータ型が、対応するパラメーターに対して定義されているデータ型に一致することは通常、パラメーターの型に変換可能ないずれの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4159d-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4159d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="4159d-126">See Also</span></span>  
 [<span data-ttu-id="4159d-127">手順</span><span class="sxs-lookup"><span data-stu-id="4159d-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="4159d-128">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="4159d-128">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="4159d-129">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="4159d-129">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="4159d-130">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="4159d-130">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="4159d-131">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="4159d-131">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="4159d-132">方法 : プロシージャにパラメーターを定義する</span><span class="sxs-lookup"><span data-stu-id="4159d-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="4159d-133">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="4159d-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="4159d-134">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="4159d-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="4159d-135">再帰プロシージャ</span><span class="sxs-lookup"><span data-stu-id="4159d-135">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="4159d-136">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="4159d-136">Procedure Overloading</span></span>](./procedure-overloading.md)
