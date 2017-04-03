---
title: "方法: Visual Basic でアプリケーション設定を読み取る | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- reading application settings
- My.Settings object, reading application settings
- application settings, reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e5ad120e52896476447d892438ed9a5d2979da8c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-application-settings-in-visual-basic"></a>方法 : Visual Basic でアプリケーション設定を読み取る
`My.Settings` オブジェクトで設定のプロパティにアクセスすると、ユーザー設定を読み取ることができます。  
  
 `My.Settings` オブジェクトでは、各設定はプロパティとして公開されます。 プロパティ名はその設定の名前と同じで、プロパティの型は設定の型と同じです。 プロパティが読み取り専用かどうかは、設定の**スコープ**でわかります。つまり、**アプリケーション** スコープの設定のプロパティは読み取り専用であるのに対し、**ユーザー** スコープの設定のプロパティは読み取り/書き込みです。 詳細については、「[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、`Nickname` の設定値を表示します。  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 この例を実行するには、アプリケーションで `String` 型の `Nickname` を設定する必要があります。 詳細については、[アプリケーションの設定の管理 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet) を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [方法: Visual Basic でユーザー設定を変更する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [方法: Visual Basic でユーザー設定を永続化する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [アプリケーションの設定の管理 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)
