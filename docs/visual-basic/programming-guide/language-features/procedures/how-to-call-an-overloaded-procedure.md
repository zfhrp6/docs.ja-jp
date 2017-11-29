---
title: "方法: オーバーロードされたプロシージャを呼び出す (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff5967c1b09ad59f249297b1cf0a4ed900faf4a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="04327-102">方法: オーバーロードされたプロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04327-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="04327-103">プロシージャのオーバー ロードの利点は、呼び出しの柔軟性にです。</span><span class="sxs-lookup"><span data-stu-id="04327-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="04327-104">呼び出し元のコードは、プロシージャに渡すし、どのような引数が渡されるに関係なく、1 つのプロシージャの名前を呼び出す必要がある情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="04327-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="04327-105">1 つ以上のバージョンの定義を持つプロシージャを呼び出しています</span><span class="sxs-lookup"><span data-stu-id="04327-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="04327-106">呼び出し元のコードでは、プロシージャに渡すデータを決定します。</span><span class="sxs-lookup"><span data-stu-id="04327-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="04327-107">引数リスト内のデータの表示、通常の方法で、プロシージャの呼び出しを記述します。</span><span class="sxs-lookup"><span data-stu-id="04327-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="04327-108">必ず、引数、プロシージャに対して定義されているバージョンのいずれかのパラメーター リストに一致します。</span><span class="sxs-lookup"><span data-stu-id="04327-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="04327-109">呼び出すプロシージャのバージョンを決定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="04327-109">You do not have to determine which version of the procedure to call.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="04327-110">引数リストに一致するバージョンに制御を渡す。</span><span class="sxs-lookup"><span data-stu-id="04327-110"> passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="04327-111">次の例では、`post`でプロシージャが宣言されて[する方法: 複数のバージョンのプロシージャ定義](./how-to-define-multiple-versions-of-a-procedure.md)です。</span><span class="sxs-lookup"><span data-stu-id="04327-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="04327-112">顧客 id を取得、かどうかが判断したこと、`String`または`Integer`、し、いずれの場合、同じプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="04327-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="04327-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="04327-113">See Also</span></span>  
 [<span data-ttu-id="04327-114">手順</span><span class="sxs-lookup"><span data-stu-id="04327-114">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="04327-115">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="04327-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="04327-116">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="04327-116">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="04327-117">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="04327-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="04327-118">方法 : プロシージャの複数のバージョンを定義する</span><span class="sxs-lookup"><span data-stu-id="04327-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="04327-119">方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="04327-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="04327-120">方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="04327-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="04327-121">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="04327-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="04327-122">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="04327-122">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="04327-123">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="04327-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
