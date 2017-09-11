---
title: "(Visual Basic) 列挙型を使用する |Microsoft ドキュメント"
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
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
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
ms.openlocfilehash: 3853950382fd4336c569f9d772aea3c1312f2ebc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="b6f1e-102">列挙型を使用する状況 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6f1e-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="b6f1e-103">列挙体は、関連する定数のセットを操作する簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="b6f1e-104">列挙をまたは`Enum`一連の値のシンボルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="b6f1e-105">列挙体は、データ型として扱われ、それらを使用して、変数やプロパティを使用する定数のセットを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="b6f1e-106">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="b6f1e-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="b6f1e-107">プロシージャが、限られた一連の変数を受け取ったときは、列挙体の使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="b6f1e-108">列挙体は、わかりやすい名前を使用する場合に特にわかりやすく読みやすいコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="b6f1e-109">列挙体を使用する利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="b6f1e-110">置き換えや数値の入力ミスによって発生したエラーを削減します。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="b6f1e-111">値は、将来変更を簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="b6f1e-112">簡単に理解がそこにエラーが生じる可能性がある可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="b6f1e-113">上位互換性を確認します。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-113">Ensures forward compatibility.</span></span> <span data-ttu-id="b6f1e-114">列挙型をコードは、メンバーの名前に対応する値が変更された後で、エラーが発生する可能性は低くです。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="b6f1e-115">列挙体の名前を付ける</span><span class="sxs-lookup"><span data-stu-id="b6f1e-115">Naming Enumerations</span></span>  
 <span data-ttu-id="b6f1e-116">列挙型メンバーの名前付け規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="b6f1e-117">ときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]列挙メンバー名の場合は、発生したその他の参照されるタイプ ライブラリには、同じ名前が含まれている場合、例外がスローされる可能性ができます。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-117">When [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="b6f1e-118">アプリケーションまたはコンポーネントから値を識別する一意のプレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="b6f1e-119">列挙体のメンバーの場合は、する必要があります列挙型の名前でメンバー名を修飾するかを使用して、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="b6f1e-120">詳細については、次を参照してください。[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)します。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="b6f1e-121">定義済み列挙型</span><span class="sxs-lookup"><span data-stu-id="b6f1e-121">Predefined Enumerations</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="b6f1e-122">などの定義済みの列挙値の数が表示`FirstDayOfWeek`と`MsgBoxResul`t、コードを容易にします。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-122"> provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResul`t, to facilitate your code.</span></span> <span data-ttu-id="b6f1e-123">これらの一覧を参照してください。[定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)します。</span><span class="sxs-lookup"><span data-stu-id="b6f1e-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f1e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6f1e-124">See Also</span></span>  
 <span data-ttu-id="b6f1e-125">[方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="b6f1e-125">[How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="b6f1e-126"> [方法: 列挙型のメンバーを参照してください](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="b6f1e-126"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="b6f1e-127"> [列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="b6f1e-127"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="b6f1e-128"> [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="b6f1e-128"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="b6f1e-129"> [方法: 列挙値に関連付けられている文字列を確認します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="b6f1e-129"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="b6f1e-130"> [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b6f1e-130"> [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md) </span></span>  
<span data-ttu-id="b6f1e-131"> [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="b6f1e-131"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
