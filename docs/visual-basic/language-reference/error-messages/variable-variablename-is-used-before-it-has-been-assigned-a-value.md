---
title: 変数 &#39;&lt;variablename&gt;&#39; は、値が割り当てられる前に使用
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 201667c250e15bb9af73e64e2d8c924c1952d1be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="84f62-102">変数 &#39;&lt;variablename&gt;&#39; は、値が割り当てられる前に使用</span><span class="sxs-lookup"><span data-stu-id="84f62-102">Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value</span></span>
<span data-ttu-id="84f62-103">変数 '\<variablename >' は、値が割り当てられる前に使用します。</span><span class="sxs-lookup"><span data-stu-id="84f62-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="84f62-104">結果として、実行時に null 参照の例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84f62-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="84f62-105">アプリケーションが任意の値を割り当てる前に、変数を読み取るをコードに少なくとも 1 つの可能なパスがあります。</span><span class="sxs-lookup"><span data-stu-id="84f62-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="84f62-106">変数に値が割り当てられていない場合、変数はそのデータ型の既定値を保持します。</span><span class="sxs-lookup"><span data-stu-id="84f62-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="84f62-107">参照データ型では、その既定値は[Nothing](../../../visual-basic/language-reference/nothing.md)です。</span><span class="sxs-lookup"><span data-stu-id="84f62-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="84f62-108">値が `Nothing` である参照変数を読み取ると、状況によって <xref:System.NullReferenceException> が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84f62-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="84f62-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="84f62-109">By default, this message is a warning.</span></span> <span data-ttu-id="84f62-110">警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="84f62-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="84f62-111">**エラー ID:** bc42104 を生成します</span><span class="sxs-lookup"><span data-stu-id="84f62-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84f62-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="84f62-112">To correct this error</span></span>  
  
-   <span data-ttu-id="84f62-113">制御フローのロジックを確認し、によって読み取られる任意のステートメントに制御が渡される前に、変数が有効な値を持つかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="84f62-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="84f62-114">変数が常に有効な値を持つことを保証するために 1 つの方法では、その宣言の一部として初期化します。</span><span class="sxs-lookup"><span data-stu-id="84f62-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="84f62-115">「初期化」を参照してください[Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="84f62-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f62-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="84f62-116">See Also</span></span>  
 [<span data-ttu-id="84f62-117">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="84f62-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="84f62-118">変数宣言</span><span class="sxs-lookup"><span data-stu-id="84f62-118">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="84f62-119">変数のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="84f62-119">Troubleshooting Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
