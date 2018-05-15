---
title: End ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 864ac5ef1713f8ffa93c18accede8ecd5b3b7a8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="end-statement"></a><span data-ttu-id="bb793-102">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="bb793-102">End Statement</span></span>
<span data-ttu-id="bb793-103">すぐに実行を終了します。</span><span class="sxs-lookup"><span data-stu-id="bb793-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb793-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb793-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="bb793-105">コメント</span><span class="sxs-lookup"><span data-stu-id="bb793-105">Remarks</span></span>  
 <span data-ttu-id="bb793-106">配置することができます、`End`ステートメント、プロシージャを強制的に実行を停止するアプリケーション全体で任意の場所。</span><span class="sxs-lookup"><span data-stu-id="bb793-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="bb793-107">`End` 使用して開いたファイルをすべて閉じます、`Open`ステートメントと、アプリケーションのすべての変数を消去します。</span><span class="sxs-lookup"><span data-stu-id="bb793-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="bb793-108">コードが実行されている、そのオブジェクトへの参照を保持している他のプログラムがないとすぐにアプリケーションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="bb793-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb793-109">`End`ステートメントが突然、コードの実行を停止しは呼び出されません、`Dispose`または`Finalize`メソッド、またはその他の Visual Basic コードです。</span><span class="sxs-lookup"><span data-stu-id="bb793-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="bb793-110">その他のプログラムによって保持されているオブジェクトの参照が無効になります。</span><span class="sxs-lookup"><span data-stu-id="bb793-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="bb793-111">場合、`End`内でステートメントが検出された、`Try`または`Catch`ブロック、コントロールに対応する渡しません`Finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="bb793-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="bb793-112">`Stop`ステートメントのとは異なりの実行が中断`End`、任意のファイルを閉じておよびコンパイル済み実行可能 (.exe) ファイルで検出された場合を除き、任意の変数をクリアされません。</span><span class="sxs-lookup"><span data-stu-id="bb793-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="bb793-113">`End`を推進せずアプリケーションを終了させるを閉じるためクリーンに使用する前に開いている可能性があるすべてのリソースを試してください。</span><span class="sxs-lookup"><span data-stu-id="bb793-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="bb793-114">たとえば、アプリケーションのすべてのフォームを開く場合を閉じる必要がありますにコントロールに到達する前に、`End`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="bb793-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="bb793-115">使用する必要があります`End`限り注意して、必要なときにすぐに停止します。</span><span class="sxs-lookup"><span data-stu-id="bb793-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="bb793-116">プロシージャを終了する通常の方法 ([Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)と[Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)) だけでなく、プロシージャを正常に終了しますが、も呼び出し元のコードに正常に閉じるための機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="bb793-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="bb793-117">コンソール アプリケーションはたとえば、単にできます`Return`から、`Main`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="bb793-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bb793-118">`End`ステートメントの呼び出し、<xref:System.Environment.Exit%2A>のメソッド、<xref:System.Environment>クラス内で、<xref:System>名前空間。</span><span class="sxs-lookup"><span data-stu-id="bb793-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="bb793-119"><xref:System.Environment.Exit%2A> 必要に`UnmanagedCode`権限です。</span><span class="sxs-lookup"><span data-stu-id="bb793-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="bb793-120">そうしない場合、<xref:System.Security.SecurityException>エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="bb793-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="bb793-121">追加のキーワードが続くと[終了\<キーワード > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)適切なプロシージャまたはブロックの定義の最後のようになります。</span><span class="sxs-lookup"><span data-stu-id="bb793-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="bb793-122">たとえば、`End Function`の定義を終了、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="bb793-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb793-123">例</span><span class="sxs-lookup"><span data-stu-id="bb793-123">Example</span></span>  
 <span data-ttu-id="bb793-124">次の例では、`End`をユーザーが要求した場合、コードの実行を終了するステートメント。</span><span class="sxs-lookup"><span data-stu-id="bb793-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="bb793-125">スマート デバイスの開発者向け注意事項</span><span class="sxs-lookup"><span data-stu-id="bb793-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="bb793-126">このステートメントはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bb793-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb793-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb793-127">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [<span data-ttu-id="bb793-128">Stop ステートメント</span><span class="sxs-lookup"><span data-stu-id="bb793-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="bb793-129">終了\<キーワード > ステートメント</span><span class="sxs-lookup"><span data-stu-id="bb793-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
