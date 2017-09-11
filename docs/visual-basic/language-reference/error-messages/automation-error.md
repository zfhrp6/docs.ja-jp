---
title: "オートメーション エラーです |。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID440
dev_langs:
- VB
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: 9
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
ms.openlocfilehash: b48ada07663889db633a43fabb577d5129c5cbb3
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="automation-error"></a><span data-ttu-id="0a806-102">オートメーション エラーです。</span><span class="sxs-lookup"><span data-stu-id="0a806-102">Automation error</span></span>
<span data-ttu-id="0a806-103">メソッドの実行中、またはオブジェクト変数のプロパティの取得中または設定中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0a806-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="0a806-104">エラーは、オブジェクトを作成したアプリケーションによって報告されました。</span><span class="sxs-lookup"><span data-stu-id="0a806-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a806-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0a806-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="0a806-106">`Err` オブジェクトのプロパティをチェックし、エラーの原因と性質を確認します。</span><span class="sxs-lookup"><span data-stu-id="0a806-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2.  <span data-ttu-id="0a806-107">アクセス ステートメントの直前で `On Error Resume Next` ステートメントを使用し、アクセス ステートメントの直後のエラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="0a806-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a806-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a806-108">See Also</span></span>  
 <span data-ttu-id="0a806-109">[エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md) </span><span class="sxs-lookup"><span data-stu-id="0a806-109">[Error Types](../../../visual-basic/programming-guide/language-features/error-types.md) </span></span>  
<span data-ttu-id="0a806-110"> [ご意見](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="0a806-110"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
