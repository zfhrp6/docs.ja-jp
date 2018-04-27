---
title: '&#39;いずれかとして&#39;でサポートされていない&#39;Declare&#39;ステートメント'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d8146e339ac5cb005b99c9a1e02f1cd248c4558b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="0cf2d-102">&#39;いずれかとして&#39;でサポートされていない&#39;Declare&#39;ステートメント</span><span class="sxs-lookup"><span data-stu-id="0cf2d-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="0cf2d-103">`Any`データ型と共に使用されました`Declare`任意のデータ型を含む可能性のある引数の使用を許可するには、Visual Basic 6.0 とそれ以前のバージョン内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> <span data-ttu-id="0cf2d-104">オーバー ロード、ただし、Visual Basic サポートされため、`Any`古いデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-104">Visual Basic supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="0cf2d-105">**エラー ID:** BC30828</span><span class="sxs-lookup"><span data-stu-id="0cf2d-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0cf2d-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0cf2d-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="0cf2d-107">を使用する特定の型のパラメーターを宣言します。例えば。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  <span data-ttu-id="0cf2d-108">使用して、<xref:System.Runtime.InteropServices.MarshalAsAttribute>を指定する属性`As Any`とき`Void*`が呼び出されるプロシージャで想定されています。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0cf2d-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cf2d-109">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="0cf2d-110">チュートリアル : Windows API の呼び出し</span><span class="sxs-lookup"><span data-stu-id="0cf2d-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="0cf2d-111">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="0cf2d-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="0cf2d-112">マネージ コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="0cf2d-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
