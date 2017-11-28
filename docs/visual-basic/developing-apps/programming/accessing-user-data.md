---
title: "ユーザー データへのアクセス (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- domain names [Visual Basic], retrieving
- data [Visual Basic], accessing user data
- My.User object [Visual Basic], tasks
- user data [Visual Basic], domain
- user names [Visual Basic], retrieving
- user data [Visual Basic], accessing
- login names [Visual Basic]
- examples [Visual Basic], accessing user data
ms.assetid: 32492a15-ee59-4a63-a1f1-9b24cc13140a
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 92c0b97059896e86d54069b637c9956cac9d10e8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="accessing-user-data-visual-basic"></a><span data-ttu-id="4b346-102">ユーザー データへのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b346-102">Accessing User Data (Visual Basic)</span></span>
<span data-ttu-id="4b346-103">このセクションには、`My.User` オブジェクトとそれで実行できるタスクに関するトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b346-103">This section contains topics dealing with the `My.User` object and tasks that you can accomplish with it.</span></span>  
  
 <span data-ttu-id="4b346-104">`My.User` オブジェクトを利用すれば、<xref:System.Security.Principal.IPrincipal> インターフェイスを実装するオブジェクトを返すことで、ログオン ユーザーに関する情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4b346-104">The `My.User` object provides access to information about the logged-on user by returning an object that implements the <xref:System.Security.Principal.IPrincipal> interface.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="4b346-105">タスク</span><span class="sxs-lookup"><span data-stu-id="4b346-105">Tasks</span></span>  
  
|<span data-ttu-id="4b346-106">目的</span><span class="sxs-lookup"><span data-stu-id="4b346-106">To</span></span>|<span data-ttu-id="4b346-107">参照トピック</span><span class="sxs-lookup"><span data-stu-id="4b346-107">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="4b346-108">ユーザーのログイン名を取得する</span><span class="sxs-lookup"><span data-stu-id="4b346-108">Get the user's login name</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|<span data-ttu-id="4b346-109">アプリケーションで Windows 認証が使用される場合、ユーザーのドメイン名を取得する</span><span class="sxs-lookup"><span data-stu-id="4b346-109">Get the user's domain name, if the application uses Windows authentication</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|<span data-ttu-id="4b346-110">ユーザーの役割を判断する</span><span class="sxs-lookup"><span data-stu-id="4b346-110">Determine the user's role</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="4b346-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b346-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>
