---
title: "My.Forms および My.WebServices が提供する既定のオブジェクト インスタンス (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44265c3f6f38a001192a8d92f2fbb6edeaca21cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="08fab-102">My.Forms および My.WebServices が提供する既定のオブジェクト インスタンス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08fab-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>
<span data-ttu-id="08fab-103">[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)と[My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)オブジェクトは、フォーム、データ ソース、およびアプリケーションによって使用される XML Web サービスへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="08fab-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="08fab-104">このように設定のコレクションを提供することによって*既定インスタンス*のこれらの各オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="08fab-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="08fab-105">既定のインスタンス</span><span class="sxs-lookup"><span data-stu-id="08fab-105">Default Instances</span></span>  
 <span data-ttu-id="08fab-106">既定のインスタンスは、ランタイムによって提供されする必要がないクラスのインスタンスは、宣言およびインスタンスを使用して、`Dim`と`New`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="08fab-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="08fab-107">次の例は、どのようにする場合がありますが宣言およびインスタンスのインスタンス、<xref:System.Windows.Forms.Form>と呼ばれるクラス`Form1`、され、どのようにこれの既定のインスタンスを取得することが今すぐ<xref:System.Windows.Forms.Form>クラスを通じて`My.Forms`です。</span><span class="sxs-lookup"><span data-stu-id="08fab-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 <span data-ttu-id="08fab-108">`My.Forms`オブジェクトに対する既定のインスタンスのコレクションを返しますすべて`Form`プロジェクトに存在するクラス。</span><span class="sxs-lookup"><span data-stu-id="08fab-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="08fab-109">同様に、`My.WebServices`アプリケーションでへの参照を作成したすべての Web サービスのプロキシ クラスの既定のインスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="08fab-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08fab-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="08fab-110">See Also</span></span>  
 [<span data-ttu-id="08fab-111">My.Forms オブジェクト</span><span class="sxs-lookup"><span data-stu-id="08fab-111">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [<span data-ttu-id="08fab-112">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="08fab-112">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [<span data-ttu-id="08fab-113">プロジェクトの種類に応じた My の機能</span><span class="sxs-lookup"><span data-stu-id="08fab-113">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
