---
title: "オートメーション エラーです。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 790b171b8d4022bd6d8b038c4221f24805ae42f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="automation-error"></a><span data-ttu-id="2d790-102">オートメーション エラーです。</span><span class="sxs-lookup"><span data-stu-id="2d790-102">Automation error</span></span>
<span data-ttu-id="2d790-103">メソッドの実行中、またはオブジェクト変数のプロパティの取得中または設定中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2d790-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="2d790-104">エラーは、オブジェクトを作成したアプリケーションによって報告されました。</span><span class="sxs-lookup"><span data-stu-id="2d790-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2d790-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="2d790-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="2d790-106">`Err` オブジェクトのプロパティをチェックし、エラーの原因と性質を確認します。</span><span class="sxs-lookup"><span data-stu-id="2d790-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2.  <span data-ttu-id="2d790-107">アクセス ステートメントの直前で `On Error Resume Next` ステートメントを使用し、アクセス ステートメントの直後のエラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d790-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d790-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d790-108">See Also</span></span>  
 [<span data-ttu-id="2d790-109">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="2d790-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="2d790-110">ご意見</span><span class="sxs-lookup"><span data-stu-id="2d790-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
