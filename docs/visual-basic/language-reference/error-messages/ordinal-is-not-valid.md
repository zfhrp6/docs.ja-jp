---
title: 序数が有効ではありません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="e468d-102">序数が有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="e468d-102">Ordinal is not valid</span></span>
<span data-ttu-id="e468d-103">プロシージャ名の代わりに、番号を使用してに示されているダイナミック リンク ライブラリ (DLL) への呼び出しを使用して、`#num`構文です。</span><span class="sxs-lookup"><span data-stu-id="e468d-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="e468d-104">このエラーには、次の考えられる原因があります。</span><span class="sxs-lookup"><span data-stu-id="e468d-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="e468d-105">変換する、`#num`失敗序数する式。</span><span class="sxs-lookup"><span data-stu-id="e468d-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="e468d-106">`#num`指定された DLL で任意の関数が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="e468d-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="e468d-107">タイプ ライブラリには、無効な序数の内部で使用されて結果として無効な宣言があります。</span><span class="sxs-lookup"><span data-stu-id="e468d-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e468d-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e468d-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="e468d-109">名前でプロシージャを呼び出すまたは式が有効な数値を表すかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e468d-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="e468d-110">確認`#num`DLL 内の有効な関数を識別します。</span><span class="sxs-lookup"><span data-stu-id="e468d-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="e468d-111">問題の原因で、コードをコメント アウト、プロシージャ呼び出しを分離します。</span><span class="sxs-lookup"><span data-stu-id="e468d-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="e468d-112">書き込み、`Declare`プロシージャ、およびレポート、タイプ ライブラリのベンダーに、問題ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="e468d-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e468d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e468d-113">See Also</span></span>  
 [<span data-ttu-id="e468d-114">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="e468d-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
