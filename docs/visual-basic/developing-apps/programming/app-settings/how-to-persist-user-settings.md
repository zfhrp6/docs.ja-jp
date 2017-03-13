---
title: "How to: Persist User Settings in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Settings object, persisting user settings"
  - "persistence, persisting user settings [Visual Basic]"
  - "user settings, persisting"
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Persist User Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Settings.Save` メソッドを使用して、ユーザー設定の変更内容を永続化できます。  
  
 通常、アプリケーションでは、ユーザー設定の変更内容を、アプリケーションの終了時に永続化するようにデザインされています。  さまざまな要因によっては、設定の保存に数秒かかる場合もあるからです。  
  
 詳細については、「[My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。  
  
> [!NOTE]
>  ユーザー スコープ設定の値は実行時に変更および保存できますが、アプリケーション スコープ設定は読み取り専用であり、プログラムから変更できません。  アプリケーション スコープの設定は、アプリケーションを作成するときに**プロジェクト デザイナー**を使用するか、またはアプリケーションの構成ファイルを編集して変更できます。  詳細については、「[アプリケーションの設定の管理 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)」を参照してください。  
  
## 使用例  
 この例では、`LastChanged` ユーザー設定の値を変更し、`My.Settings.Save` メソッドを呼び出して、その変更内容を保存します。  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 この例が動作するためには、アプリケーションに `Date` 型の `LastChanged` ユーザー設定が必要です。  詳細については、「[アプリケーションの設定の管理 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)」を参照してください。  
  
## 参照  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [How to: Change User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [How to: Create Property Grids for User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [アプリケーションの設定の管理 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)