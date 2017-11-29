---
title: "標準例外型の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 91cd9a03ad1acf61681ecfad0edb061802c4362c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="7173f-102">標準例外型の使用</span><span class="sxs-lookup"><span data-stu-id="7173f-102">Using Standard Exception Types</span></span>
<span data-ttu-id="7173f-103">このセクションでは、フレームワークとその使用方法の詳細によって提供される標準の例外について説明します。</span><span class="sxs-lookup"><span data-stu-id="7173f-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="7173f-104">一覧は完全ではではありません。</span><span class="sxs-lookup"><span data-stu-id="7173f-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="7173f-105">その他のフレームワークの例外の種類の使用率の .NET Framework リファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7173f-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="7173f-106">例外と SystemException</span><span class="sxs-lookup"><span data-stu-id="7173f-106">Exception and SystemException</span></span>  
 <span data-ttu-id="7173f-107">**X しないで**スロー<xref:System.Exception?displayProperty=nameWithType>または<xref:System.SystemException?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="7173f-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="7173f-108">**X しないで**キャッチ`System.Exception`または`System.SystemException`framework コードで再スローする場合を除き、します。</span><span class="sxs-lookup"><span data-stu-id="7173f-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="7173f-109">**避け x**キャッチ`System.Exception`または`System.SystemException`、トップレベルの例外ハンドラーでは可します。</span><span class="sxs-lookup"><span data-stu-id="7173f-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="7173f-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="7173f-110">ApplicationException</span></span>  
 <span data-ttu-id="7173f-111">**X しないで**スロー サービスまたはそれから派生<xref:System.ApplicationException>です。</span><span class="sxs-lookup"><span data-stu-id="7173f-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="7173f-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="7173f-112">InvalidOperationException</span></span>  
 <span data-ttu-id="7173f-113">**✓ しないで**スロー、<xref:System.InvalidOperationException>オブジェクトが不適切な状態である場合。</span><span class="sxs-lookup"><span data-stu-id="7173f-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="7173f-114">ArgumentException、ArgumentNullException、および ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="7173f-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="7173f-115">**✓ しないで**スロー<xref:System.ArgumentException>またはメンバーに無効な引数が渡された場合は、そのサブタイプのいずれか。</span><span class="sxs-lookup"><span data-stu-id="7173f-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="7173f-116">該当する場合は、最派生例外の種類を選びます。</span><span class="sxs-lookup"><span data-stu-id="7173f-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="7173f-117">**✓ しないで**設定、`ParamName`プロパティのサブクラスのいずれかをスローするときに`ArgumentException`です。</span><span class="sxs-lookup"><span data-stu-id="7173f-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="7173f-118">このプロパティは、例外がスローされる原因となったパラメーターの名前を表します。</span><span class="sxs-lookup"><span data-stu-id="7173f-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="7173f-119">コンス トラクター オーバー ロードのいずれかを使用して、プロパティを設定できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7173f-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="7173f-120">**✓ は**使用`value`プロパティ set アクセス操作子の暗黙的な値パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="7173f-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="7173f-121">NullReferenceException、IndexOutOfRangeException、および AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="7173f-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="7173f-122">**X しないで**明示的または暗黙的にスローする、api で公開されている呼び出し可能<xref:System.NullReferenceException>、 <xref:System.AccessViolationException>、または<xref:System.IndexOutOfRangeException>です。</span><span class="sxs-lookup"><span data-stu-id="7173f-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="7173f-123">これらの例外は予約されておりとほとんどの場合は、バグを示す場合に、実行エンジンによってスローされます。</span><span class="sxs-lookup"><span data-stu-id="7173f-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="7173f-124">引数に、これらの例外がスローされないようにチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="7173f-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="7173f-125">時間の経過と共に変わる可能性があるメソッドの実装の詳細を公開するこれらの例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="7173f-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="7173f-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="7173f-126">StackOverflowException</span></span>  
 <span data-ttu-id="7173f-127">**X しないで**を明示的にスロー<xref:System.StackOverflowException>です。</span><span class="sxs-lookup"><span data-stu-id="7173f-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="7173f-128">CLR によってのみ、例外が明示的にスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7173f-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="7173f-129">**X しないで**キャッチ`StackOverflowException`です。</span><span class="sxs-lookup"><span data-stu-id="7173f-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="7173f-130">ほとんどでは、一貫性のある任意のスタック オーバーフローが存在する場合に残っているマネージ コードを記述することはできません。</span><span class="sxs-lookup"><span data-stu-id="7173f-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="7173f-131">CLR のアンマネージ部分一貫して任意のスタック オーバーフローからバックアップではなくプローブを使用してスタックのオーバーフローを適切に定義された場所に移動するでします。</span><span class="sxs-lookup"><span data-stu-id="7173f-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="7173f-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="7173f-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="7173f-133">**X しないで**を明示的にスロー<xref:System.OutOfMemoryException>です。</span><span class="sxs-lookup"><span data-stu-id="7173f-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="7173f-134">この例外では、CLR インフラストラクチャによってのみスローされます。</span><span class="sxs-lookup"><span data-stu-id="7173f-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="7173f-135">ComException、SEHException、および ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="7173f-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="7173f-136">**X しないで**を明示的にスロー <xref:System.Runtime.InteropServices.COMException>、 <xref:System.ExecutionEngineException>、および<xref:System.Runtime.InteropServices.SEHException>です。</span><span class="sxs-lookup"><span data-stu-id="7173f-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="7173f-137">これらの例外では、CLR インフラストラクチャによってのみスローされます。</span><span class="sxs-lookup"><span data-stu-id="7173f-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="7173f-138">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="7173f-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7173f-139">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="7173f-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7173f-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="7173f-140">See Also</span></span>  
 [<span data-ttu-id="7173f-141">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="7173f-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="7173f-142">例外のデザイン ガイドライン</span><span class="sxs-lookup"><span data-stu-id="7173f-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
