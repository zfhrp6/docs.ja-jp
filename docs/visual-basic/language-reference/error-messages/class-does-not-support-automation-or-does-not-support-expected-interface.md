---
title: クラスがオートメーションをサポートしていないか、必要なインターフェイスをサポートしていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: 860c472794495ef2be37aea7c7d8305c237dfd13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585675"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="497c1-102">クラスがオートメーションをサポートしていないか、必要なインターフェイスをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="497c1-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="497c1-103">`GetObject` 関数呼び出しまたは `CreateObject` 関数呼び出しで指定したクラスが外部からプログラム可能なインターフェイスを公開していません。あるいは、.dll から .exe へ、または .exe から .dll へプロジェクトを変更しました。</span><span class="sxs-lookup"><span data-stu-id="497c1-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="497c1-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="497c1-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="497c1-105">オブジェクトを作成したアプリケーションのドキュメントを参照して、このクラスのオブジェクトでオートメーションを使用する上での制限を確認します。</span><span class="sxs-lookup"><span data-stu-id="497c1-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2.  <span data-ttu-id="497c1-106">.dll から .exe へ、または .exe から .dll へプロジェクトを変更した場合は、古い .dll または .exe を手動で登録解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="497c1-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497c1-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="497c1-107">See Also</span></span>  
 [<span data-ttu-id="497c1-108">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="497c1-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="497c1-109">ご意見</span><span class="sxs-lookup"><span data-stu-id="497c1-109">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
