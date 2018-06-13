---
title: Error ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 3ecfe18392de15dc937d90565b49641415dd7e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603887"
---
# <a name="error-statement"></a><span data-ttu-id="025b2-102">Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="025b2-102">Error Statement</span></span>
<span data-ttu-id="025b2-103">エラーの発生をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="025b2-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="025b2-104">構文</span><span class="sxs-lookup"><span data-stu-id="025b2-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="025b2-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="025b2-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="025b2-106">必須。</span><span class="sxs-lookup"><span data-stu-id="025b2-106">Required.</span></span> <span data-ttu-id="025b2-107">任意の有効なエラー番号を指定できます。</span><span class="sxs-lookup"><span data-stu-id="025b2-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="025b2-108">コメント</span><span class="sxs-lookup"><span data-stu-id="025b2-108">Remarks</span></span>  
 <span data-ttu-id="025b2-109">`Error`ステートメントは、旧バージョンとの互換性のためサポートされます。</span><span class="sxs-lookup"><span data-stu-id="025b2-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="025b2-110">オブジェクトを作成するときに特に新しいコードを使用して、`Err`オブジェクトの`Raise`実行時エラーを生成する方法です。</span><span class="sxs-lookup"><span data-stu-id="025b2-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="025b2-111">場合`errornumber`が定義されている、`Error`ステートメントでは、エラー ハンドラーを呼び出し、プロパティの後に、`Err`オブジェクトには、次の既定値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="025b2-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="025b2-112">プロパティ</span><span class="sxs-lookup"><span data-stu-id="025b2-112">Property</span></span>|<span data-ttu-id="025b2-113">[値]</span><span class="sxs-lookup"><span data-stu-id="025b2-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="025b2-114">引数として指定された値`Error`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="025b2-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="025b2-115">任意の有効なエラー番号を指定できます。</span><span class="sxs-lookup"><span data-stu-id="025b2-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="025b2-116">現在の Visual Basic プロジェクトの名前です。</span><span class="sxs-lookup"><span data-stu-id="025b2-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="025b2-117">文字列式の戻り値に対応する、 `Error` 、指定された関数`Number`、この文字列が存在する場合。</span><span class="sxs-lookup"><span data-stu-id="025b2-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="025b2-118">文字列が存在しない場合`Description`長さ 0 の文字列が含まれています ("") です。</span><span class="sxs-lookup"><span data-stu-id="025b2-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="025b2-119">完全修飾のドライブ、パス、および適切な Visual Basic のヘルプ ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="025b2-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="025b2-120">コンテキスト ID に対応するエラーを適切な Visual Basic のヘルプ ファイル、`Number`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="025b2-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="025b2-121">0 を返します。</span><span class="sxs-lookup"><span data-stu-id="025b2-121">Zero.</span></span>|  
  
 <span data-ttu-id="025b2-122">エラー ハンドラーが存在しないか、エラー メッセージが作成されから表示される場合は、有効でない場合、`Err`オブジェクト プロパティです。</span><span class="sxs-lookup"><span data-stu-id="025b2-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="025b2-123">Visual Basic ホスト アプリケーションの一部では、オブジェクトを作成できません。</span><span class="sxs-lookup"><span data-stu-id="025b2-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="025b2-124">クラスとオブジェクトのどちらを作成できるかどうかを決定は、ホスト アプリケーションのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="025b2-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="025b2-125">例</span><span class="sxs-lookup"><span data-stu-id="025b2-125">Example</span></span>  
 <span data-ttu-id="025b2-126">この例では、 `Error` 11 のエラー番号を生成するステートメント。</span><span class="sxs-lookup"><span data-stu-id="025b2-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="025b2-127">要件</span><span class="sxs-lookup"><span data-stu-id="025b2-127">Requirements</span></span>  
 <span data-ttu-id="025b2-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="025b2-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="025b2-129">**アセンブリ:** Visual Basic Runtime Library (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="025b2-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="025b2-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="025b2-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [<span data-ttu-id="025b2-131">On Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="025b2-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [<span data-ttu-id="025b2-132">Resume ステートメント</span><span class="sxs-lookup"><span data-stu-id="025b2-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="025b2-133">エラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="025b2-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
