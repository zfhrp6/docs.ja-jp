---
title: "その他のデータ型 (Visual Basic) |Microsoft ドキュメント"
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
- Object data type, data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
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
ms.openlocfilehash: ed7b61a5ec57ff85347f2c257e321ab9ec425274
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="156fb-102">その他のデータ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="156fb-102">Miscellaneous Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="156fb-103">数値や文字を対象としていない複数のデータ型を提供します。</span><span class="sxs-lookup"><span data-stu-id="156fb-103"> supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="156fb-104">代わりになどを扱う特殊なデータはい/いいえ値、日付/時刻値、およびオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="156fb-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="156fb-105">サイド バイ サイドの比較を示す表に、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データ型を参照してください[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)します。</span><span class="sxs-lookup"><span data-stu-id="156fb-105">For a table showing a side-by-side comparison of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="156fb-106">ブール型</span><span class="sxs-lookup"><span data-stu-id="156fb-106">Boolean Type</span></span>  
 <span data-ttu-id="156fb-107">[ブール データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)いずれかとして解釈される符号なしの値は、`True`または`False`です。</span><span class="sxs-lookup"><span data-stu-id="156fb-107">The [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="156fb-108">データのサイズは実装されているプラットフォームに依存します。</span><span class="sxs-lookup"><span data-stu-id="156fb-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="156fb-109">変数は、はい/いいえ、またはオン/オフ、true または false などの&2; つの状態値のみを含めることができます、宣言として`Boolean`します。</span><span class="sxs-lookup"><span data-stu-id="156fb-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="156fb-110">Date 型</span><span class="sxs-lookup"><span data-stu-id="156fb-110">Date Type</span></span>  
 <span data-ttu-id="156fb-111">[Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)日付と時刻の両方の情報を保持する 64 ビット値です。</span><span class="sxs-lookup"><span data-stu-id="156fb-111">The [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="156fb-112">増分では、グレゴリオ暦の年 1 月 1 (12時 00分 AM) 開始時からの経過時間の 100 ナノ秒を表します。</span><span class="sxs-lookup"><span data-stu-id="156fb-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="156fb-113">変数には、日付値、時間の値、またはその両方を含めることができます、宣言として`Date`します。</span><span class="sxs-lookup"><span data-stu-id="156fb-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="156fb-114">オブジェクトの種類</span><span class="sxs-lookup"><span data-stu-id="156fb-114">Object Type</span></span>  
 <span data-ttu-id="156fb-115">[Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)またはその他のアプリケーションで、アプリケーション内でオブジェクトのインスタンスを指す 32 ビット アドレスです。</span><span class="sxs-lookup"><span data-stu-id="156fb-115">The [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="156fb-116">`Object`変数は、アプリケーションが認識されると、任意のオブジェクトまたは任意のデータ型のデータを参照できます。</span><span class="sxs-lookup"><span data-stu-id="156fb-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="156fb-117">両方が含まれます*値の型*など`Integer`、 `Boolean`、および構造体のインスタンスと*型を参照*であるなどのクラスから作成されたオブジェクトのインスタンスである`String`と<xref:System.Windows.Forms.Form>、インスタンスの配列</xref:System.Windows.Forms.Form>。</span><span class="sxs-lookup"><span data-stu-id="156fb-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="156fb-118">変数は、コンパイル時に不明なクラスのインスタンスへのポインターを格納するさまざまなデータ型のデータをポイントできる場合や、宣言として`Object`します。</span><span class="sxs-lookup"><span data-stu-id="156fb-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="156fb-119">利点、`Object`データ型は、任意のデータ型のデータの格納に使用ことができます。</span><span class="sxs-lookup"><span data-stu-id="156fb-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="156fb-120">デメリットは、実行に時間がかかると、アプリケーションの実行が遅くなる余分な処理を発生することです。</span><span class="sxs-lookup"><span data-stu-id="156fb-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="156fb-121">使用する場合、`Object`発生する値型の変数、*ボックス化*と*ボックス化解除*します。</span><span class="sxs-lookup"><span data-stu-id="156fb-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="156fb-122">参照型を使用する場合に発生する*遅延バインディング*します。</span><span class="sxs-lookup"><span data-stu-id="156fb-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156fb-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="156fb-123">See Also</span></span>  
 <span data-ttu-id="156fb-124">[型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span><span class="sxs-lookup"><span data-stu-id="156fb-124">[Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span></span>  
<span data-ttu-id="156fb-125"> [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="156fb-125"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="156fb-126"> [数値データ型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="156fb-126"> [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span></span>  
<span data-ttu-id="156fb-127"> [文字データ型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="156fb-127"> [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span></span>  
<span data-ttu-id="156fb-128"> [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="156fb-128"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="156fb-129"> [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span><span class="sxs-lookup"><span data-stu-id="156fb-129"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span></span>
