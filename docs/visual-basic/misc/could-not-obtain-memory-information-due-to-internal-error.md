---
title: "内部エラーのため、メモリ情報を取得できませんでした"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDiagnosticInfo_Memory
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bf339e34368df8fb03024cec255e39e6992be77f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="could-not-obtain-memory-information-due-to-internal-error"></a><span data-ttu-id="3a765-102">内部エラーのため、メモリ情報を取得できませんでした</span><span class="sxs-lookup"><span data-stu-id="3a765-102">Could not obtain memory information due to internal error</span></span>
<span data-ttu-id="3a765-103">`My.Computer.Info` オブジェクトのメモリ情報のプロパティの 1 つに対する呼び出しが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="3a765-103">A call to one of the memory-information properties of the `My.Computer.Info` object failed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3a765-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3a765-104">To correct this error</span></span>  
  
-   <span data-ttu-id="3a765-105">`Try...Catch` オブジェクトのメモリ情報プロパティへの呼び出しの周囲に `My.Computer.Info` を追加します。</span><span class="sxs-lookup"><span data-stu-id="3a765-105">Add a `Try...Catch` block around the call to the memory-information property of the `My.Computer.Info` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a765-106">参照</span><span class="sxs-lookup"><span data-stu-id="3a765-106">See Also</span></span>  
 [<span data-ttu-id="3a765-107">My.Computer.Info</span><span class="sxs-lookup"><span data-stu-id="3a765-107">My.Computer.Info</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo)  
 [<span data-ttu-id="3a765-108">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="3a765-108">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
