---
title: "クラスがオートメーションをサポートしていないかは、必要なインターフェイスをサポートしていません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID430
dev_langs:
- VB
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
caps.latest.revision: 11
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
ms.openlocfilehash: 8368ac123ce24dae41363e74c8b76773f64473b1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="263a3-102">クラスがオートメーションをサポートしていないか、必要なインターフェイスをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="263a3-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="263a3-103">`GetObject` 関数呼び出しまたは `CreateObject` 関数呼び出しで指定したクラスが外部からプログラム可能なインターフェイスを公開していません。あるいは、.dll から .exe へ、または .exe から .dll へプロジェクトを変更しました。</span><span class="sxs-lookup"><span data-stu-id="263a3-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="263a3-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="263a3-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="263a3-105">オブジェクトを作成したアプリケーションのドキュメントを参照して、このクラスのオブジェクトでオートメーションを使用する上での制限を確認します。</span><span class="sxs-lookup"><span data-stu-id="263a3-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2.  <span data-ttu-id="263a3-106">.dll から .exe へ、または .exe から .dll へプロジェクトを変更した場合は、古い .dll または .exe を手動で登録解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="263a3-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="263a3-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="263a3-107">See Also</span></span>  
 <span data-ttu-id="263a3-108">[エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md) </span><span class="sxs-lookup"><span data-stu-id="263a3-108">[Error Types](../../../visual-basic/programming-guide/language-features/error-types.md) </span></span>  
<span data-ttu-id="263a3-109"> [ご意見](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="263a3-109"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
