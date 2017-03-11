---
title: "How to: Change User Settings in Visual Basic | Microsoft Docs"
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
  - "user settings, changing in Visual Basic"
  - "user settings"
  - "My.Settings object, changing user settings"
  - "examples [Visual Basic], changing user settings"
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Change User Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Settings` オブジェクトで設定のプロパティに新しい値を割り当てると、ユーザー設定を変更できます。  
  
 `My.Settings` オブジェクトでは、各設定がプロパティとして公開されています。  プロパティの名前は設定の名前と同じで、プロパティの型は設定の型と同じです。  プロパティが読み取り専用かどうかは、設定の**スコープ**で決定されます。つまり、**アプリケーション** スコープの設定のプロパティは読み取り専用であるのに対し、**ユーザー** スコープの設定のプロパティは読み書き可能です。  詳細については、「[My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。  
  
> [!NOTE]
>  ユーザー スコープ設定の値は実行時に変更および保存できますが、アプリケーション スコープ設定は読み取り専用であり、プログラムから変更できません。  アプリケーション スコープの設定は、アプリケーションを作成するときに**プロジェクト デザイナー**を使用するか、またはアプリケーションの構成ファイルを編集して変更できます。  詳細については、「[アプリケーションの設定の管理 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)」を参照してください。  
  
## 使用例  
 この例では、`Nickname` ユーザー設定の値を変更します。  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/visualbasic/VbVbalrMyResources2/Form1.vb#7)]  
  
 この例が動作するためには、アプリケーションに `String` 型の `Nickname` ユーザー設定が必要です。  
  
 アプリケーションがユーザー設定を保存するのは、アプリケーションが終了するときです。  設定をすぐに保存するには、`My.Settings.Save` メソッドを呼び出します。  詳細については、「[How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)」を参照してください。  
  
## 参照  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [How to: Create Property Grids for User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [アプリケーションの設定の管理 \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)