---
title: "Visual Basic における制御フロー"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control flow [Visual Basic]
- control structures [Visual Basic]
- structures [Visual Basic], control
- conditional statements [Visual Basic], control flow
ms.assetid: 5623ef47-52b1-4202-befd-9af36422ec6f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce0cb7cba8f05b488d47f99da51b0b5de75eb15
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="control-flow-in-visual-basic"></a><span data-ttu-id="9e267-102">Visual Basic における制御フロー</span><span class="sxs-lookup"><span data-stu-id="9e267-102">Control Flow in Visual Basic</span></span>
<span data-ttu-id="9e267-103">制御されていないままの場合、プログラムは最初から最後までそのステートメントを使って続行されます。</span><span class="sxs-lookup"><span data-stu-id="9e267-103">Left unregulated, a program proceeds through its statements from beginning to end.</span></span> <span data-ttu-id="9e267-104">この 1 方向のフローのみを使用して、いくつかの単純なプログラムを記述できます。</span><span class="sxs-lookup"><span data-stu-id="9e267-104">Some very simple programs can be written with only this unidirectional flow.</span></span> <span data-ttu-id="9e267-105">ただし、任意のプログラミング言語の能力とユーティリティのほとんどは、制御ステートメントとループで実行する順番を変更する機能からのものです。</span><span class="sxs-lookup"><span data-stu-id="9e267-105">However, much of the power and utility of any programming language comes from the ability to change execution order with control statements and loops.</span></span>  
  
 <span data-ttu-id="9e267-106">制御構造を使用すると、プログラムの実行フローを制御できます。</span><span class="sxs-lookup"><span data-stu-id="9e267-106">Control structures allow you to regulate the flow of your program's execution.</span></span> <span data-ttu-id="9e267-107">制御構造を使用して、判断したり、アクションを繰り返したりする [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] のコードを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="9e267-107">Using control structures, you can write [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code that makes decisions or that repeats actions.</span></span> <span data-ttu-id="9e267-108">他の制御構造を使用して、リソースの破棄を保証したり、同じオブジェクト参照で一連のステートメントを実行したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="9e267-108">Other control structures let you guarantee disposal of a resource or run a series of statements on the same object reference.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e267-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9e267-109">In This Section</span></span>  
 [<span data-ttu-id="9e267-110">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="9e267-110">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 <span data-ttu-id="9e267-111">分岐に使用する制御構造を説明します。</span><span class="sxs-lookup"><span data-stu-id="9e267-111">Describes control structures used for branching.</span></span>  
  
 [<span data-ttu-id="9e267-112">ループ構造</span><span class="sxs-lookup"><span data-stu-id="9e267-112">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 <span data-ttu-id="9e267-113">プロセスを繰り返すために使用する制御構造を説明します。</span><span class="sxs-lookup"><span data-stu-id="9e267-113">Discusses control structures used to repeat processes.</span></span>  
  
 [<span data-ttu-id="9e267-114">その他の制御構造</span><span class="sxs-lookup"><span data-stu-id="9e267-114">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 <span data-ttu-id="9e267-115">リソースの破棄とオブジェクトのアクセスに使用される制御構造を説明します。</span><span class="sxs-lookup"><span data-stu-id="9e267-115">Describes control structures used for resource disposal and object access.</span></span>  
  
 [<span data-ttu-id="9e267-116">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="9e267-116">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 <span data-ttu-id="9e267-117">他の制御構造内に制御構造を含めます。</span><span class="sxs-lookup"><span data-stu-id="9e267-117">Covers control structures inside other control structures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9e267-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e267-118">Related Sections</span></span>  
 [<span data-ttu-id="9e267-119">制御フローの概要</span><span class="sxs-lookup"><span data-stu-id="9e267-119">Control Flow Summary</span></span>](../../../../visual-basic/language-reference/keywords/control-flow-summary.md)  
 <span data-ttu-id="9e267-120">この領域の言語リファレンス ページへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="9e267-120">Provides links to language reference pages on this subject.</span></span>
