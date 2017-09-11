---
title: "方法: 値 (Visual Basic) を返さないプロシージャを呼び出す |Microsoft ドキュメント"
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
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
ms.openlocfilehash: 26120b763d2ecedb3aa43adb08e4c87c2b1e0be1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="dd245-102">方法: 値を返さないプロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd245-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="dd245-103">A`Sub`プロシージャが呼び出し元のコードに値を返しません。</span><span class="sxs-lookup"><span data-stu-id="dd245-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="dd245-104">これを明示的に呼び出すスタンドアロンの呼び出し元ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="dd245-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="dd245-105">単に式の中で名前を使用して呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="dd245-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="dd245-106">Sub プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="dd245-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="dd245-107">名前を指定、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="dd245-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="dd245-108">次のプロシージャ名の引数リストを囲むかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="dd245-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="dd245-109">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="dd245-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="dd245-110">ただし、かっこを使用して、コードを読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="dd245-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="dd245-111">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="dd245-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="dd245-112">同じ順序で引数を指定する必要があります`Sub`プロシージャは、対応するパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="dd245-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="dd245-113">次の例では、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>アプリケーション ウィンドウにアクティブにします</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>。</span><span class="sxs-lookup"><span data-stu-id="dd245-113">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="dd245-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>単一の引数として、ウィンドウのタイトルを取得します。</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A></span><span class="sxs-lookup"><span data-stu-id="dd245-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="dd245-115">呼び出し元のコードに値を返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="dd245-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="dd245-116">例では、スロー <xref:System.ArgumentException>。</xref:System.ArgumentException>でメモ帳のプロセスが実行されていない場合</span><span class="sxs-lookup"><span data-stu-id="dd245-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="dd245-117">`Shell`プロシージャでは、アプリケーションは、指定されたパスに前提としています。</span><span class="sxs-lookup"><span data-stu-id="dd245-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     <span data-ttu-id="dd245-118">[!code-vb[VbVbalrCatRef&#11;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="dd245-118">[!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd245-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd245-119">See Also</span></span>  
 <span data-ttu-id="dd245-120"><xref:Microsoft.VisualBasic.Interaction.Shell%2A></xref:Microsoft.VisualBasic.Interaction.Shell%2A></span><span class="sxs-lookup"><span data-stu-id="dd245-120"><xref:Microsoft.VisualBasic.Interaction.Shell%2A></span></span>   
 <span data-ttu-id="dd245-121"><xref:System.ArgumentException></xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="dd245-121"><xref:System.ArgumentException></span></span>   
<span data-ttu-id="dd245-122"> [手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="dd245-122"> [Procedures](./index.md) </span></span>  
<span data-ttu-id="dd245-123"> [Sub プロシージャ](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="dd245-123"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="dd245-124"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="dd245-124"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="dd245-125"> [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="dd245-125"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="dd245-126"> [方法: プロシージャを作成します。](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="dd245-126"> [How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
<span data-ttu-id="dd245-127"> [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="dd245-127"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="dd245-128"> [方法: Visual Basic でイベント ハンドラーを呼び出す](./how-to-call-an-event-handler.md)</span><span class="sxs-lookup"><span data-stu-id="dd245-128"> [How to: Call an Event Handler in Visual Basic](./how-to-call-an-event-handler.md)</span></span>
