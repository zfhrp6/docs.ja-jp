---
title: 列挙型を使用する状況 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ab152687f4f9e4ba6bd032ae7c1352f65af715f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="31222-102">列挙型を使用する状況 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31222-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="31222-103">列挙体は、関連する定数のセットを操作する簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="31222-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="31222-104">列挙をまたは`Enum`一連の値のシンボリック名を指定します。</span><span class="sxs-lookup"><span data-stu-id="31222-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="31222-105">列挙体は、データ型として扱われ、それらを使用して、変数とプロパティを使用する定数のセットを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="31222-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="31222-106">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="31222-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="31222-107">プロシージャが、限られた一連の変数を受け入れるときに、列挙体の使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="31222-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="31222-108">列挙体は、わかりやすい名前を使用する場合に特に明確でわかりやすくコードでは、ようにします。</span><span class="sxs-lookup"><span data-stu-id="31222-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="31222-109">列挙体を使用する利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="31222-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="31222-110">転置または番号の入力ミスによって発生したエラーが減少します。</span><span class="sxs-lookup"><span data-stu-id="31222-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="31222-111">将来の値を変更するのには便利です。</span><span class="sxs-lookup"><span data-stu-id="31222-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="31222-112">コードを読みやすくするので、そこにエラーが生じる可能性がある可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="31222-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="31222-113">前方の互換性を確保します。</span><span class="sxs-lookup"><span data-stu-id="31222-113">Ensures forward compatibility.</span></span> <span data-ttu-id="31222-114">列挙型をコードが後で、メンバー名に対応する値が変更された場合は失敗する可能性は低くします。</span><span class="sxs-lookup"><span data-stu-id="31222-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="31222-115">列挙体の名前を付ける</span><span class="sxs-lookup"><span data-stu-id="31222-115">Naming Enumerations</span></span>  
 <span data-ttu-id="31222-116">列挙型メンバーの名前付け規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="31222-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="31222-117">Visual Basic では、列挙メンバー名が検出されると、その他の参照先の型ライブラリには、同じ名前が含まれている場合に例外がスローする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="31222-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="31222-118">アプリケーションまたはコンポーネントから値を識別する一意のプレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="31222-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="31222-119">列挙体のメンバーの場合は、する必要があります列挙名でメンバー名を修飾するか、またはを使用して、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="31222-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="31222-120">詳細については、次を参照してください。[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)です。</span><span class="sxs-lookup"><span data-stu-id="31222-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="31222-121">事前定義された列挙型</span><span class="sxs-lookup"><span data-stu-id="31222-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="31222-122">Visual Basic などの事前定義された列挙体の数の提供`FirstDayOfWeek`と`MsgBoxResult`コードを容易にします。</span><span class="sxs-lookup"><span data-stu-id="31222-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="31222-123">これらの一覧については、次を参照してください。[定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)です。</span><span class="sxs-lookup"><span data-stu-id="31222-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31222-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="31222-124">See Also</span></span>  
 [<span data-ttu-id="31222-125">方法: 列挙型を宣言</span><span class="sxs-lookup"><span data-stu-id="31222-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="31222-126">方法 : 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="31222-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="31222-127">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="31222-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="31222-128">方法: Visual Basic で列挙型を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="31222-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="31222-129">方法 : 列挙値に関連付けられている文字列を確認する</span><span class="sxs-lookup"><span data-stu-id="31222-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="31222-130">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="31222-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="31222-131">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="31222-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
