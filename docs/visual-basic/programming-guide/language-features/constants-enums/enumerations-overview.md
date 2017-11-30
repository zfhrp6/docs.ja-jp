---
title: "列挙型の概要 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, enumerations
- enumerations [Visual Basic], about enumerations
ms.assetid: b42a38ee-5e77-4f99-a037-e3a127ead89c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d50e6bae880e5dc4dcde203708c6b07c05bb4e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="enumerations-overview-visual-basic"></a><span data-ttu-id="dc68f-102">列挙型の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc68f-102">Enumerations Overview (Visual Basic)</span></span>
<span data-ttu-id="dc68f-103">列挙体は、関連する定数のセットを使用して、定数値の名前に関連付ける便利な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="dc68f-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="dc68f-104">たとえば、一連の整数型の定数を曜日に関連付けて列挙型として宣言すると、コードで整数値ではなく曜日名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="dc68f-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="tasks-involving-enumerations"></a><span data-ttu-id="dc68f-105">列挙体に関連するタスク</span><span class="sxs-lookup"><span data-stu-id="dc68f-105">Tasks involving Enumerations</span></span>  
 <span data-ttu-id="dc68f-106">次の表は、列挙型に関する一般的なタスクを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="dc68f-106">The following table lists common tasks involving enumerations.</span></span>  
  
|<span data-ttu-id="dc68f-107">目的</span><span class="sxs-lookup"><span data-stu-id="dc68f-107">To do this</span></span>|<span data-ttu-id="dc68f-108">参照トピック</span><span class="sxs-lookup"><span data-stu-id="dc68f-108">See</span></span>|  
|----------------|---------|  
|<span data-ttu-id="dc68f-109">事前に定義された列挙型を検索します。</span><span class="sxs-lookup"><span data-stu-id="dc68f-109">Find a pre-defined enumeration</span></span>|[<span data-ttu-id="dc68f-110">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="dc68f-110">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|  
|<span data-ttu-id="dc68f-111">列挙体を宣言します。</span><span class="sxs-lookup"><span data-stu-id="dc68f-111">Declare an enumeration</span></span>|[<span data-ttu-id="dc68f-112">方法: 列挙型を宣言</span><span class="sxs-lookup"><span data-stu-id="dc68f-112">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)|  
|<span data-ttu-id="dc68f-113">列挙型の名前を完全に修飾します。</span><span class="sxs-lookup"><span data-stu-id="dc68f-113">Fully qualify an enumeration's name</span></span>|[<span data-ttu-id="dc68f-114">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="dc68f-114">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)|  
|<span data-ttu-id="dc68f-115">列挙体のメンバーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc68f-115">Refer to an enumeration member</span></span>|[<span data-ttu-id="dc68f-116">方法 : 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="dc68f-116">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)|  
|<span data-ttu-id="dc68f-117">列挙体を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="dc68f-117">Iterate through an enumeration</span></span>|[<span data-ttu-id="dc68f-118">方法: Visual Basic で列挙型を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="dc68f-118">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)|  
|<span data-ttu-id="dc68f-119">列挙体に関連付けられている文字列を確認します。</span><span class="sxs-lookup"><span data-stu-id="dc68f-119">Determine the string associated with an enumeration</span></span>|[<span data-ttu-id="dc68f-120">方法 : 列挙値に関連付けられている文字列を確認する</span><span class="sxs-lookup"><span data-stu-id="dc68f-120">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)|  
|<span data-ttu-id="dc68f-121">列挙体を使用する状況します。</span><span class="sxs-lookup"><span data-stu-id="dc68f-121">Decide when to use an enumeration</span></span>|[<span data-ttu-id="dc68f-122">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="dc68f-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)|  
  
## <a name="see-also"></a><span data-ttu-id="dc68f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc68f-123">See Also</span></span>  
 [<span data-ttu-id="dc68f-124">定数の概要</span><span class="sxs-lookup"><span data-stu-id="dc68f-124">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="dc68f-125">ユーザー定義定数</span><span class="sxs-lookup"><span data-stu-id="dc68f-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [<span data-ttu-id="dc68f-126">方法 : 定数を宣言する</span><span class="sxs-lookup"><span data-stu-id="dc68f-126">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [<span data-ttu-id="dc68f-127">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="dc68f-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="dc68f-128">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="dc68f-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
