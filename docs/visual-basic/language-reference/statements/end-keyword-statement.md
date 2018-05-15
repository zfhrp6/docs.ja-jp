---
title: 終了&lt;キーワード&gt;ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 8137434bfd8c26144d78b1761b784cdba4894eaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a><span data-ttu-id="ca98c-102">終了&lt;キーワード&gt;ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca98c-102">End &lt;keyword&gt; Statement (Visual Basic)</span></span>
<span data-ttu-id="ca98c-103">その他のキーワードの後に、そのキーワードによって導入されるステートメント ブロックの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="ca98c-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca98c-104">構文</span><span class="sxs-lookup"><span data-stu-id="ca98c-104">Syntax</span></span>  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="ca98c-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="ca98c-105">Parts</span></span>  
 `End`  
 <span data-ttu-id="ca98c-106">必須。</span><span class="sxs-lookup"><span data-stu-id="ca98c-106">Required.</span></span> <span data-ttu-id="ca98c-107">プログラミング要素の定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="ca98c-107">Terminates the definition of the programming element.</span></span>  
  
 `AddHandler`  
 <span data-ttu-id="ca98c-108">終了するために必要な`AddHandler`、対応する開始アクセサー`AddHandler`カスタム ステートメント[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-108">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Class`  
 <span data-ttu-id="ca98c-109">クラスの定義を対応する終了を終了するために必要な[クラス ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-109">Required to terminate a class definition begun by a matching [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
 `Enum`  
 <span data-ttu-id="ca98c-110">対応する開始列挙の定義を終了するために必要な[Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-110">Required to terminate an enumeration definition begun by a matching [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
 `Event`  
 <span data-ttu-id="ca98c-111">終了するために必要な`Custom`イベントの定義を対応する終了[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-111">Required to terminate a `Custom` event definition begun by a matching [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Function`  
 <span data-ttu-id="ca98c-112">終了するために必要な`Function`プロシージャの定義が、対応する開始[関数ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-112">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="ca98c-113">実行されると、`End``Function`ステートメントでは、呼び出し元のコードに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="ca98c-113">If execution encounters an `End``Function` statement, control returns to the calling code.</span></span>  
  
 `Get`  
 <span data-ttu-id="ca98c-114">終了するために必要な`Property`プロシージャの定義が、対応する開始[Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-114">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md).</span></span> <span data-ttu-id="ca98c-115">実行されると、`End``Get`ステートメントでは、プロパティの値を要求したステートメントに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="ca98c-115">If execution encounters an `End``Get` statement, control returns to the statement requesting the property's value.</span></span>  
  
 `If`  
 <span data-ttu-id="ca98c-116">終了するために必要な`If`しています.`Then`...`Else`ブロック定義が、対応する開始`If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ca98c-116">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="ca98c-117">参照してください[場合.そうしたら...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-117">See [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span>  
  
 `Interface`  
 <span data-ttu-id="ca98c-118">開始されて、対応するインターフェイス定義を終了するために必要な[インターフェイス ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-118">Required to terminate an interface definition begun by a matching [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md).</span></span>  
  
 `Module`  
 <span data-ttu-id="ca98c-119">開始されて、対応するモジュールの定義を終了するために必要な[モジュール ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-119">Required to terminate a module definition begun by a matching [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
 `Namespace`  
 <span data-ttu-id="ca98c-120">開始されて、対応する名前空間の定義を終了するために必要な[Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-120">Required to terminate a namespace definition begun by a matching [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span>  
  
 `Operator`  
 <span data-ttu-id="ca98c-121">開始されて、対応する演算子の定義を終了するために必要な[Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-121">Required to terminate an operator definition begun by a matching [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 `Property`  
 <span data-ttu-id="ca98c-122">開始されて、対応するプロパティの定義を終了するために必要な[Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-122">Required to terminate a property definition begun by a matching [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
 `RaiseEvent`  
 <span data-ttu-id="ca98c-123">終了するために必要な`RaiseEvent`、対応する開始アクセサー`RaiseEvent`カスタム ステートメント[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-123">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `RemoveHandler`  
 <span data-ttu-id="ca98c-124">終了するために必要な`RemoveHandler`、対応する開始アクセサー`RemoveHandler`カスタム ステートメント[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-124">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Select`  
 <span data-ttu-id="ca98c-125">終了するために必要な`Select`しています.`Case`ブロック定義が、対応する開始`Select`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ca98c-125">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="ca98c-126">参照してください[を選択しています.ステートメントの case](../../../visual-basic/language-reference/statements/select-case-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-126">See [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
 `Set`  
 <span data-ttu-id="ca98c-127">終了するために必要な`Property`プロシージャの定義が、対応する開始[Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-127">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md).</span></span> <span data-ttu-id="ca98c-128">実行されると、`End``Set`ステートメントでは、プロパティの値を設定するステートメントに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="ca98c-128">If execution encounters an `End``Set` statement, control returns to the statement setting the property's value.</span></span>  
  
 `Structure`  
 <span data-ttu-id="ca98c-129">開始されて、対応する構造体の定義を終了するために必要な[Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-129">Required to terminate a structure definition begun by a matching [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
 `Sub`  
 <span data-ttu-id="ca98c-130">終了するために必要な`Sub`プロシージャの定義が、対応する開始[Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-130">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span> <span data-ttu-id="ca98c-131">実行されると、`End``Sub`ステートメントでは、呼び出し元のコードに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="ca98c-131">If execution encounters an `End``Sub` statement, control returns to the calling code.</span></span>  
  
 `SyncLock`  
 <span data-ttu-id="ca98c-132">終了するために必要な`SyncLock`ブロック定義が、対応する開始`SyncLock`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ca98c-132">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="ca98c-133">参照してください[SyncLock ステートメント](../../../visual-basic/language-reference/statements/synclock-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-133">See [SyncLock Statement](../../../visual-basic/language-reference/statements/synclock-statement.md).</span></span>  
  
 `Try`  
 <span data-ttu-id="ca98c-134">終了するために必要な`Try`しています.`Catch`...`Finally`ブロック定義が、対応する開始`Try`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ca98c-134">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="ca98c-135">参照してください[を再試行してください.キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-135">See [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 `While`  
 <span data-ttu-id="ca98c-136">終了するために必要な`While`ループの定義を対応する終了`While`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ca98c-136">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="ca98c-137">参照してください[中.While ステートメント終了](../../../visual-basic/language-reference/statements/while-end-while-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-137">See [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
 `With`  
 <span data-ttu-id="ca98c-138">終了するために必要な`With`ブロック定義が、対応する開始`With`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ca98c-138">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="ca98c-139">参照してください[としています.ステートメントで終了して](../../../visual-basic/language-reference/statements/with-end-with-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-139">See [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca98c-140">コメント</span><span class="sxs-lookup"><span data-stu-id="ca98c-140">Remarks</span></span>  
 <span data-ttu-id="ca98c-141">[End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)、追加のキーワードをせずにすぐに実行を終了します。</span><span class="sxs-lookup"><span data-stu-id="ca98c-141">The [End Statement](../../../visual-basic/language-reference/statements/end-statement.md), without an additional keyword, terminates execution immediately.</span></span>  
  
 <span data-ttu-id="ca98c-142">番号記号に続く場合 (`#`) では、`End`キーワードが、対応するディレクティブによって導入されるプリプロセッサのブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="ca98c-142">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  
  
 `#End`  
 <span data-ttu-id="ca98c-143">必須。</span><span class="sxs-lookup"><span data-stu-id="ca98c-143">Required.</span></span> <span data-ttu-id="ca98c-144">処理前のブロックの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="ca98c-144">Terminates the definition of the preprocessing block.</span></span>  
  
 `#ExternalSource`  
 <span data-ttu-id="ca98c-145">開始されて、対応する外部のソース ブロックを終了するために必要な[#ExternalSource ディレクティブ](../../../visual-basic/language-reference/directives/externalsource-directive.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-145">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span></span>  
  
 `#If`  
 <span data-ttu-id="ca98c-146">対応する開始条件付きコンパイル ブロックを終了するために必要な`#If`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="ca98c-146">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="ca98c-147">参照してください[#If しています.Then... #Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-147">See [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span></span>  
  
 `#Region`  
 <span data-ttu-id="ca98c-148">開始されて、対応するソース領域ブロックを終了するために必要な[#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca98c-148">Required to terminate a source region block begun by a matching [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md).</span></span>  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="ca98c-149">スマート デバイスの開発者向け注意事項</span><span class="sxs-lookup"><span data-stu-id="ca98c-149">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="ca98c-150">`End`その他のキーワードを使用せず、ステートメントはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ca98c-150">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca98c-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca98c-151">See Also</span></span>  
 [<span data-ttu-id="ca98c-152">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="ca98c-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
