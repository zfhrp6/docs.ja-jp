---
title: "方法: オーバー ロードされたプロシージャ (Visual Basic) を呼び出す |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- procedures, overloading
- procedures, calling
- procedures, multiple versions
- procedure calls, overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
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
ms.openlocfilehash: 777df0cc81a4e0518773a0e8cc98d590d1c0cf0d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="12531-102">方法: オーバーロードされたプロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12531-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="12531-103">プロシージャのオーバー ロードの利点は、呼び出しの柔軟性です。</span><span class="sxs-lookup"><span data-stu-id="12531-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="12531-104">呼び出し元のコードでは、プロシージャに渡すし、どの引数が渡される、単一のプロシージャ名を呼び出して必要な情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="12531-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="12531-105">定義された&1; つ以上のバージョンを持つプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="12531-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="12531-106">呼び出し元のコードでは、プロシージャに渡すデータを決定します。</span><span class="sxs-lookup"><span data-stu-id="12531-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="12531-107">通常の方法では、引数リストで、データを提供することで、プロシージャの呼び出しを記述します。</span><span class="sxs-lookup"><span data-stu-id="12531-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="12531-108">引数には、プロシージャに対して定義されたバージョンのいずれかのパラメーター リストが一致することをします。</span><span class="sxs-lookup"><span data-stu-id="12531-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="12531-109">呼び出すプロシージャのバージョンを決定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="12531-109">You do not have to determine which version of the procedure to call.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="12531-110">引数リストに一致するバージョンに制御を渡す。</span><span class="sxs-lookup"><span data-stu-id="12531-110"> passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="12531-111">次の例では、`post`プロシージャ内で宣言[する方法: 複数のバージョンのプロシージャ定義](./how-to-define-multiple-versions-of-a-procedure.md)します。</span><span class="sxs-lookup"><span data-stu-id="12531-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="12531-112">顧客 id を取得して、ことがあるかどうかを判定する`String`または`Integer`、し、いずれの場合と同じ手順を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="12531-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     <span data-ttu-id="12531-113">[!code-vb[VbVbcnProcedures #&56;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="12531-113">[!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="12531-114">[!code-vb[VbVbcnProcedures #&57;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="12531-114">[!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12531-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="12531-115">See Also</span></span>  
 <span data-ttu-id="12531-116">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="12531-116">[Procedures](./index.md) </span></span>  
<span data-ttu-id="12531-117"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="12531-117"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="12531-118"> [プロシージャのオーバー ロード](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="12531-118"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="12531-119"> [トラブルシューティングの手順](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="12531-119"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="12531-120"> [方法: プロシージャの複数のバージョンを定義します。](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="12531-120"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="12531-121"> [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="12531-121"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="12531-122"> [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="12531-122"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="12531-123"> [プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="12531-123"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="12531-124"> [オーバー ロードの解決](./overload-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="12531-124"> [Overload Resolution](./overload-resolution.md) </span></span>  
<span data-ttu-id="12531-125"> [オーバーロード](../../../../visual-basic/language-reference/modifiers/overloads.md)</span><span class="sxs-lookup"><span data-stu-id="12531-125"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)</span></span>
