---
title: "その他のデータ型 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6bb86bb6d203aa4e6bdded27a4cb78a8155ddec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="1ec06-102">その他のデータ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ec06-102">Miscellaneous Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="1ec06-103">数字や文字を対象とされているいくつかのデータ型を提供します。</span><span class="sxs-lookup"><span data-stu-id="1ec06-103"> supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="1ec06-104">代わりが扱う特化されたデータなど、はい/いいえ値、日付/時刻値、およびオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="1ec06-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="1ec06-105">サイド バイ サイドの比較を示す表に、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]データ型を参照してください[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ec06-105">For a table showing a side-by-side comparison of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="1ec06-106">ブール型</span><span class="sxs-lookup"><span data-stu-id="1ec06-106">Boolean Type</span></span>  
 <span data-ttu-id="1ec06-107">[ブールのデータ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)いずれかとして解釈される符号なしの値は、`True`または`False`です。</span><span class="sxs-lookup"><span data-stu-id="1ec06-107">The [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="1ec06-108">データのサイズは実装されているプラットフォームに依存します。</span><span class="sxs-lookup"><span data-stu-id="1ec06-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="1ec06-109">場合は、変数は、はい/いいえ、またはオン/オフ、true または false などの 2 つの状態値のみを含めることができます、宣言として`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="1ec06-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="1ec06-110">日付型</span><span class="sxs-lookup"><span data-stu-id="1ec06-110">Date Type</span></span>  
 <span data-ttu-id="1ec06-111">[Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)日付と時刻の両方の情報を保持する 64 ビット値です。</span><span class="sxs-lookup"><span data-stu-id="1ec06-111">The [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="1ec06-112">各インクリメントは、グレゴリオ暦カレンダーにおける年 1 月 1 (12時 00分 AM) の開始以降の経過時間を 100 ナノ秒を表します。</span><span class="sxs-lookup"><span data-stu-id="1ec06-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="1ec06-113">場合は、変数には、日付の値、時間の値、またはその両方を含めることができます、宣言として`Date`です。</span><span class="sxs-lookup"><span data-stu-id="1ec06-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="1ec06-114">オブジェクトの種類</span><span class="sxs-lookup"><span data-stu-id="1ec06-114">Object Type</span></span>  
 <span data-ttu-id="1ec06-115">[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)アプリケーション内で、またはその他のアプリケーションでのオブジェクト インスタンスを指す 32 ビット アドレスです。</span><span class="sxs-lookup"><span data-stu-id="1ec06-115">The [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="1ec06-116">`Object`変数は、アプリケーションが認識されると、任意のオブジェクトや任意のデータ型のデータに参照できます。</span><span class="sxs-lookup"><span data-stu-id="1ec06-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="1ec06-117">両方が含まれます*値の型*など`Integer`、 `Boolean`、および構造体のインスタンスと*型参照*、オブジェクトなどのクラスから作成されたのインスタンスは`String`と<xref:System.Windows.Forms.Form>のインスタンスの配列。</span><span class="sxs-lookup"><span data-stu-id="1ec06-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="1ec06-118">変数が分かっていなければ、コンパイル時に、クラスのインスタンスへのポインターを格納するさまざまなデータ型のデータを指すことができる場合や、として宣言`Object`です。</span><span class="sxs-lookup"><span data-stu-id="1ec06-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="1ec06-119">利点、`Object`データ型が使用できる、任意のデータ型のデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="1ec06-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="1ec06-120">欠点は、実行時間がかかるし、アプリケーションの実行速度が遅くする余分な処理が発生することです。</span><span class="sxs-lookup"><span data-stu-id="1ec06-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="1ec06-121">使用する場合、`Object`発生する値の型の変数、*ボックス化*と*アンボックス*です。</span><span class="sxs-lookup"><span data-stu-id="1ec06-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="1ec06-122">で参照型を使用する場合に発生する*遅延バインディング*です。</span><span class="sxs-lookup"><span data-stu-id="1ec06-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec06-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ec06-123">See Also</span></span>  
 [<span data-ttu-id="1ec06-124">型文字</span><span class="sxs-lookup"><span data-stu-id="1ec06-124">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="1ec06-125">基本データ型</span><span class="sxs-lookup"><span data-stu-id="1ec06-125">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="1ec06-126">数値のデータ型</span><span class="sxs-lookup"><span data-stu-id="1ec06-126">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [<span data-ttu-id="1ec06-127">文字データ型</span><span class="sxs-lookup"><span data-stu-id="1ec06-127">Character Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [<span data-ttu-id="1ec06-128">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="1ec06-128">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="1ec06-129">事前バインディングと遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="1ec06-129">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
