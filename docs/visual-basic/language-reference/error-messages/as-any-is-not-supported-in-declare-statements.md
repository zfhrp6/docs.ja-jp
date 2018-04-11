---
title: '&#39;です。いずれかの &#39; としてサポートされていません (& a) #39; Declare &#39;ステートメント'
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
ms.openlocfilehash: 59120622688ee38d5b8f45c08dfc3ae40711fb8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="de41f-102">&#39;です。いずれかの &#39; としてサポートされていません (& a) #39; Declare &#39;ステートメント</span><span class="sxs-lookup"><span data-stu-id="de41f-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="de41f-103">`Any`データ型と共に使用されました`Declare`任意のデータ型を含む可能性のある引数の使用を許可するには、Visual Basic 6.0 とそれ以前のバージョン内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="de41f-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="de41f-104">ただし、オーバー ロードをサポートしは、`Any`旧式の型します。</span><span class="sxs-lookup"><span data-stu-id="de41f-104"> supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="de41f-105">**エラー ID:** BC30828</span><span class="sxs-lookup"><span data-stu-id="de41f-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="de41f-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="de41f-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="de41f-107">を使用する特定の型のパラメーターを宣言します。例えば。</span><span class="sxs-lookup"><span data-stu-id="de41f-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  <span data-ttu-id="de41f-108">使用して、<xref:System.Runtime.InteropServices.MarshalAsAttribute>を指定する属性`As Any`とき`Void*`が呼び出されるプロシージャで想定されています。</span><span class="sxs-lookup"><span data-stu-id="de41f-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="de41f-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="de41f-109">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="de41f-110">チュートリアル : Windows API の呼び出し</span><span class="sxs-lookup"><span data-stu-id="de41f-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="de41f-111">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="de41f-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="de41f-112">マネージ コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="de41f-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
