---
title: "My.Resources と My.Settings による Rapid Application Development (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1657febf935560ff4c8dd2f54b10fdcb2254891f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>My.Resources と My.Settings による Rapid Application Development (Visual Basic)
`My.Resources`オブジェクトは、アプリケーションのリソースへのアクセスを提供し、アプリケーションのリソースを動的に取得することができます。  
  
## <a name="retrieving-resources"></a>リソースの取得  
 使用して取得できるオーディオ ファイル、アイコン、イメージ、および文字列などのリソースの数、`My.Resources`オブジェクト。 たとえば、アプリケーションのカルチャに固有のリソース ファイルを表示できます。 次の例は、という名前のアイコンをフォームのアイコンを設定`Form1Icon`アプリケーションのリソース ファイルに格納します。  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 `My.Resources`オブジェクトはグローバル リソースのみを公開します。 フォームに関連付けられているリソース ファイルへのアクセスは提供されません。 フォームからフォーム リソースにアクセスする必要があります。 詳しくは、「[チュートリアル: Windows フォームのローカリゼーション](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)」をご覧ください。  
  
 同様に、`My.Settings`オブジェクトがアプリケーションの設定にアクセスできるようにし、動的に格納およびプロパティの設定と、アプリケーションの他の情報を取得することができます。 詳細については、次を参照してください。 [My.Resources オブジェクト](../../../visual-basic/language-reference/objects/my-resources-object.md)と[My.Settings オブジェクト](../../../visual-basic/language-reference/objects/my-settings-object.md)です。  
  
## <a name="see-also"></a>関連項目  
 [My.Resources オブジェクト](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [My.Settings オブジェクト](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [アプリケーション設定へのアクセス](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
