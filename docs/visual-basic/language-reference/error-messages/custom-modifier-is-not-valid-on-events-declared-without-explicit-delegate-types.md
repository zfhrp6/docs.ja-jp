---
title: "&#39;です。カスタム &#39;修飾子は無効です。 明示的なデリゲート型なしで宣言されたイベント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords: BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 844bd033ea05e373b04a04f80777af77179c1263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="fba50-102">&#39;です。カスタム &#39;修飾子は無効です。 明示的なデリゲート型なしで宣言されたイベント</span><span class="sxs-lookup"><span data-stu-id="fba50-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="fba50-103">非カスタム イベントとは異なり、`Custom Event`宣言が必要です、`As`句が次のイベントの名前を明示的にイベントのデリゲート型を指定します。</span><span class="sxs-lookup"><span data-stu-id="fba50-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="fba50-104">非カスタム イベントを指定できますいずれかで定義されている、`As`句と、明示的なデリゲート型、またはすぐにパラメーターを持つリスト次のイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="fba50-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="fba50-105">**エラー ID:** BC31122</span><span class="sxs-lookup"><span data-stu-id="fba50-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fba50-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="fba50-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="fba50-107">カスタム イベントとして同じパラメーター リストを持つデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="fba50-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="fba50-108">たとえば場合、`Custom Event`によって定義された`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`を対応するデリゲートは、次です。</span><span class="sxs-lookup"><span data-stu-id="fba50-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  <span data-ttu-id="fba50-109">カスタム イベントのパラメーター一覧の置換、`As`句のデリゲート型を指定します。</span><span class="sxs-lookup"><span data-stu-id="fba50-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="fba50-110">この例では、`Custom Event`宣言を次のように書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="fba50-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="fba50-111">例</span><span class="sxs-lookup"><span data-stu-id="fba50-111">Example</span></span>  
 <span data-ttu-id="fba50-112">この例で宣言、`Custom Event`し、必要な指定`As`デリゲート型を含む句。</span><span class="sxs-lookup"><span data-stu-id="fba50-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fba50-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="fba50-113">See Also</span></span>  
 [<span data-ttu-id="fba50-114">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="fba50-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="fba50-115">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="fba50-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="fba50-116">イベント</span><span class="sxs-lookup"><span data-stu-id="fba50-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
