---
title: "&quot;Custom&quot; 修飾子は、明示的なデリゲート型なしで宣言されたイベントに対して無効な |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
dev_langs:
- VB
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
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
ms.openlocfilehash: 449e5a690f06ce35d1ccc799daf5f2c1ad1c6dac
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="a6fb0-102">'Custom' 修飾子は、明示的なデリゲート型なしで宣言されたイベントでは無効</span><span class="sxs-lookup"><span data-stu-id="a6fb0-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="a6fb0-103">非カスタム イベントとは異なり、`Custom Event`宣言が必要ですが`As`句を次に示す、イベントのデリゲート型を明示的に指定するイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="a6fb0-104">非カスタム イベントは、いずれかで定義されている、`As`句と明示的なデリゲート型、またはすぐにパラメーターを持つリスト イベント名の後です。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="a6fb0-105">**エラー ID:** BC31122</span><span class="sxs-lookup"><span data-stu-id="a6fb0-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a6fb0-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a6fb0-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a6fb0-107">カスタム イベントと同じパラメーター リストを持つデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="a6fb0-108">たとえば場合、`Custom Event`で定義された`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`、対応するデリゲートは、次です。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     <span data-ttu-id="a6fb0-109">[!code-vb[VbVbalrEventError&#18;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a6fb0-109">[!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]</span></span>  
  
2.  <span data-ttu-id="a6fb0-110">カスタム イベントとのパラメーターのリストを置き換える、`As`デリゲート型を指定する句。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-110">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="a6fb0-111">先ほどの例では、`Custom Event`宣言を次のように書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-111">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     <span data-ttu-id="a6fb0-112">[!code-vb[VbVbalrEventError&#19;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a6fb0-112">[!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6fb0-113">例</span><span class="sxs-lookup"><span data-stu-id="a6fb0-113">Example</span></span>  
 <span data-ttu-id="a6fb0-114">この例で宣言、`Custom Event`し、必要な指定`As`デリゲート型を含む句。</span><span class="sxs-lookup"><span data-stu-id="a6fb0-114">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 <span data-ttu-id="a6fb0-115">[!code-vb[VbVbalrEventError&#2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a6fb0-115">[!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fb0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6fb0-116">See Also</span></span>  
 <span data-ttu-id="a6fb0-117">[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a6fb0-117">[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="a6fb0-118"> [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a6fb0-118"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="a6fb0-119"> [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="a6fb0-119"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
