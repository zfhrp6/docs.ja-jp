---
title: "Visual Basic の定数と列挙体"
ms.custom: 
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
- enumerations [Visual Basic]
- Visual Basic code, constants
- constants
- object libraries, Object Browser
- Visual Basic code, enumerations
- declaring constants, enumerations
- naming conventions, constants
- Visual Basic code, improving readability with constants
ms.assetid: c8aba36e-fa47-4a33-8b68-cb2009218270
caps.latest.revision: 16
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5ef8ade1100bb660af4d968d4b600aba41073fc2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="5c720-102">Visual Basic の定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="5c720-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="5c720-103">定数は、変化しない値の代わりにわかりやすい名前を使用するための方法です。</span><span class="sxs-lookup"><span data-stu-id="5c720-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="5c720-104">定数に格納された値は、その名が示すとおり、アプリケーションの実行中に変わることはありません。</span><span class="sxs-lookup"><span data-stu-id="5c720-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="5c720-105">定数を使用すると、数値の代わりにわかりやすい名前を指定できるので、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="5c720-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="5c720-106">一連の関連する定数を操作する場合や、定数値に名前を関連付ける場合は、列挙型を使うと便利です。</span><span class="sxs-lookup"><span data-stu-id="5c720-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="5c720-107">たとえば、一連の整数型の定数を曜日に関連付けて列挙型として宣言すると、コードで整数値ではなく曜日名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5c720-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c720-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5c720-108">In This Section</span></span>  
  
|<span data-ttu-id="5c720-109">用語</span><span class="sxs-lookup"><span data-stu-id="5c720-109">Term</span></span>|<span data-ttu-id="5c720-110">定義</span><span class="sxs-lookup"><span data-stu-id="5c720-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="5c720-111">定数の概要</span><span class="sxs-lookup"><span data-stu-id="5c720-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="5c720-112">このセクションのトピックでは定数とその使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c720-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="5c720-113">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="5c720-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="5c720-114">このセクションのトピックでは列挙型とその使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c720-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="5c720-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c720-115">Related Sections</span></span>  
  
|<span data-ttu-id="5c720-116">用語</span><span class="sxs-lookup"><span data-stu-id="5c720-116">Term</span></span>|<span data-ttu-id="5c720-117">定義</span><span class="sxs-lookup"><span data-stu-id="5c720-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="5c720-118">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="5c720-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="5c720-119">整数の宣言に使用される、`Const` ステートメントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5c720-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="5c720-120">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="5c720-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="5c720-121">列挙型の作成に使用される、`Enum` ステートメントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5c720-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="5c720-122">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="5c720-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="5c720-123">`Option Explicit` ステートメントについて説明します。このステートメントはモジュール レベルで使用され、そのモジュール内のすべての変数の明示的な宣言を強制します。</span><span class="sxs-lookup"><span data-stu-id="5c720-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="5c720-124">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="5c720-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="5c720-125">`Option Infer` ステートメントについて説明します。このステートメントは、変数の宣言でローカル型推論を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5c720-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="5c720-126">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="5c720-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="5c720-127">`Object` ステートメントについて説明します。このステートメントは、暗黙的なデータ型変換を拡大変換のみに制限し、遅延バインディングを許可せず、`Option Strict` 型になる暗黙的な型指定も許可しません。</span><span class="sxs-lookup"><span data-stu-id="5c720-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|

