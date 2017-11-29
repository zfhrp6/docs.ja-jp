---
title: "方法: 値を返さないプロシージャを呼び出す (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bbea50132d1110b38bf9b01397795a2cd51f86d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="906ee-102">方法: 値を返さないプロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="906ee-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="906ee-103">A`Sub`プロシージャが呼び出し元のコードに値を返しません。</span><span class="sxs-lookup"><span data-stu-id="906ee-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="906ee-104">これを明示的に呼び出すスタンドアロンの呼び出し元ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="906ee-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="906ee-105">単に式の中で名前を使用して呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="906ee-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="906ee-106">Sub プロシージャを呼び出しています</span><span class="sxs-lookup"><span data-stu-id="906ee-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="906ee-107">名前を指定、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="906ee-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="906ee-108">プロシージャ名を引数リストを囲むかっこに従ってください。</span><span class="sxs-lookup"><span data-stu-id="906ee-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="906ee-109">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="906ee-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="906ee-110">ただし、かっこを使用して、コードを読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="906ee-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="906ee-111">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="906ee-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="906ee-112">同じ順序で引数を指定する必要がありますする、`Sub`プロシージャが、対応するパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="906ee-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="906ee-113">次の例では、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>アプリケーション ウィンドウにアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="906ee-113">The following example calls the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="906ee-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>その唯一の引数として、ウィンドウのタイトルを使用します。</span><span class="sxs-lookup"><span data-stu-id="906ee-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="906ee-115">値を返さない呼び出しコードにします。</span><span class="sxs-lookup"><span data-stu-id="906ee-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="906ee-116">メモ帳のプロセスが実行されていない場合がスローされます、<xref:System.ArgumentException>です。</span><span class="sxs-lookup"><span data-stu-id="906ee-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="906ee-117">`Shell`プロシージャでは、アプリケーションは、指定されたパスに前提としています。</span><span class="sxs-lookup"><span data-stu-id="906ee-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="906ee-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="906ee-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [<span data-ttu-id="906ee-119">手順</span><span class="sxs-lookup"><span data-stu-id="906ee-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="906ee-120">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="906ee-120">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="906ee-121">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="906ee-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="906ee-122">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="906ee-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="906ee-123">方法 : プロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="906ee-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="906ee-124">方法: 値を返すプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="906ee-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="906ee-125">方法: Visual Basic では、イベント ハンドラーを呼び出します</span><span class="sxs-lookup"><span data-stu-id="906ee-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
