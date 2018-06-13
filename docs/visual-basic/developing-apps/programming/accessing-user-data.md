---
title: ユーザー データへのアクセス (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 097006caf56072d5a6e9f2945f5969eed249849e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582845"
---
# <a name="accessing-user-data-visual-basic"></a>ユーザー データへのアクセス (Visual Basic)
このセクションには、`My.User` オブジェクトとそれで実行できるタスクに関するトピックが含まれています。  
  
 `My.User` オブジェクトを利用すれば、<xref:System.Security.Principal.IPrincipal> インターフェイスを実装するオブジェクトを返すことで、ログオン ユーザーに関する情報にアクセスできます。  
  
## <a name="tasks"></a>[タスク]  
  
|終了|解決方法については、|  
|--------|---------|  
|ユーザーのログイン名を取得する|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|アプリケーションで Windows 認証が使用される場合、ユーザーのドメイン名を取得する|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|ユーザーの役割を判断する|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>
